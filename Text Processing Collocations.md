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
