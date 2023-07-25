# Matching an email regex tutorial

In this tutorial I will be explaining a regex (regular expression) on matching an email. email addresses are used to sign up for most accounts on the internet and as such are essential. Understanding how to match and email is a valuable skill for any programmer and I will discuss the regex exploring the syntax, metacharacters, and various texhniques to construct patterns for validating email addresses effectively.

## Summary

A regex is a sequence of characters that defines a search pattern. In this specific tutorial we will be covering the regex for matching and email EX: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
There are multiple components of regular expressions.
    * The ^ and $ anchors symbolize the start and end of the regex ensuring that the pattern matches the entire email and doesnt allow extra characters before and after.
    * The ([a-z0-9_\.-]+) part of the regex matches the local part of the email address.
    * The @ sign is a literal character that must be present in the email address.
    * ([\da-z\.-]+) This part of the regex matches the domain name of the email address.
    * The \. is a literal character that seperates the domain name from the top-level-domain.
    * ([a-z\.]{2,6}) is the third capturing group that matches the top-level-domain.
### Anchors
The anchors of this regex are the first thing we covered in the components section.

The ^ represents the start of the string and ensures that the pattern must match at the beginning of the text. If used outside of a character class it asserts that the entire pattern must start at the beginning of the line or string.

The $ represents the end of the string and ensures that the pattern that precedes must match at the end of the text. If used outside of the character class it asserts that the entire pattern must end at the end of the line or string.
### Quantifiers
Quantifiers allow for the creation of flexible patterns that can handle varying lengths of text. Using quantifiers you can easily match repetitive sequences or specific patterns that appear a certain amount of times in the input text.

The * matches zero or more occurences of the preceding character or group. This means the character or group can appear any number of times or not at all.

The + matches one or more occurences of the preceding character or group meaning the character or group must appear at least once.

The ? matches zero or one occurence of the preceding character or group meaning the character or group can appear at most once.

{n} matches exactly 'n' occurences of the preceding character or group.

{n,} matches 'n' or more occurences of the preceding character or group.

and finally {n,m} matches between 'n' and 'm' occurences of the preceding group or character.
### OR Operator
In regex the OR operator is represented by the | character allowing you to define multiple alternatives within a single pattern.
This part is easier to explain with examples.
    for example the regex red|blue will match either red or blue in the input text.
### Character Classes
Character classes allow you to define a set of characters from which the pattern should match any one character. They are enclosed in [].

[rgb] for example matches any single character that is either r g or b. For example if the input text was grape the the regex would match the letter 'g'.

[a-z] matches any single lowercase alphabetic character from a to z. For example if the input text was 432abc the regex would match 'a' because it is the first lowercase letter encountered.

[0-9] matches any single digit from 0 to 9. For example if the input text is 794blue the regex would match '7' because it is the first digit encountered.

[^rgb] because of the ^ this class represents a negated class meaning it will match any single character that is not r g or b. For example given the input is redsalad the regex would match e because it is the first character that is not r g or b.

[\d] is shorthand for [0-9].

[\w] is shorthand for matching any word character equivalent to [a-zA-Z0-9_].

[\s] is shorthand for matching any whitespace character meaning spaces, tabs, newlines, etc.

[a-zA-Z0-9] matches any single alphanumeric character.

[aeiou] matches any single lowercase vowel.

[A-Za-z] matches any single uppercase or lowercase letter.

[-] when the hyphen is placed between characters it is treated as a literal character and not as a range specifier.
### Flags
Flags are parameters that modify how the regex pattern behaves during matching.
 
(i) is the flag for case-insensitive meaning it allows for the regex pattern to match characters regardless of their case.

The (g) flag allows the regex pattern to match all occurences of the pattern in the input text not just the first one.

The (m) flag is the multiline flag meaning it changes the behaviour of the ^ and $ anchors so when the flag is in effect ^ matches the start of each line and the $ matches the end of each line.

The (s) flag is the dot-all flag allowing the . metacharacter to match any character.

(u) is the unicode flag enabling full unicode support for the regex.

The sticky flag (y) restricts the mathcing process to the index specified by the 'lastIndex' property of the regex object.
### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match
Greedy Match is the default for quantifiers meaning they try to match as much of the input text as possible while still allowing the overall pattern to match. Greedy Quantifiers are represented by *, +, and ? and as such will match as many occurences as possible before considering the match complete.

Lazy Matches will match the minimum number of occurences possible. To create a lazy match append a ? to the greedy quantifier making it match as little text as possible while still allowing the overall pattern to match.
### Boundaries
Boundaries are specific positions in the text that are not actual characters but represent specific locations relative to the characters in the text. Useful for defining where certain patterns should and should not occur. In this specific instance for matching an email regex boundaries ensure that the pattern only matches emails that appear as standalone entities not as part of larger words or strings.

The word boundary \b matches the position between a word character and a non word character allowing you to specify that the pattern should occur at the beginning or end of a word.

The start '^' and end '$' string anchors are also boundaries. we know the ^ represents the start of the string and the $ represents the end and when used in regex they ensure the pattern matches the entire input text from start to finish.

Combining these ensures that the email is accurately matched as a standalone entity which is important for avoiding matching partial email addresses embedded within larger strings.
### Back-references
Back references allow you to refer back to capturing groups within the regex pattern. They are used to match the same text that was previously matched by a capturing group. They are denoted by a \ followed by a digit where the digit represents the order of the capturing group in the regex.

First we need a capturing group. To create one you enclose a part of the regex in parentheses (). When the regex matches the text the content captured is stored in memory.
After a capturing group has been created you can reference the captured content using a back-reference. For example given the regex /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ the back-reference \1 would refer to the content captured by the first capturing group which would be ([a-z0-9_\.-]+) a back-reference of \2 would refer to the content captured by the second capturing group ([\da-z\.-]+).
### Look-ahead and Look-behind

## Author
Hello I am the author of the gist my name is John. I hope you found this helpful and if there is anything I missed or you think I should add please let me know.
