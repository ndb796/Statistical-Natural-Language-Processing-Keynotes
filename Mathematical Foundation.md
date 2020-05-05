## Probability

### Experiments & Sample Space

* 표본 공간 (Sample space) Ω: Set of possible basic outcomes (한 번의 시도를 통해 발생할 수 있는 결과의 집합)
    * Coin toss (Ω = {head, tail}), dice (Ω = {1, ..., 6}), quality test (Ω = {bad, good})
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
    * Dice: natural "numbering" [1, 6], coin: {0, 1}
