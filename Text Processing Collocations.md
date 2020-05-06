### Regular Expressions

* A formal language for specifying text strings
* How can we search for any of these?
    * woodchuck
    * woodchucks
    * Woodchuck
    * Woodchucks

### Regular Expressions: Disjunctions

* Letters inside square brackets []

|Pattern|Matches|
|------|------|
|[wW]|Woodchuck, woodchuck|
|[123456789]|Any digit|

* Ranges

|Pattern|Matches||
|------|------|------|
|[A-Z]|An upper case letter|<b>D</b>renched Blossoms|
|[a-z]|A lower case letter|<b>m</b>y beans were impatient|
|[0-9]|A single digit|Chapter <b>1</b>: Down the Rabbit Hole|

### Regular Expressions: Negation in Disjunction

* Negations
    * Caret means negation only when first in []

|Pattern|Matches||
|------|------|------|
|[^A-Z]|Not an upper case letter|O<b>y</b>fn pripetchik|
|[^Ss]|Neither 'S' nor 's'|<b>I</b> have no exquisite reason|
|[^e^]|Neither e nor ^|Look he<b>r</b>e|
|a^b|The pattern a caret b|Look up <b>a^b</b> now|

### Regular Expressions: More Disjunctions

* Woodchucks is another name for groundhog!
* The pipe | for disjunction

|Pattern|Matches|
|------|------|
|groundhog\|woodchuck||
|yours\|mine|yours mine|
|a\|b\|c|= [abc]|
|[gG]roundhog\|[Ww]oodchuck||

### Regular Expressions: ? \* + .

|Pattern|Matches||
|------|------|------|
|colou?r|Optional previous char|<b>color colour</b>|
|oo\*h!|0 or more of previous char|<b>oh! ooh! oooh! ooooh!</b>|
|o+h!|1 or more of previous char|<b>oh! ooh! oooh! ooooh!</b>|
|baa+||<b>baa baaa baaaa baaaaa</b>|
|beg.n||<b>begin begun beg3n</b>|

### Regular Expressions: Anchors ^ $

|Pattern|Matches|
|------|------|
|^[A-Z]|<b>P</b>alo Alto|
|^[^A-Za-z]|<b>1</b> <b>\"</b>Hello\"|
|\\.$|The end<b>.</b>|
|.$|The end<b>?</b> The end<b>!</b>|

### Regular Expressions Example

* Find me all instances of the word "the" in a text.
    * the -> Misses capitalized examples
    * [tT]he -> Incorrectly returns other or theology
        * False positives: Matching strings that we should not have matched
    * Solution: <b>[^a-zA-z][tT]he[^a-zA-Z]</b>

### Regular Expressions Summary

* Regular Expressions play a surprisingly large role
    * Sophisticated sequences of regular expressions are often the first model for any text processing
* For many hard tasks, we use machine learning classifiers
    * But regular expressions are used as features in the classifiers
    * Can be very useful in capturing generalizations

### Tokenization (토큰화) & Normalization (정규화)

* 텍스트 토큰화: 코퍼스(Corpus)를 토큰(Token)이라 불리는 단위로 나누기
* "They lay back on the San Francisco grass and looked at the stars and their"
    * Type: an element of the vocabulary -> 13 Types
    * Token: an instance of that type in running text -> 15 Tokens
    * 다양한 데이터베이스를 확인해 보면, Tokens의 수가 Types에 비해서 훨씬 많음
* 텍스트 정규화: 표현 방법이 다른 단어들을 통합하여 같은 단어로 처리
* Every NLP task needs to do text normalization
    * Segmenting/tokenizing words in running text
    * Normalizing word formats
    * Segmenting sentences in running text

### Issues in Tokenization

* Finland's capital -> Finland Finlands Finland's?
* San Francisco -> One token or two?

### Maximum Matching Word Segmentation Algorithm

* 중국어처럼 단어 사이에 공백이 없는 경우가 있음
    * Average word is 2.4 characters long
* Maximum Matching: <b>Greedy approach</b>
    * 가장 긴 단어에 우선순위를 두어서 매칭하는 간단한 방법
    * Given a wordlist of Chinese, and a string
        1. Start a pointer at the beginning of the string
        2. Find the longest word in dictionary that matches the string starting at pointer
        3. Move the pointer over the word in string
        4. Go to 2
* Max-match segmentation illustration
    * Thecatinthehat -> The cat in the hat (work)
    * Thetabledownthere -> Theta bled own there (Not work)
    * Doesn't generally work in English
    * <b>But works astonishingly well in Chinese</b>

### Normalization (정규화)

* Need to "normalize" terms
    * Information Retrieval (IR): indexed text & query terms must have same form
        * We want to match U.S.A. and USA
* We implicitly define equivalence classes of terms
    * e.g., deleting periods in a term
* Alternative
    * Enter: window, Search: window, windows
    * Enter: windows, Search: Windows, windows, window
    * Enter: Windows, Search: Windows

### Lemmatization (표제어 추출)

* Reduce inflections or variant forms to base form
* Lemmatization: have to find correct dictionary headword form (표제어 형식)
* 표제어 (Lemma): 기본 사전형 단어
    * 예를 들어 am, are, is의 스펠링은 서로 다르지만, 표제어를 be라고 볼 수 있음
    * car, cars, car's, cars' -> car
* Machine translation

### Morphology (형태학)

* 형태학: 형태소로부터 단어들을 만들어가는 학문 분야
* 형태소 (Morphemes): The small meaningful units that make up words
    * <b>어간 (Stems): The core meaning-bearing units</b>
    * <b>접사 (Affixes): Bits and pieces that adhere to stems</b>
        * Often with grammatical functions

### Stemming (어간 추출)

* 어간을 추출하는 작업: 정해진 규칙에 따라서 단어의 어미를 자름
* Reduce terms to their stems in information retrieval
* Stemming is crude chopping of affixes
    * language dependent
    * e.g., automate(s), automatic, automation all reduced to <b>automat</b>
* Porter's algorithm: The most common English stemmer

### Minimum Edit Distance

* The minimum number of editing operations
    * Insertion
    * Deletion
    * Substitution
* For string X → string Y
* Pseudocode
<pre>
D[0][0] = 0
For each i = 1..N
    D[i][0] = D[i-1][0] + deletion(X[i])
For each j = 1..M
    D[0][j] = D[0][j-1] + insertion(Y[j])

For each i = 1..N
    For each j = 1..M
        if X[i] == Y[j]
            D[i][j] = D[i-1][j-1]
        else
            D[i][j] = min(D[i-1][j] + deletion(X[i]), D[i][j-1] + insertion(Y[j]), D[i-1][j-1] + substitution(X[i], Y[j]))

Then, D[N][M] is the minimum edit distance.
</pre>
* Python 3.7 Code
<pre>
''' Weighted Minimum Edit Distance '''
# Find the "Minimum Edit Distance" from X to Y.
X = "EXECUTION"
Y = "INTENTION"

n = len(X)
m = len(Y)

D = [[0] * (m + 1) for _ in range(n + 1)]

# Define Distance Functions
def deletion(a):
    return 1
def insertion(a):
    return 1
def substitution(a, b):
    return 1 # return 2 in Levenshtein algorithm. 

# Initialization
D[0][0] = 0
for i in range(1, n + 1):
    D[i][0] = D[i - 1][0] + deletion(X[i - 1])
for j in range(1, m + 1):
    D[0][j] = D[0][j - 1] + insertion(Y[j - 1])

# Recurrence Relation
for i in range(1, n + 1):
    for j in range(1, m + 1):
        if X[i - 1] == Y[j - 1]:
            D[i][j] = D[i - 1][j - 1]
        else:
            D[i][j] = min(D[i - 1][j] + deletion(X[i - 1]), D[i][j - 1] + insertion(Y[j - 1]), D[i - 1][j - 1] + substitution(X[i - 1], Y[j - 1]))

# Termination (D[N][M] is the minimum edit distance.)
print(D[n][m])
</pre>
