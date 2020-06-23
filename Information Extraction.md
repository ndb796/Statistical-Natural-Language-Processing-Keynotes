### Information Extraction (IE) systems

* Find and understand limited relevant parts of texts
* Gather information from many pieces of text
* Produce a structured representation of relevant information:
    * relations (in the database sense)
    * a knowledge base
* Goals:
    1) Organize information so that it is useful to people
    2) Put information in a semantically precise form that allows further inferences to be made by computer algorithms

### Named Entity Recognition (NER)

* A very important sub-task: find and classify names in text
* The uses:
    * Named entities can be indexed, linked off, etc.
    * Sentiment can be attributed to companies or products.
    * For question answering, answers are often named entities.
* Concretely:
    * Many web pages tag various entities, with links to bio or topic pages, etc.

### The Named Entity Recognition Task

* Task: Predict entities in a text
    * Foreign: ORG
    * Ministry: ORG
    * Shen: PER
    * Guofang: PER
    * spokesman: O

### Relation Extraction

* Extracting relations from text
* Company report: "International Business Machines Corporation (IBM or the company) was incorporated in ..."
    * Company: IBM
    * Location: New York
    * Date: June 16, 1911
* 관계추출(Relation Extraction)은 비구조적인 자연어 문장으로부터 구조적인 트리플(triple)를 추출하는 작업
* 트리플이란 두 개체 간의 관계(relation)를 <주어, 관계, 목적어>와 같이 세 개의 항으로 표현하는 구조
