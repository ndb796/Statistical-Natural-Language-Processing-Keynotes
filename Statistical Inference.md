### Probabilistic Language Modeling

* Goal: Compute the probability of a sentence or sequence of words
    * P(W) = P(w1, w2, w3, w4, w5, ..., wn)
    * 어떠한 문장이 등장할 확률을 구하는 것이 목표
    * 하나의 문장(W)은 여러 개의 단어(w)로 구성
* Related task: Probability of an upcoming word
    * P(w5|w1, w2, w3, w4)
* A model that computes either of these:
    * P(W) or P(wn|w1, w2, w3, ..., wn-1) is called a language model

### Perfect Language Model

* Sequence of word forms
* The big (modeling) question:
    * P(W) = ?
* We know Chain Rule,
    * P(W) = P(w1, w2, w3, ..., wd) = p(w1) * p(w2|w1) * P(w3|w1, w2) * P(wd|w1, w2, ..., wd-1)
    * But, it's not practical (even short W → too many parameters)

### 마르코프 체인 (Markov Chain)

* 마르코프 성질이란, n + 1번째 상태(State)는 오직 n회의 상태, 혹은 그 이전 일정 기간의 상태에만 영향을 받는 것을 의미
    * 여기에서는 단어(Word)가 상태(State)를 의미
* Unlimited memory:
    * for wi, we know all its predecessors w1, w2, w3, ..., wi-1
* Limited memory:
    * we disregard "too old" predecessors
    * remember only k previous words: wi-k, wi-k+1, wi-k+2, ..., wi-1
        * 앞의 모든 단어를 확인하지 말고, k개의 이전 단어만 확인

### N-gram Language Models

* (n-1)th order Markov approximation → n-gram LM
    * <b>P(W) = ∏P(wi|wi-n+1, wi-n+2, ..., wi-1)</b>
* How large n?
    * Nothing is enough (theoretically)
    * But anyway: as much as possible
    * Empirically: 3

### Maximum Likelihood Estimate

* MLE: Relative frequency
* Trigrams from Training Data T:
    * Count sequences of three words in T: c(wi-2, wi-1, wi)
    * Count sequences of two words in T: c(wi-1, wi)
    * <b>p(wi|wi-2,w-1) = count(wi-2, wi-1, wi) / count(wi-1, wi)</b>
    * 단순히 Likelihood 공식을 이용하여 다음에 나올 문자(wi)의 확률을 계산할 수 있음

### Intuition of Perplexity

* A better model of a text
    * Is one which assigns a higher probability to the word that actually occurs

### Perplexity

* The best language model is one that best predicts an unseen test set
    * Gives the highest P(sentence)
* PP(W) = pow(P(w1, w2, w3, ..., wn), -1/N)
    * For bigrams: PP(W) = pow(∏P(wi|wi-1), -1/N)
* Lower perplexity = better model
|N-gram Order|Unigram|Bigram|Trigram|
|------|------|------|------|
|Perplexity|962|170|109|

### Language Modeling Example

* Training data:
    * "\<s\> \<s\> He can buy the can of soda."
* Unigram P1: P(He) = P(buy) = P(the) = P(of) = P(soda) = P(.) = 0.125, P(can) = 0.25
* Bigram P2: P(He|\<s\>) = 1, P(can|He) = 1, P(buy|can) = 0.5, P(of|can) = 0.5, p(the|buy) = 1, ...
* Trigram P3: P(He|\<s\>,\<s\>) = 1, P(can|\<s\>,He) = 1, P(buy|He,can) = 1, P(of|the,can) = 1, ...
* H(P1) = 2.75, H(P2) = 0.25, H(P3) = 0
* When the test data = "\<s\> \<s\> It was the greatest buy of all."
    * We want to make all probabilties non-zero → <b>Data sparseness handling</b>

### Eliminating the Zero Probabilities: Laplace Smoothing

* There are many ways of smoothing
* Predicting words w from a vacabulary V, training data T:
    * <b>P'(w|h) = (c(h, w) + 1) / (c(h) + |V|)</b>
* Example
    * Training data: "\<s\> what is it what is small?", |T| = 8
    * V = {what, is, it, small, ?, \<s\>, flying, birds, are, a, bird, .}, |V| = 12
    * P(what is it?) = 0.25 * 0.25 * 0.125 * 0.125
    * <b>P'(what is it?) = 0.125 * 0.125 * 0.1 * 0.1</b>
