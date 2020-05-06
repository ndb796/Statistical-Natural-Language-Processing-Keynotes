### Text Classification

* Spam detection
* Sentiment analysis
* Age/gender identification
* Assigning subject categories, topics, or genres

### Text Classification: Definition

* Input
    * A document d
    * A fixed set of classes C = {c1, c2, ..., ci}
    * A training set of m hand-labeled documents (d1, c1), ..., (dm, cm)
* Output
    * A learned classifier y: d → c

### Classification Methods: Supervised Machine Learning

* Naive Bayes
* Logistic Regression
* Support-Vector Machines
* K-Nearest Neighbors

### Naive Bayes Intuition

* Simple "naive" classification method based on Bayes rule.
* Relies on very simple representation of document
    * Bag of words
* 하나의 문장에서 각 단어의 빈도수를 구하여 벡터로 만든 뒤에, 이를 입력으로 받아 분류 결과를 출력

### Naive Bayes Classifier

* 하나의 문서(d)가 들어왔을 때, 확률이 가장 높은 클래스(c)를 찾아야 함
* Bayes rule에 따라서 P(d|c)P(c)가 가장 높은 클래스를 찾으면 됨
* 유도: <b>C = argmax P(c|d) = argmax P(d|c)P(c)/P(d) = argmax P(d|c)P(c) = argmax P(x1, x2, ..., xn|c)P(c)</b>

### Multinomial Naive Bayes Independence Assumptions

* Bag of Words (BoW) assumption: Assume position doesn't matter
* Conditional Independence: Assume the feature probabilities P(xi|c) independent given the class c.
    * P(x1, x2, ..., xn|c) = P(x1|c) * P(x2|c) * P(x3|c) * ... * P(xn|c)
* Then, <b>C = argmax P(x1, x2, ..., xn|c)P(c) = argmax P(c)∏P(x|c)</b>
* 이는 "해당 클래스의 확률 * 해당 클래스에서 각 단어가 나올 확률을 모두 곱한 것"을 의미
* 하지만, 해당 클래스에서 특정한 단어가 나올 확률이 0이라면? 확률 자체가 0이 되어버림

### Naive Bayes Example 1

||Positive|Negative|
|------|------|------|
|I|0.1|0.2|
|love|0.1|0.001|
|this|0.01|0.01|
|fun|0.05|0.005|
|film|0.1|0.1|

* Sentence = "I love this fun film"
* P(Sentence|Positive) = 0.1 * 0.1 * 0.01 * 0.05 * 0.1
* P(Sentence|Negative) = 0.2 * 0.001 * 0.01 * 0.005 * 0.1
* So, <b>P(Sentence|Positive) > P(Sentence|Negative)</b>

### Laplace Smoothing

* <b>P(w|c) = (count(w, c) + 1) / (count(c) + V)</b>

### Naive Bayes Example 2

||Documents|Words|class|
|------|------|------|------|
|Train|1|Chinese Beijing Chinese|c|
|Train|2|Chinese Chinese Shanghai|c|
|Train|3|Chinese Macao|c|
|Train|4|Tokyo Japan Chinese|j|
|Test|5|Chienese Chinese Chinese Tokyo Japan|?|

* Priors
    * P(c) = 3/4, P(j) = 1/4
* Conditional Probabilities
    * P(Chinese|c) = (5 + 1) / (8 + 6) = 3/7
    * P(Tokyo|c) = (0 + 1) / (8 + 6) = 1/14
    * P(Japan|c) = (0 + 1) / (8 + 6) = 1/14
    * P(Chinese|j) = (1 + 1) / (3 + 6) = 2/9
    * P(Tokyo|j) = (1 + 1) / (3 + 6) = 2/9
    * P(Japan|j) = (1 + 1) / (3 + 6) = 2/9
* Choosing a class
    * P(c|Document 5) = 3/4 * 3/7 * 3/7 * 3/7 * 1/14 * 1/14
    * P(j|Document 5) = 1/4 * 2/9 * 2/9 * 2/9 * 2/9 * 2/9
    * So, the class is Chinese!
