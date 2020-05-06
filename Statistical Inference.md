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
