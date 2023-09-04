# Screenplay Analysis Tool

```python
# This script retrieves a screenplay from a given URL and extracts a specific character's dialogue.
# The extracted dialogue is then tokenized, and a keyword extraction technique (RAKE - Rapid Automatic Keyword Extraction) is used.
# Additionally, named entity recognition from SpaCy is utilized to filter out named entities from the extracted keywords.
# The script finally displays a list of all words spoken by the character and the extracted keywords.

import re
import requests
from bs4 import BeautifulSoup
from rake_nltk import Rake
import nltk
import ssl
import spacy

try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    pass
else:
    ssl._create_default_https_context = _create_unverified_https_context

nltk.download('stopwords')

def fetch_screenplay(url):
    response = requests.get(url)
    response.raise_for_status()

    soup = BeautifulSoup(response.text, 'html.parser')
    pre_tag = soup.find('pre')

    if pre_tag:
        return pre_tag.get_text()
    else:
        raise ValueError("Screenplay not found in the specified URL")

def extract_dialogue(screenplay, character_name):
    character_dialogue = []
    lines = screenplay.split('\n')
    character_name = character_name.upper()

    is_character_line = False
    for line in lines:
        if line.strip() == character_name:
            is_character_line = True
        elif is_character_line and len(line.strip()) > 0:
            character_dialogue.append(line.strip())
            is_character_line = False

    return character_dialogue

def tokenize_dialogue(dialogue_lines):
    tokenized_words = {}
    for line in dialogue_lines:
        words = re.findall(r'\b\w+\b', line.lower())
        for word in words:
            tokenized_words[word] = tokenized_words.get(word, 0) + 1

    return tokenized_words

nlp = spacy.load("en_core_web_sm")

def extract_keywords(dialogue_lines, num_keywords=40):
    r = Rake()
    r.extract_keywords_from_sentences(dialogue_lines)
    keywords = r.get_ranked_phrases()[:num_keywords]

    keyword_dict = {}
    for keyword in keywords:
        words = keyword.split()
        for word in words:
            # Check if the word is a name using SpaCy NER
            doc = nlp(word)
            if not any(ent.label_ == "PERSON" for ent in doc.ents):
                keyword_dict[word] = keyword_dict.get(word, 0) + 1

    return keyword_dict

def print_words(words, words_per_line=10):
    sorted_words = {k: v for k, v in sorted(words.items())}
    word_list = [f"{k}: {v}" for k, v in sorted_words.items()]
    for i in range(0, len(word_list), words_per_line):
        print(' '.join(word_list[i:i + words_per_line]))

def main():
    screenplay_url = 'https://imsdb.com/scripts/Joker.html'
    character_name = 'JOKER'

    screenplay = fetch_screenplay(screenplay_url)
    dialogue_lines = extract_dialogue(screenplay, character_name)
    character_words = tokenize_dialogue(dialogue_lines)

    print("All words:")
    print_words(character_words)

    keywords = extract_keywords(dialogue_lines, num_keywords=20)

    print("\nKeywords:")
    print_words(keywords)

if __name__ == '__main__':
    main()
