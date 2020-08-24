# NLPfin
using NLP tools to model financial assets
The goal of this project is to use NLP tools to analyze vast amounts of textual data to infer financial asset properties. Financial pricing and return data is very limiting. It is especially limiting when estimating relationships between assets. In order to estimate the most straightforward correlation matrix between N assets, we need N*(N-1)/2 parameters. For large N, this model becomes extremely weak and matrix properties are not desirable. This is because financial pricing data has limited history, anywhere between a few years to a few decades at the very most.
NLP analysis allows us to use the vast amounts of textual data to infer facts about financial assets. It can overcome lack of financial data. And such analysis is absolutely crucial when dealing with assets with short history or no history at all (private assets).
There are two Jupyter notebooks and two files:
```
(A) Financial Word2Vec Train
(B) Financial Word2Vec Infer
(C) A sample file 'articles_final.csv' contains 30k articles downloaded from Bloomberg and Yahoo Finance (https://www.dropbox.com/s/vwcklshfuhvsdz8/articles_final.zip?dl=0 )
(D) Assets.xlsx is just a file that allows us to resolve some tickers to names and vice versa
```

The first notebook contains code needed to train your own word2vec model. Word2Vec is a standard NLP model pioneered by Google researchers. At this point in 2020 it is far from the most advanced model, but it is still very robust and useful. It is much quicker to train than some of the newer models, such as Transformer models.
The second notebook uses the model created in the first one to infer facts about financial assets. As an example, we use pr=model.wv.most_similar(['Tesla'],topn=200) to find 200 most similar concepts to Tesla in our text corpus. 
What is notable is that most similar concepts to Tesla include:
```
'Tesla': (0.814926266670227, 'Tsla'),
 'Musk': (0.7463796138763428, ''),
 'Elon': (0.7269102334976196, ''),
 'Automaker': (0.6607990264892578, ''),
 'Nio': (0.6583075523376465, 'Nio'),
 'Forward': (0.583686351776123, 'Fwrd'),
 'Nikola': (0.5724355578422546, 'Nkla'),
 'Gigafactory': (0.5711787939071655, ''),
 'Cybertruck': (0.5705713629722595, ''),
 'Cadillac': (0.5384987592697144, ''),
 'Rival': (0.5378053784370422, ''),
 'Nvidia': (0.5317240953445435, 'Nvda'),
 'Xpeng': (0.5313283801078796, '')
 ```
 
 It contains companies such as Nio and Nikola, with very little price history. It also contains another competitor to Tesla called Xpeng, which is not traded at all at this point. Yet, we can estimate correaltions between those assets using our model.
Beyond finding correlations, here are possible uses for NLP methods in finance.
- Sentiment analysis
- Simulating neural networks to come up with very rich datasets that will allow us to estimate much richer models i.e. power law copulas
