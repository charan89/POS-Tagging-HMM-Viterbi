# NLP-POS-tagging-using-HMMs-and-Viterbi-heuristic
This project uses the tagged treebank corpus available as a part of the NLTK package to build a part-of-speech tagging algorithm using Hidden Markov Models (HMMs) and Viterbi heuristic.

# The data set
The data set comprises of the Penn Treebank dataset which is included in the NLTK package. The dataset consists of a list of (word, tag) tuples. This data set is split into train and test data set using sklearn's train_test_split function.

# The HMM based POS tagging algorithm
Hidden Markov Model based algorithm is used to tag the words. Given a sequence of words to be tagged, the task is to assign the most probable tag to the word.

In other words, to every word w, assign the tag t that maximises the likelihood P(t/w). Since P(t/w) = P(w/t). P(t) / P(w), after ignoring P(w), we have to compute P(w/t) and P(t).

P(w/t) is basically the probability that given a tag (say NN), what is the probability of it being w (say 'building'). This can be computed by computing the fraction of all NNs which are equal to w, i.e.

P(w/t) = count(w, t) / count(t).

The term P(t) is the probability of tag t, and in a tagging task, we assume that a tag will depend only on the previous tag. In other words, the probability of a tag being NN will depend only on the previous tag t(n-1). So for e.g. if t(n-1) is a JJ, then t(n) is likely to be an NN since adjectives often precede a noun (blue coat, tall building etc.).

Given the penn treebank tagged dataset, we can compute the two terms P(w/t) and P(t) and store them in two large matrices. The matrix of P(w/t) will be sparse, since each word will not be seen with most tags ever, and those terms will thus be zero.

# Viterbi algorithm
Viterbi algorithm is a dynamic programming based algorithm. Instead of computing the probabilities of all possible tag combinations for all words and then computing the total probability, Viterbi algorithm goes step by step to reduce computational complexity. 
For each word, the algorithm finds the most likely tag by maximizing P(t/w).

# Evaluating the Viterbi algorithm
Custom function for the Viterbi algorithm is developed and an accuracy of 87.3% is achieved on the test data set.
