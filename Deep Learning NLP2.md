### Classification setup and notation

* Generally we have a training dataset consisting of samples
    * {x_i, y_i}
    * x_i are inputs, e.g. words (vectors), sentences, documents etc.
    * y_i are labels we try to predict, for example:
        * classes: 감정(sentiment), 개체명(named entities), 의사 결정(decision)
        * other words
        * later: multi-word sequences

### Neural Nets for the Win!

* Neural networks can learn much more complex functions and nonlinear decision boundaries.

### Named Entity Recognition (NER)

* The task: find and classify names in text, for example:
    * Input: "The European Commission said on Thursday it disagreed with German advice."
    * Output: "The European Commission [ORG] said on Thursday it disagreed with German [MISC] advice."
* Possible purposes:
    * Tracking mentions of particular entities in documents
    * For question answering, answers are usually named entities
    * A lot of wanted information is really associations between named entities

### Why might NER be hard?

* Hard to know if something is an entity
    * Is there a school called "Future School" or is it a future school?
* Hard to know class of unknown/novel entity

### Window classification

* Idea: classify a word in its context window of neighboring words
* For example, Named Entity Classification of a word in context:
    * Person, Location, Organization, None
* A simple way to classify a word in context might be to average the word vectors in a window.
    * We can classify the average vector
    * Problem: that would lose position information

### Window classification: Softmax

* Train softmax classifier to classify a center word by taking concatenation of word vectors surrounding it in a window.
