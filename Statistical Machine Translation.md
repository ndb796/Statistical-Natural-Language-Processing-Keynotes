### Machine Translation Pyramid

* RBMT (Rule-Based Machine Translation)
    * Analysis, Structure transfer, and Generation
* SMT/NMT
    * Direct Translation

### SMT: Noisy Channel Model

* Noisy Channel
    * Encoder
    * We get the data through noisy channel
    * The clean (original) data can not be observed directly
    * Noisy channel adds some noise to the data
* Decoder
    * Estimates the original data from the noisy  data
    * Recovered data may contain some errors
    * Our goal is designing the decoder that recovers  the data with minimum errors

### Noisy Channel Model in SMT

* Given a source sentence S find T that maximizes the probability of T given S
* Language model
    * Role: Making a fluent sentence
    * Model for the target language
* Translation model:
    * Role: Making a correct translation
    * Model for both languages
* Decoder
    * Role: Find a sentence which gives the best score
    * We use P(S|T)P(T) rather than P(T|S).

### Parallel Corpus

* Two or more texts written in different languages have the same meaning
* We need alignments at least sentence level

### N-gram Language Model

* Probability of next words given history
    * We can not store all the word sequences if the length is not limited
    * The words sequence is very scarce if the length is long
* Approximation
    * Assume that the probability of a word is independent to too far history
    * Use limited history
        * 0 history - Unigram
        * 1 history - Bigram
        * 2 history - Trigram
* N-gram is the most popular method for scoring sentences
