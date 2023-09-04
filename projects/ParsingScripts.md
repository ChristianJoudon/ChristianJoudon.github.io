# Screenplay Analysis Tool

This script fetches a screenplay from a URL and extracts a character's dialogue. 
It then tokenizes the dialogue and uses RAKE for keyword extraction. 
Employing SpaCy's NER, it filters out named entities from the keywords. 
Finally, the script displays the character's spoken words and the identified keywords.

# Importing required libraries
import re
import requests
from bs4 import BeautifulSoup
from rake_nltk import Rake
import nltk
import ssl
import spacy

# Handling SSL certificate issues
try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    # This exception is raised in environments where the SSL context does not exist
    pass
else:
    ssl._create_default_https_context = _create_unverified_https_context

# Download stopwords for NLTK (used internally by RAKE)
nltk.download('stopwords')

def fetch_screenplay(url):
    """Fetches the screenplay content from a given URL using BeautifulSoup."""
    
    response = requests.get(url)
    response.raise_for_status()  # Check for HTTP errors
    
    # Parse the fetched content
    soup = BeautifulSoup(response.text, 'html.parser')
    
    # Search for a <pre> tag that generally holds screenplay data
    pre_tag = soup.find('pre')

    if pre_tag:
        return pre_tag.get_text()
    else:
        raise ValueError("Screenplay not found in the specified URL")

def extract_dialogue(screenplay, character_name):
    """Extracts all dialogues of a specified character from the screenplay."""
    
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
    """Tokenizes the dialogue lines and counts the frequency of each word."""
    
    tokenized_words = {}
    for line in dialogue_lines:
        # Use regex to extract words from each line
        words = re.findall(r'\b\w+\b', line.lower())
        for word in words:
            tokenized_words[word] = tokenized_words.get(word, 0) + 1

    return tokenized_words

# Loading the SpaCy model for Named Entity Recognition (NER)
nlp = spacy.load("en_core_web_sm")

def extract_keywords(dialogue_lines, num_keywords=40):
    """Uses the RAKE algorithm to extract keywords from the dialogue lines."""
    
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
    """Prints the words in a formatted manner, with a specified number of words per line."""
    
    sorted_words = {k: v for k, v in sorted(words.items())}
    word_list = [f"{k}: {v}" for k, v in sorted_words.items()]
    for i in range(0, len(word_list), words_per_line):
        print(' '.join(word_list[i:i + words_per_line]))

def main():
    """Main function to drive the script."""
    
    screenplay_url = 'https://imsdb.com/scripts/Joker.html'
    character_name = 'JOKER'

    # Fetch screenplay and extract dialogues
    screenplay = fetch_screenplay(screenplay_url)
    dialogue_lines = extract_dialogue(screenplay, character_name)
    character_words = tokenize_dialogue(dialogue_lines)

    # Display all words spoken by the character
    print("All words:")
    print_words(character_words)

    # Extract and display keywords from the dialogues
    keywords = extract_keywords(dialogue_lines, num_keywords=20)
    print("\nKeywords:")
    print_words(keywords)

# Running the script
if __name__ == '__main__':
    main()
    print_words(keywords)

if __name__ == '__main__':
    main()
