# Natural Language Processing
Natural Language Processing (NLP) is an artificial intelligence (AI) that aids computer in *comprehending*, *interpreting*, and *manipulating* human language.

NLP isn't a new subject, but it's progressing quickly thanks to a growing interest in human-machine communication, as well as the availability of massive data, powerful computation, and improved algorithms.

## 10 Best NLP Algorithms
Human language is complex by nature. A technology must grasp not just grammatical rules, meaning, and context, but also colloquialisms, slang, and acronyms used in a language to interpret human speech. NLP algorithms aid computers by  emulating human language comprehension.

---
## 1. Lemmatization and Stemming
- This works nicely with a variety of other morphological variations of a word.
- Allow to limit a single word's variability to a single root.
  - e.g: Reduce `singer, singing, sang and sang` to a singular version of word `sing`.
  - Reduce data space required and construct more powerful and robust NLP algorithms by doing this to all the terms in a document or text
- Pre-processing techniques -> employ one of the two NLP algorithms based on needs before moving forward with NLP to free up data space and prepare the database
- Both are extremely diverse procedures that can be done in a variety of ways, but the end effect is the same for both: `a reduced search area for the problem we're dealing with`.

### Difference between Lemmatization and Stemming

| Lemmatization                                                             | Stemming                                                                                                          |
| ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| - Considers the context and converts the word to its meaningful base form | - Process that stems or removes last few characters from a word, often leading to incorrect meanings and spelling |
| - Lemmatizing the word `Caring` would return `Care`                       | - Stemming the word `Caring` would return `Car`                                                                   |
| - Computationally expensive since it involves look-up tables and what not | - Used in case of large dataset where performance is an issue                                                     |

### Use Case for Lemmatization
- `Search Engine Optimization`
  - Help respond to queries in the best possible way. 
- `Sentiment Analysis`
  - To better understand the user's sentiments in a message
- `Information Retrieval`
  - can easily retrieve information and group similar data

### Pros and Cons of Lemmatization
| Pros                                                                                                                            | Cons                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| - Help better understanding of the text and provides accurate results by understanding the context in which the words are used | - Slow and time-consuming process because it uses a dictionary to conduct a morphological of the inflected words |
---

### Lemmatization Example 
1. Import the libraries
```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer
```
2. Get the input
```python
paragraph = """I have three visions for India. In 3000 years of our history, people from all over 
               the world have come and invaded us, captured our lands, conquered our minds. 
               From Alexander onwards, the Greeks, the Turks, the Moguls, the Portuguese, the British,
               the French, the Dutch, all of them came and looted us, took over what was ours. 
               Yet we have not done this to any other nation. We have not conquered anyone. 
               We have not grabbed their land, their culture, 
               their history and tried to enforce our way of life on them. 
               """
```
3. Tokenization (step before stemming)
```python
sentences = nltk.sent_tokenize(paragraph)
print(sentence)
```
4. Lemmatization

The difference between stemming and lemmatization comes in this step where
`WordNetLemmatizer()` is used instead of `PorterStemmer()`. Rest of the steps are
the same.
```python
lemmatizer = WordNetLemmatizer()
# Lemmatization
for i in range(len(sentences)):
    words = nltk.word_tokenize(sentences[i])
    words = [lemmatizer.lemmatize(word) for word in words if word not in set(stopwords.words('english'))]
    sentences[i] = ' '.join(words)
```
5. Get the output
```python
print(sentences)
```
