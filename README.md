# Twitter
<strong>Sentiment Analysis with Twitter data and PySpark</strong>

Download Dataset [here](https://www.kaggle.com/datasets/kazanova/sentiment140)

1. Read data and calculate vocab size
2. EDA to find relation of sentiment with:
   - length of tweet
   - time of tweet
3. Prepocessing
   - "Text"
   - "Target"
   - Add 3 new fields: "WordCount", "Weekday", "Hour"
4. Feature extraction with some methods and predict target by Logistic Regression to find best features:
   - CountVectorizer + IDF + Logistic Regression => <strong>the best AUC method</strong>
   - HashTF + IDF + Logistich Regression => good method and fast
   - Word2Vec + Logistic Regression => the worst AUC method, because vector of a sentence is the average of vectors of all words in the sentence. And it is very slow.
     |                   |Time of extracting (seconds) |AUC (%)|Accuracy (%)|
     |-------------------|-----------------------------|-------|------------|
     |CountVectorizer–IDF|450,07                       |84,7   |77,69       |
     |HashTF–IDF         |158,00                       |84,14  |77,25       |
     |Word2Vec           |590,61                       |74,25  |67,76       |     
5. Try some models to find the best model to classify:
   - Logistic Regression => good AUC but faster than Linear SVM
   - Naive Bayes => the worst AUC. Because the fields make feature are not independent, so it is not suitable with Naive Bayes.
   - Decision Tree => bad AUC. Because the feature vectors have many dimensions. It makes the depth of tree (default is 5) is not enough to classify clearly, and need much time to build the tree.
   - Linear SVM => <strong>the best AUC</strong>
     |Time of training (seconds)|	AUC (%)	| Accuracy (%)|
     |--------------------------|---------|-------------|
     |Logistic Regression + TF-IDF|	174,89|	84,70|	77,69|
     |Naïve Bayes + TF-IDF| 	71,32|	52,66|	75,30|
     |Decision Tree + TF-IDF| 	6311,49|	56,92|	59,11|
     |Linear SVM + TF-IDF|	250|	85,10|	77,80|
