# Quora-Insincere-Questions-Classification


# Summary

Our strategy employs two noteworthy approaches :

First, we try text processing Without Pretrained Embeddings. 

Second, we use the Glove Embeddings.

We found that Pretrained embeddings seem to give better results compared to the non-pretrained model.



# Problem

An existential problem for any major website today is how to handle toxic and divisive content. 
Quora wants to tackle this problem head-on to keep its platform a place where users can feel safe sharing their knowledge with the world.
The objective is to predict whether a question asked on Quora is sincere or not. 
An insincere question is defined as a question intended to make a statement rather than look for helpful answers.




# Solution

I used Natural Language Processing for text classification. We will compare the performance of models using these pre-trained embeddings against the baseline model that doesn't use any pre-trained embeddings.
Embeddings generally represent geometrical encodings of words based on how frequently appear together in a text corpus.




# Data

The training data includes the question that was asked, and whether it was identified as insincere (target = 1). 
The ground-truth labels contain some amount of noise: they are not guaranteed to be perfect.

Note that the distribution of questions in the dataset should not be taken to be representative of the distribution of questions asked on Quora. 
This is, in part, because of the combination of sampling procedures and sanitization measures that have been applied to the final dataset.



# Modeling

Preprocessing steps :

  - Split the training dataset into the train and Val sample. Cross-validation is a time-consuming process and so let us do simple
     train_val split   
  - Fill up the missing values in the text column with 'na'
  - Tokenize the text column and convert them to vector sequences
  - Pad the sequence as needed - if the number of words in the text is greater than 'max_len' truncate them to 'max_len' or 
     if the number of words in the text is lesser than 'max_len' add zeros for remaining values.
     
   

Modeling without Pretrained Embeddings :

Now that we are done with all the necessary preprocessing steps, we can first train a Bidirectional GRU model. 
We will not use any pre-trained word embeddings for this model and the embeddings will be learned from scratch. 
Please check out the model summary for the details of the layers used.

Modeling with Pretrained Embeddings :

I used the Glove embeddings which is pre-trained using billions of words could improve our accuracy score as compared to training our embedding and rebuild the GRU model.
GLOVE learns by constructing a co-occurrence matrix (words X context) that count how frequently a word appears in a context.



# Results

Overall pre-trained embeddings seem to give better results compared to the non-pre-trained model.
