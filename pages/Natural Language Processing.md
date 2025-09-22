- Source: https://youtube.com/playlist?list=PLKnIA16_RmvZo7fp5kkIth6nRTeQQsjfX&si=7309uFb4G9YqrBe7
- ## Introduction
	- ### Common NLP tasks
		- Document Classification
		- Sentiment Analysis
		- Information Retrieval
		- POS tagging
		- Language Detection/Translation
		- Conversational Chatbot
		- Knowledge Graphs
		- Text Summarization
		- Topic Modelling/Text Generation/Spell Check/Text Parsing/ Speech to Text
	- ### Approach
		- Heuristic: Rule based, wordnet, open mind common sense
		  logseq.order-list-type:: number
		- Machine Learning: Naive Bayes, Logistic Regression, SVM etc
		  logseq.order-list-type:: number
		- Deep learning: Have sequential context. RNN, LSTM, GRU/CNN, transformers, autoencoders
		  logseq.order-list-type:: number
	- ### Challenges in NLP
		- Ambiguity
		- Contextual Words
		- Colloquialisms and slang
		- Synonym
		- Irony, Sarcasm and tonal diff
		- Spelling Errors
		- Creativity
		- Diversity
- ## NLP Pipeline
	- Data Acquisition -> Text Prep(Cleanup, Pre-processing) -> Feature Engineering -> Modelling (Building, Eval) -> Deploy
	- Data Acquisition
		- Less data: Data augmentation using synonym, bigram flip (flip word pair), back translate, add noise
	- Text Preparation
		- Cleaning: HTML/tag cleaning, emojis, spelling
		- Basic pre-processing
			- Basic: Tokenization -> Sentence or Word
			- Optimal: Stop Word remove(which add no meaning), Stemming(convert to root tense form), Removing digits/punctuation, lower-casing, language detection
		- Advanced pre-processing
			- POS tagging (done without stop word removal)
			- Parsing
			- Coreference Resolution (Replace pronoun with person/entity)
	- Feature Engineering
		- Text into numbers (eg sentiment on text, # of +ve words etc)
		- Deep learning don't require feature engineering, while ML does, but lose on model interpretability.
	- Modelling
		- Modelling: Heuristic, ML Algo, Deep Learning (Transfer Learning), Cloud API
			- Amount/nature of data, if low -> heuristic, then increase use heuristic as feature in ML Algo then maybe deep if needed
		- Evaluation: intrinsic (recall, precision, perplexity etc), extrinsic (business logic based)
	- Deployment
		- Deploy
		- Monitoring
		- Update
- ### Text Preprocessing
	- Lowercasing
	  logseq.order-list-type:: number
	- Remove HTML tags: Using regex
	  logseq.order-list-type:: number
	- Remove URLs: Using regex
	  logseq.order-list-type:: number
	- Remove Punctuation: 
	  logseq.order-list-type:: number
		- ![image.png](../assets/image_1758565173874_0.png)
		- Lemmetization can produce side-effects like Hello!, Hello, Hello, ! etc
	- Chat Word treatment: rofl, lmao
	  logseq.order-list-type:: number
	- Spelling correction
	  logseq.order-list-type:: number
	- Removing stop words: a, the, of, are, my (not done in POS tagging)
	  logseq.order-list-type:: number
	- Handling emojis: either remove or demojify.
	  logseq.order-list-type:: number