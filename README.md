# NLP-Fake-New-Classifier (School Project)
Datasets download from https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset. As a start for Neutral language processing with scikit learn in python.


## Preprocessing:

Five steps are included for:

**1.	Fix Contractions**
- A python library named “contractions” helps deal with the contractions on a sentence, it defined a map for short form and the full form. For example, it will replace “won’t” with “will not”, “can’t” to “cannot”. 

**2.	Generalize words**
-	This process generalized the words, like, “Google”, “Microsoft”. A pre-trained model by spaCy - “en_core_web_sm” is used. It can extract the noun that can be generalized. For example: 

	1.	"Sam took $50 dollars yesterday"
	2.	[('Sam', 'PERSON'), ('$50 dollars', 'MONEY'), ('yesterday', 'DATE')]


- The word will then be replaced with its label return, like “Sam” will be replaced with “\_PERSON”, “$50 dollars” will be replaced with “\_MONEY”. A “\_” is added to beginning to differentiate the label with the English word.

**3.	Tokenize sentences**
-	This process divided the article (or sentence) into smaller parts, which we called token. In the nltk library, sentences usually are divided based on the regular expression. For example:

	1.	"Sam took $50 dollars yesterday"
	2.	['Sam', 'took', '$', '50', 'dollars', 'yesterday']
  
-	Combined with previous steps, the final tokens of the sentence will be:
	-	['_PERSON', 'took', '_MONEY', '_DATE']

**4.	Remove Stopword**
-	Stopword is the name of the words that we wanted to remove. Usually, words will no meaning like prepositions, pronouns, etc, or words appear many times will be marked as a Stopword. Therefore, in this process, it removed the tokens, generated from the previous steps, if the token is a Stopword, to reduce the effect of meaningless words.  

**5.	Remove Non-English**
-	This process removed the non-English words, to avoid seeing some slang or some rare words. It is similar to “remove Stopword” that both step oxymoron is aiming to reduce the effect of meaningless words. Non-English words were defined as meaningless words because they should not appear frequently, which potentially causing overfitting.

**6.	Lemmatize word**
-	This process generalized the words of different forms. Part of speech of the word is first identified, and WordNetLemmatizer from the nltk is used, for returning the word to its basic form with the part of speech identified. For example:


	1.	['_PERSON', 'took', '_MONEY', '_DATE']
	2.	[('_PERSON', 'NNS'), ('took', 'VBD'), ('_MONEY', 'NN'), ('_DATE', 'NN')]
  
-	Word ‘took’ is identified as a verb, so after lemmatizing, it becomes ‘take’. 

## Result:

|Model| Precision | Recall | F1 Score | Time| 
|-| - | - | - | -| 
|Decision Tree Classifier| 0.95| 0.96| 0.95| 343s|
|Random Forest Classifier| 0.95| 0.96| 0.95| 154s| 
|Multinomial Naive Bayes| 0.93| 0.90| 0.91| 3s| 


