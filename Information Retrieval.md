### Information Retrieval

* Information Retrieval (IR) is finding material of an unstructured nature (usually text) that satisfies an information need from within large collections (usually stored on computers).
* For example:
    * E-mail search
    * Searching your laptop
    * Web search
    * Legal information retrieval
* Goal: Retrieve documents with information that is relevant to the user's information need.

### How good are the retrieved docs?

* 정확도(Precision): Fraction of retrieved docs that are relevant to the user's information need.
* 재현율(Recall): Fraction of relevant docs in the collection that are retrieved.

### Inverted index

* For each term t, we must store a list of all documents that contain t.
    * Identify each doc by a docID, a document serial number
    * Hello → [1, 2, 4, 11, 31, 45, 173, 174]
* Can we used fixed-size arrays for this?

### Problem with the Boolean search: feast or famine

* Boolean queries often result in either too few (≈0) or too many (1000s) results.
* It takes a lot of skill to come up with a query that produces a manageable number of hits.
    * AND gives too few; OR gives to many

### Measures for a search engine

* How fast does it index
    * Number of documents/hour
    * (Average document size)
* How fast does it search
    * Latency as a function of index size
* Expressiveness of query language
    * Ability to express complex information needs

### Text Summarization

* Goal: Produce an abridged version of a text that contains information that is important or relevant to a user
* Summarization Applications
    * Outlines or abstracts of any document, article, etc.
    * Summaries of email threads
    * Action items from a meeting
    * Simplifying text by compressing sentences
