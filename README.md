# Regex-Tutorial
# Regular Expressions (Regex) Tutorial

This Regular Expression tutorial, also know as Regex, explains and defines the sequence of special characters to verify a search pattern. A Regular Expression is a sequence of characters that specifies a match pattern in text. Regex can be used to find patterns of characters in a string, replace that character or sequence and validate input data.
## Summary

Today I will be covering and breaking down the components of a regular expression used to match Hex Values. Hex values are commonly used for color using the hexadecimal color code format. In the web we can use hex triplet (hex color code) to represent colors on a web page. For the hex color code, there are two formats, a standard hex triplet and a shorthand hex format, where both formats start with a #.

## Table of Contents

- [Regex-Tutorial](#regex-tutorial)
- [Regular Expressions (Regex) Tutorial](#regular-expressions-regex-tutorial)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
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
  - [Author](#author)

## Regex Components

### Anchors
Anchors are used to check if the matching symbol is the starting symbol or ending symbol of the input string.There are 2 types of anchors, the caret ^ and  the dollar sign $.The caret ^ checks if the matching character is the first character of the input.
/^abc/.test('abc123'); // returns true
/^abc/.test('123abc'); // returns false
The top line of code returns true because the matching characters are the first characters of the input. The bottom line of code returns false because the matching characters are not the first characters of the input.

The dollar sign $ checks if a matching character is the last character of the input string.
/abc$/.test('123abc'); // returns true
/abc$/.test('abc123'); // returns false
The top line of code returns true because the matching characters are the last characters of the input. The bottom line of code returns false because the matching characters are not the last characters of the input.
### Quantifiers
Quantifiers are symbols used in regular expressions to specify how many times a character or a group of characters can repeat. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found and match as many characters as possible. The i characters include the asterisk * (0 or more times), plus sign + (1 or more times), question mark ? (0 or 1 time), and braces {} which indicate a specific number of repetitions.
Example:
/a*/.test('');    // Returns true
/a*/.test('a');   // Returns true
/a*/.test('aaa'); // Returns true

/a+/.test('');    // Returns false
/a+/.test('a');   // Returns true
/a+/.test('aaa'); // Returns true

/a?/.test('');   // Returns true
/a?/.test('a');  // Returns true
/a?/.test('aa'); // Returns false (only the first 'a' is matched)

/a{2}/.test('a');   // Returns false
/a{2}/.test('aa');  // Returns true
/a{2}/.test('aaa'); // Returns true (only the first 'aa' is matched)

### OR Operator
The "or" operator uses the pipe symbol "|" element. The pipe symbol "|" is used to match any one element separated by the pipe symbol. 
Example:
let regex = /cat|dog/;
console.log(regex.test("I have a cat.")); // true
console.log(regex.test("I have a dog.")); // true
console.log(regex.test("I have a bird.")); // false

In our example we have 2 elements separated by the pipe symbol. The first element is [cat] and the second element is [dog]. This means that our regular expression will match any element that is either [cat] or [dog].
### Character Classes
Character classes are components used to specify type of characters to be expected.
Examples:
1. Dot (.): Matches any character except newline (\n).
2. Digits (\d): Matches any digit from 0-9.
3. Non-digits (\D): Matches any character that is not a digit.
4. Word characters (\w): Matches any alphanumeric character (a-z, A-Z, 0-9) and underscore (_).
5. Non-word characters (\W): Matches any character that is not a word character.
6. Whitespace (\s): Matches any whitespace character.
### Flags
Flags are parameters that we can add to a plain expression to control a search. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behavior.
Some examples of flags are:
1. g: global match; find all matches rather than stopping after the first match.
2. i: case-insensitive match; ignore case when matching characters.
3. m: multiline match; treat beginning and end characters (^ and $) as working over multiple lines (i.e., match the beginning or end of each line (delimited by \n or \r), not only the very beginning or end of the whole input string).
### Grouping and Capturing
Grouping is used to group subexpressions together by placing them inside parenthesis. Grouping is used to apply quantifiers to a group of characters. Capturing is used to capture the result of a group, not just match it.The captured group can be reused with a numbered backreference.
### Bracket Expressions
Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
Example:
let regex = /[abc]/;
console.log(regex.test("apple"));   // Outputs: true
console.log(regex.test("banana"));  // Outputs: true
console.log(regex.test("cherry"));  // Outputs: true
console.log(regex.test("date"));    // Outputs: false

regex = /[0-9]/;
console.log(regex.test("123abc"));  // Outputs: true
console.log(regex.test("abc"));     // Outputs: false

regex = /[^abc]/;
console.log(regex.test("abcd"));    // Outputs: true
console.log(regex.test("abc"));     // Outputs: false


### Greedy and Lazy Match
 By default, regex is greedy.A greedy match tries to match a pattern as many times as possible. Whereas, a lazy match tries to match as few times as possible. *, +, ?, and {n,} are all greedy by default. To make them lazy, add a ? after the quantifier.

### Boundaries
Boundaries are used to check if the matching character is the starting character or ending character of the input string. There are 2 types of boundaries, the caret ^ and the dollar sign $. The caret ^ checks if the matching character is the first character of the input. The dollar sign $ checks if a matching character is the last character of the input string.

### Back-references
Back-references are used to match the same text as previously matched by a capturing group. They are denoted by a backslash followed by a digit corresponding to the number of the group it refers to. \1 matches the same text as the first capturing group. \2 matches the same text as the second capturing group, and so on. \0 matches the text matched by the whole regular expression.

### Look-ahead and Look-behind
Also know as lookarounds, look-ahead and look-behind are used to match a pattern only if it is followed or preceded by another pattern. Lookarounds are zero-length assertions, meaning they match a position without consuming any of the input string. Lookarounds can be either positive or negative. Positive lookarounds are denoted by (?=) and (?!). Negative lookarounds are denoted by (?<=) and (?<!).
Example:
R(?=t)       matches a r only if is followed by t, but t will not be part of the match
(?<=t)r      matches a r only if is preceded by an t, but t will not be part of the match
## Author
Alvaro Vazquez is a student currently working on his coding bootcamp though the University of California Irvine. He is currently working on his coding skills and hopes to become a full stack developer in the near future.

