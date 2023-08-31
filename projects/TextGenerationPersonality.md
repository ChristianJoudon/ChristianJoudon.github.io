---
layout: project
type: project
image: img/Screenshot 2023-08-30 at 9.57.24 PM.png
title: "Text Generation from Personality Traits"
date: 2022-01-01  # Adjust the date as necessary
published: true
labels:
  - Numpy
  - Pandas
  - Sickit-Learn
  - TfidfVectorizer
  - Linear Regression
  - Textgenrnn
  - Python
summary: "I designed a software that extracts and compiles a keyword dictionary for individual characters from film or TV scripts."
---

Understanding Text Generation for Predicted Personality Traits

Modern computational tools provide a unique opportunity to not only understand human personality from text, but to artificially generate text that mirrors specific personality traits. This repository leverages Python, along with popular libraries such as NumPy, Pandas, and Scikit-learn, to develop a sophisticated workflow that aims to achieve this goal. The analysis pipeline presented herein encompasses data preprocessing, model training, and text generation.

1. Importing Essential Libraries
The following libraries form the backbone of our text analysis and generation pipeline:

NumPy and Pandas: Used for data manipulation and preprocessing.
Scikit-learn: Offers tools for machine learning and data analysis.
TfidfVectorizer: For feature extraction from text.
LinearRegression: Linear regression modeling.
Utilities for dataset splitting and creating a sequence of operations (Pipeline) are employed.
textgenrnn: A recurrent neural network library for text generation.
2. Data Acquisition and Preprocessing
The dataset, assumed to be a CSV file, contains texts and their corresponding personality trait scores. The file is loaded into a pandas DataFrame, and the data is split into training and test sets. The split ensures that 80% of the data is used for training while 20% is reserved for testing.

3. Feature Extraction and Model Training
A pipeline is constructed to first convert the text data into numerical features using the Term Frequency-Inverse Document Frequency (TF-IDF) technique. Subsequently, a linear regression model is applied to these features to predict personality traits. This streamlined approach ensures consistency in operations and reduces potential errors in the modeling process.

4. Text Generation Model Training
The textgenrnn library is employed to train a text generation model on our dataset. This model learns patterns and structures in the provided text and becomes capable of generating new, similar texts.

5. Generating Text with Specific Personality Traits
A function named generate_text_with_personality is defined, which generates text with a desired personality trait score. It starts by producing a piece of text using the textgenrnn model. This generated text is then passed through the previously trained linear regression model to predict its personality trait score. If the predicted score is within a specified tolerance (in this case, 0.1) of the desired score, the text is accepted. Otherwise, new texts are continuously generated and evaluated until one meets the criteria.

To demonstrate the system's capabilities, an example usage is provided at the end. The goal is to generate a text with a personality trait score of 0.7. Once achieved, the generated text is printed for review.

This pipeline showcases the synergy between traditional machine learning models and deep learning text generation techniques. The innovative approach allows for the creation of text data that can be mapped to specific personality trait scores, which has promising implications for research in psychology, marketing, and other domains.
