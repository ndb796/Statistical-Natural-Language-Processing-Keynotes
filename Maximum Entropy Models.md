### Introduction

* So far we've looked at "Generative Models"
    * Language models, Naive Bayes
* But there is now much use of conditional or discriminative probabilistic models
    * in NLP, Speech, IR (and ML generally)
* Because:
    * They give high accuarcy performance
    * They make it easy to incorporate lots of linguistically important features
    * They allow automatic building of language independent, retargetable NLP modules

### Generative vs Discriminative

* Generative: Naive Bayes, HMM (Hidden Markov Model)
* Discriminative: Logistic Regression, Classification

### Features

* Features f are elementary pieces of evidence
     * links aspects of what we observe d with a category c that we want to predict
* Models will assign to each feature a <b>weight</b>
    * 딥 러닝(Deep Learning)을 이용하는 경우, 특징(Features) 값을 스스로 잘 잡아내는 경우가 많음

### Feature-based (Log-Linear) Classifiers

* Linear classifiers at classification time:
    * Linear function from feature sets {f} to classes {c}.
    * vote(c) = Σλf(c,d)
    * <b>Then, choose the class c which maximizes Σλf(c,d).</b>
* There are many ways to choose weights for features
    * Perceptron: find a currently misclassified example, and nudge weights in the direction of its correct classification
    * Margin-based methods: Support Vector Machines (SVM)
* Exponential (log-linear, maxent, logistic) models:
    * Make a probabilistic model from the linear combination Σλf(c,d)
        * <b>P(c|d,λ) = exp(Σλf(c,d)) / Σexp(Σλf(c',d))</b>
        * c는 특정 클래스, c'는 전체 클래스를 의미
    * 흔히 Image Classification에서 사용되는 형태
    * The weights are the parameters of the probability model
        * combined via a "softmax" function
