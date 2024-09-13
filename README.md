# Contexto-Like
Inspired by [Contexto](https://contexto.me/), given any word, the most similar words are displayed in a list and ranked, using [GloVe](https://nlp.stanford.edu/projects/glove/) embeddings. In particular, the Wikipedia 2014 + Gigaword 5 (6B tokens, 400K vocab) was used with the 50d vectors. 

Download the embeddings on their [GitHub](https://github.com/stanfordnlp/GloVe?tab=readme-ov-file). See the complete Python notebook file in the Google Colab [link](https://colab.research.google.com/drive/1xd1DMDiwihfk0RHhVVkYqE87xIPcE1Aw?usp=sharing). 

Example:

![image](https://github.com/user-attachments/assets/02d04463-f0a2-4c6c-8c80-1355d1d151e2)

## Preprocessing
The embeddings were cleaned, similar to how it's done in Contexto, where only lemmatized words with no punctuation or numbers can be displayed in the rankings. This results in a cleaner display. For example, when using the word rabbit, the most similar word shown will not be rabbits:

![image](https://github.com/user-attachments/assets/f2e80cc1-bd91-4807-b9dc-80ad2e23357b)

## Similarity Metrics
Three common vector similarity metrics are used: dot product (inner product), Euclidean distance, and cosine similarity. Euclidean distance and cosine similarity tend to give extremely similar results that seem quite accurate, whereas dot product gives slightly different results that also seem accurate. Regarding computation time, euclidean distance and cosine similarity take noticeably longer than dot product which is quite efficient. 

Example:

![image](https://github.com/user-attachments/assets/4fcd418e-1e05-451b-956d-f6063b3d1d21) ![image](https://github.com/user-attachments/assets/e1bd8dd2-a857-4903-be7b-f79ba4c080d1) ![image](https://github.com/user-attachments/assets/f0ec8cae-cfe9-4408-9c21-6ee74e126856)

As seen above, Euclidean distance and cosine similarity give very similar results in contrast with dot product, but all of them look reasonable. Additionally, we can observe that to calculate similarity over the whole vocabulary, it took Euclidean distance 3 seconds, cosine similarity 2 seconds, and dot product less than 1 second. 

## Libraries used:
- [NumPy](https://numpy.org/) for storing the embeddings and calculating dot product and cosine similarity
- [SciPy](https://scipy.org/) for calculating Euclidean distance
- [NLTK](https://www.nltk.org/) for lemmatizing the words, using [WordNetLemmatizer](https://www.nltk.org/api/nltk.stem.WordNetLemmatizer.html?highlight=wordnet) 
