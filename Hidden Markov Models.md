### Review: Markov Process

* Bayes formula (Chain rule)
    * P(W) = P(w1, w2, ..., wn) = ∏P(wi|w1, w2, w3, ..., wi-1)
    * 단, 모든 이전 상태(State) 정보를 다루는 것은 많은 파라미터를 요구
* N-gram Language Models:
    * Markov process (chain) of the order n-1
    * P(W) = P(w1, w2, ..., wn) = ∏P(wi|wi-n+1, wi-n+2, wi-n+3, ..., wi-1)

### Markov Properties

* Generalize to any process (not just words/LM):
    * Sequence of random variables: X = (x1, x2, ..., xn)
    * Sample space S (states), size N: S = {s0, s1, s2, ..., sn)
* Limited History
* Time invariance
    * 시간에 대한 불변성: 오늘의 값과 내일의 값이 모두 동일 (시스템의 내부가 시간에 따라 변하지 않음)

### Hidden Markov Models

* The simplest HMM: states generate [observable] output, but remain "invisible"
* Five-tuple (S, s0, Y, Ps, Py), where:
    * S = {s0, s1, s2, ..., sn} is the set of states, s0 is the initial state, <b>(Invisible)</b>
    * Y = {y1, y2, y3, ..., ym} is the output alphabet, <b>(Visible)</b>
    * Ps(sj|si) is the set of prob. distributions of transitions,
    * Py(yk|si, sj) is the set of output (emission) prob. distributions.
* Example
    * S = {x, 1, 2, 3, 4}, s0 = x
    * Y = {t, o, e}

### Using the HMM

* The generation algorithm:
    1. Start in s = s0.
    2. Move from s to s' with probability Ps(s'|s).
    3. Output (emit) symbol yk with probability Ps(yk|s,s').
    4. Repeat from step 2 (until somebody says enough).
* More interesting usage:
    * Given an output sequence Y = {y1, y2, ..., yk}, compute its probability.
    * Given an output sequence Y = {y1, y2, ..., yk}, compute the most likely sequence of states which has generated it.
