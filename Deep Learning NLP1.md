### Representing words as discrete symbols

* 국소 표현(Local Representation) = Discrete Representation
* In traditional NLP, we regard words as discrete symbols.
    * Words can be represented by one-hot vectors.
    * motel = [0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0]
    * hotel = [0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0]
* There is no natural notion of similarity for one-hot vectors.
    * 기본적으로 각 벡터들은 직교(Orthogonal)하기 때문임

### Representing words by their context

* 분산 표현(Distributed Representation)
* 분포 의미론(Distributional Semantics)
    * A word's meaning is given by the words that frequently appear close-by.
* When a word appears in a text, its context is the set of words that appear nearby.

### Word vectors

* We will build a dense vector for each word
    * So that it is similar to vectors of words that appear in similar contexts
* banking = [0.286, 0.792, -0.177, -0.107, 0.109, -0.542, 0.349, 0.271]
* Note: word vectors are sometimes called word embeddings or word representations.
    * They are a distributed representation.
* 일반적으로 말하는 워드 임베딩은 대표적인 분산 표현 방법임

### Word2vec

* A framework for learning word vectors
    * We have a large corpus of text
    * Every word in a fixed vocabulary is represented by a vector
    * Go through each position 't' in the text, which has a center word 'c' and context words 'o'
    * Use the similarity of the word vectors for c and o to calculate the probability of o given c (or vice versa)
    * Keep adjusting the word vectors to maximize this probability

### Word2vec: More details

* Two model variants:
    1) Skip-grams (SG)
        * Predict context ("outside") words (position independent) given center word
    2) Continuous Bag of Words (CBOW)
        * Predict center word (bag of) context words

### Stochastic Gradient Descent

* Problem: J(θ) is a function of all windows in the corpus (potentially billions!)
    * So ∇J(θ) is very expensive to compute
    * You would wait a very long time before making a single update!
* Solution: Stochastic Gradient Descent (SGD)
    * Repeatedly sample windows, and update after each one
