### Spoken Language Understanding

* Spoken language understanding is to map natural language speech to frame structure encoding of its meanings.
* What's the difference between NLU and SLU?
    * Robustness; noise and ungrammatical spoken language
    * Domain-dependent; Further deep-level semantics (e.g. Person vs. Cast)
    * Dialog; dialog history-dependent and utt. by utt. analysis
* Traditional approaches; natural language to SQL conversion
* Speech → (ASR) → Text → (SLU) → Semantic Frame → (SQL Generate) → SQL → (Database) → Response

### Semantic Representation

* Semantic frame
    * An intermediate semantic representation to serve as the interface between user and dialog system.

### Semantic Frame Extraction

1) Main Action Identification: Classification
2) Frame-Slot Object Extraction: Named Entity Recognition
3) Object-Attribute Attachment: Relation Extraction
* For example:
    * "롯데월드 어떻게 가나요?"
    * Domain: Navigation
    * Main Action: Search
    * Object.Location.Destination=롯데월드

### Reducing the Human Effort

* The goal is to reduce the labeling effort for spoken language understanding
    * Preparation of human-labeled utterances is labor-intensive and time-consuming
* Supervised learning
    * requires a large amount of labeled data
    * Given the data (x1, y1), ..., (xn, yn)
    * We find a function f: X → Y
    * f can be any classifiers (e.g. MaxEnt, SVM, Boosting, Decision tree, etc.)

### Reducing the Effort of Human Annotation

* Active learning
* Semi-supervised learning
* Combining two techniques
