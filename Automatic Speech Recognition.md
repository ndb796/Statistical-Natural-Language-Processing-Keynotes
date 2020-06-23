### The Noisy Channel Model

* Automatic Speech Recognition (ASR) is a process by which an acoustic speech signal is converted into a set of words.
* The noisy channel model
    * Acoustic input considered a noisy version of a source sentence
* What is the most likely sentence out of all sentences in the language L given some acoustic input O?
  * argmax P(W|O) → argmax P(O|W)P(W)/P(O) → argmax P(O|W)P(W)

### Feature Extraction

* The Mel-Frequency Cepstrum Coefficients (MFCC) is a popular choice.

### Acoustic Model

* Provide P(O|Q) = P(features|phone)

### Pronunciation Model

* Provide P(Q|W) = P(phone|word)

### Language Model

* Provide P(W); the probability of the sentence
   * Word sentence: W = w1, w2, w3, ..., wn
   * N-gram Language Model
       * N-gram language models use the previous (n - 1) words to represent the history

### Decoding

* Find argmax P(W|O)
