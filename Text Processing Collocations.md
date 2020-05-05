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

### Example

* Find me all instances of the word "the" in a text.
    * the -> Misses capitalized examples
    * [tT]he -> Incorrectly returns other or theology
        * False positives: Matching strings that we should not have matched
    * Solution: <b>[^a-zA-z][tT]he[^a-zA-Z]</b>
