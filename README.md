# Experiment-6---Implementation-of-Semantic-Analysis

## Aim : Construct a python program to read a text from a file.Identify the verbs from the text file and provide synonyms for all verbs using Natutal Language Processing 

## Algorithm:
1) Install the required libraries:
           Install nltk (Natural Language Toolkit) by running pip install nltk in your terminal.
           Install WordNet by running nltk.download('wordnet') in your Python script or notebook.
2) Import the necessary libraries and modules.
3) Read the text file.
4) Tokenize the text into sentences and words.
5) Identify verbs using part-of-speech tagging.
6) Get synonyms for each verb.
7) Process the text file and display the verbs and their synonyms.
## Program:
import nltk
from nltk.corpus import wordnet

# Download NLTK data
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

def get_synonyms(word):
    synonyms = set()
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.add(lemma.name())
    return synonyms

def process_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
        
        # Tokenize the text into sentences
        sentences = nltk.sent_tokenize(text)
        
        for sentence in sentences:
            # Tokenize each sentence into words
            words = nltk.word_tokenize(sentence)
            
            # Perform part-of-speech tagging
            pos_tags = nltk.pos_tag(words)
            
            # Extract verbs
            verbs = [word for word, pos in pos_tags if pos.startswith('V')]
            
            # Get synonyms for each verb
            for verb in verbs:
                synonyms = get_synonyms(verb)
                print(f"Verb: {verb}")
                print(f"Synonyms: {', '.join(synonyms)}\n")

file_path = 'text.txt'  
process_text_file(file_path)

## Output:
![image](https://github.com/Kavya-Bollineni22/Experiment-6---Implementation-of-Semantic-Analysis/assets/75235813/bf70381f-2067-45ba-bd52-56de7ac52b45)

## Result
Thus, we have successfully implemented a program for Natural Language Processing.
