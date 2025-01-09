---
layout: project
type: project
image: img/c6a7db474ee18492e629b4a3f3d5627b.png
title: "Character Dictionary"
date: 2022-01-01  # Adjust the date as necessary
published: false
labels:
  - Natural Language Processing
  - Rake
  - Ntlk
  - Ssl
  - Spacy
  - Beautiful Soup
  - Python
summary: "I designed a software that extracts and compiles a keyword dictionary for individual characters from film or TV scripts."
---
# Screenplay Analysis with Natural Language Processing

In the age of Big Data and Natural Language Processing (NLP), understanding the linguistic nuances and thematic elements of screenplays becomes more nuanced and systematic. This script offers an efficient way to harness the power of computational methods for screenplay analysis. Specifically, it aims to extract, tokenize, and identify keywords from dialogues of a given character from an online screenplay.

## Essential Libraries

The script incorporates several essential libraries, each serving a particular function:

- `re`: Facilitates string operations and word tokenization through regular expressions.
- `requests`: Essential for fetching the screenplay from the web.
- `BeautifulSoup`: Parses HTML and extracts relevant data.
- `rake_nltk` and `nltk`: Libraries for keyword extraction and linguistic operations respectively.
- `ssl`: Manages SSL certificate verifications for secure web requests.
- `spacy`: Employed for named entity recognition (NER).

## Addressing SSL Certificate Issues

To bypass potential SSL certificate verification issues during web requests, the script uses a workaround to override the default SSL context creation with an unverified context.

## Screenplay Acquisition

The `fetch_screenplay` function retrieves content from a URL. Using `requests`, it fetches the HTML, parsed by `BeautifulSoup`, to extract the content inside the `<pre>` tags.

## Dialogue Extraction

`extract_dialogue` filters out lines spoken by a specified character. It tokenizes the screenplay by lines and checks each one for the character's name. If found, the following line (containing the dialogue) is appended to a list.

## Dialogue Tokenization

`tokenize_dialogue` tokenizes extracted dialogue lines into words and calculates word frequencies.

## Keyword Extraction and Named Entity Filtering

`extract_keywords` uses the RAKE algorithm (via `rake_nltk`) to deduce keywords. SpaCy's NER system then filters out proper names to ensure relevance.

## Presentation Function

`print_words` presents words (or keywords) in a structured manner, grouping them for enhanced readability.

## Main Execution

The main function targets the dialogue of the "JOKER" character from the "Joker" screenplay. It fetches the screenplay, extracts and tokenizes dialogues, prints all spoken words, and highlights the significant keywords.

# Conclusion

This script integrates web scraping and NLP tools to offer an automated approach to screenplay analysis. By extracting dialogues and identifying keywords, it provides insights into a character's linguistic patterns and recurrent themes. A valuable tool for screenwriters, linguists, and film analysts, offering a fresh, computational perspective to cinematic texts.
## Access the Code

The implementation of this project can be found in our [ParsingScripts Python file](ParsingScripts.md).
