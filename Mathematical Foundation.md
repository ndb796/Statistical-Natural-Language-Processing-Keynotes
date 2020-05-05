## Probability

### Experiments & Sample Space

* 표본 공간 (Sample space) Ω: Set of possible basic outcomes (한 번의 시도를 통해 발생할 수 있는 결과의 집합)
    * Coin toss (Ω = {head, tail}), die (Ω = {1, ..., 6}), quality test (Ω = {bad, good})
    * \# of traffic accidents somewhere per year (Ω = N)
    * Spelling errors (Ω = Z*), where Z is an alphabet, and Z* is a set of possible strings over such alphabet
* Repeat experiment many times, record how many times a given event A occurred.
* Example
    * Experiment: Three times coin toss
    * Ω = {HHH, HHT, HTH, HTT, THH, THT, TTH, TTT}
    * Let's count cases with exactly two tails: A = {HTT, THT, TTH}
    * Run an experiment 1000 times (i.e. 3000 tosses)
    * Counted: 386 cases with two tails (HTT, THT, or TTH)
    * Estimate: P(A) = 386 / 1000 = 0.386
    * Run again: 373, 399, 382, 355, 372, 406, 359
    * P(A): 0.379 (weighted average) or simply 3032 / 8000
    * Uniform distribution assumption: P(A) = 3/8 = 0.375

### Joint and Conditional Probability

* Joint Probability: P(A,B) = P(A∩B)
* Conditional Probability: P(A|B) = P(A,B) / P(B)

### Bayes Rule

* P(A,B) = P(B,A), Then P(A|B)P(B) = P(B|A)P(A).
* <b>Bayes Rule: P(A|B) = P(B|A)P(A) / P(B)</b>

### Independence

* If A and B are independent, P(B|A) = P(B)

### Chain Rule

* P(A1, A2, A3, ..., An) = P(A1|A2, A3, ..., An) * P(A2|A3, A4, ..., An), ..., P(An-1|An) * P(An)

### Golden Rule

* If you interested in an event A given B to estimate P(A|B):
    * argmax P(A|B) = argmax P(B|A)P(A) / P(B) = <b>argmax P(B|A)P(A)</b>

### Random Variables

* Is a function X: Ω → Q
    * <b>It's easier to handle real numbers than real-world events</b>
* Random variable is dicrete if Q is countable (i.e. also if finite)
* Example
    * Die: natural "numbering" [1, 6], coin: {0, 1}

### Entropy

* Measure of uncertainty
    * The higher the entropy, the higher uncertainty, but the higher "surprise" we can get out of an experiment
* Let P(X) be a distribution of random variable X
    * <b>H(X) = -∑P(X)logP(X)</b>
* Example (Entropy 값 계산해보기)
    * Toss a fair coin: Ω = {head, tail}
    * P(head) = 0.5, P(tail) = 0.5
    * H(P) = -0.5 log (0.5) + -0.5 log 0.5 = 1
* If a result of an experiment is known ahead of time, H(P) = 0
    * 매 번 특정 이벤트만 발생하는 경우에는, 정보량이 0이라고 할 수 있음
* 기대값 (Expectation) 공식
    * <b>E(X) = ∑P(X) * X</b>
* Entropy is non-negative
* H(P) is concave

### Perplexity

* 언어 모델을 평가하기 위한 내부 평가 지표
    * G(P) = pow(2, H(P))
* 2 equiprobable outcomes: H(P) = 1
* 32 equiprobable outcomes: H(P) = 5
* The lower entropy, the lower perplexity

### Joint and Conditional Entropy

* Joint entropy: H(X, Y) = -∑∑P(X,Y)logP(X,Y)
* Chain rule
    * H(X, Y) = H(Y|X) + H(X)
    * H(X, Y) = H(X|Y) + H(Y)
    * 일반적인 Probability와 공식이 유사하게 생김: P(A,B) = P(A|B) * P(B)
* H(X, Y) <= H(X) + H(Y)
* Conditional entropy: H(Y|X) = -∑∑P(X,Y)logP(Y|X)
* Conditional entropy is better than unconditional
    * H(Y|X) <= H(Y)

### Kullback-Leibler Distance

* <b>D(P||Q) = ∑P(X)log(P(X)/Q(X)) = E[log(P(X)/Q(X))]</b>
* Is not a distance metric
    * Not symmetric
    * Does not satisfy the triangle inequality

### Mutual Information (MI)

* Mutual Information: I(X, Y) = D(P(X,Y) || P(X)P(Y))
* 상호정보량은 Joint Probability와 Marginal Probability의 KL-Divergence로 표현
* MI measures how much Y contributes easing the prediction of X
* <b>I(X, Y) = D(P(X,Y) || P(X)P(Y)) = ∑∑P(X,Y)log(P(X,Y)/P(X)P(Y))</b>
* I(X,Y) = H(X) - H(X|Y) = H(Y) - H(Y|X)
* I(X,Y) >= 0

### Jensen's Inequality

* For distribution P(X), and convex f,
    * f(∑P(X) * X) <= ∑P(X) * f(x)
    * f(E[X]) <= E[f(x)]

### Cross Entropy

* Joint entropy는 하나의 확률 분포 P에 대해서, X와 Y 두 개의 사건이 갖는 정보량으로 정의
* Cross entropy는 두 개의 확률 분포 P와 Q에 대해서, 하나의 사건 X가 갖는 정보량으로 정의
