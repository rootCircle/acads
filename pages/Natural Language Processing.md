## Introduction
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