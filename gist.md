# Regex: Matching an Email

Javascript has a handful of ways to check a string to see if it contains a certain letter or phrase. Regular Expressions, or regex for short, are a series of special characters that define a search pattern. The following is one of the examples in which you can match an email.
'/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/'

## Summary

The email match regex code helps us search for an email with the pattern. Here's the breakdown of the code:
- The first part before the @ can contain lowercase, numbers 0-9, an underscore, a period or a hyphen
- The part after the @ but before the . can contain any lowercase letter along with a period, or a hyphen
- after the . it can contain any lowercase letter, and a period. It can only be within 2 and 6 characters long

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

A regex is considered a literal, so the pattern must be wrapped in slash characters (/).

### Anchors

The ^ and $ are anchors.
The ^ anchor signifies a string that begins with the characters that are after it. Here are some examples
    - ^The matches "The" or "The person", but does not match "the" and "the person because "the" in both strings has a lowercase t
The $ anchor signifies a string that ends with the characters that are after it. It can also be preceded by an exact string or a range of possible matches.

### Quantifiers

The pattern {2,6} preceded by the $ character is called a quantifier. Quantifiers set the limits of the strings that the regex matches. The first number (2) is the minimum number of characters. The second number (6) is the maximum number of characters. There are more ways to set quantifiers:
    - * matches the pattern zero or more times
    - + matches the pattern one or more times
    - ? matches the pattern zero or one time
    - {} provide three different ways to set limits for a match
        - { n } matches the pattern exactly n number of times
        - { n, } matches the pattern at least n number of times
        - { n, x } matches the pattern from a min of n to a max of x amount of times
Each one of those can be followed by a ? to make it match as few as possible. In the email match regex '/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/' there are a few quantifiers. (+), {2,6}, and $
    - + matches the first part of the email one or more times
    - {2,6} sets the minimum of 2 and a max of 6 characters for the middle part of the email.

### Grouping Constructs

Grouping constructs are ways to see if a string matches all requirements. An example would be (abc):(efg) the first part (abc) finds if it has the letters a,b,c if it does then it will go on to check the 2nd part to see if the string also has e,f,g in it. Since the expression has a (:) in between them, the string will have to have one. So the following would return true in that it matches:
    - abc:efg
    - aty:ehi
These would not return as a match:
    - abc efg
    - tyu:klo

### Bracket Expressions

Anything inside of the [] represents what the range of characters that we want to try and match. These are known as bracket expressions. For example, [iks] will look for a string that includes i, k, or s. So all of the following examples would match: "iiii", "kiss", "source", "kin". If you want to include multiple character in between 2 letters you can use a hyphen (-). So, [a-h] would bring up any string that includes a, b, c, d, e, f, g, and h. If you wanted to include capital letter you would write it like this: [A-Z] or [IKS.
You can include numbers as well by typing [0-9] this will include any number from 0 to 9
There are also ways to include special characters like hyphens or underscores. By using [_-] this will include everything that has an underscore or hyphen.
If we put all these together it'll look something like this: [a-z0-9_-] this will include anything with lowercase letters, numbers from 0 to 9 and special characters underscore and hyphen
The following would be a match for [a-z0-9_-]:
    - numbers
    - numb3rs
    - num_bers
    - num-b3rs
These would be a nonmatch:
    - NUMBERS
    - NUMBER$
    - NUM&BERS

### Character Classes

Character classes defines a set of characters, any one of which can occur in a string to fulfill a match.
    - . matches any character except the newline character (\n)
    - \d matches any arabic numeral digits. Its equivalent to the bracket expression [0-9]
    - \w matches any alphanumeric character from the basic Latin alphabet including the underscore. Its equivalent to [A_Za-z0-9_]
    - \s matches a single whitespace character, including tabs and line breaks

### The OR Operator

The OR Operator tells us that they don't have to meet all the letter requirements. Just like in the previous examples above, the string only has to meet one of whatever is in the (). Regex could also be written like this (a|b|c) the | is also read as 'or'. So that would read 'It contains a, b OR, c'.

### Flags

Flags are the one exception to the regex's must be wrapped in slash characters. They are placed at the end of a regex, after the second slash. They define additional functionality or limits for the regex.
    - g Global search: regex should be tested against all possible matches in a string
    - i Case-insensitive search: case should be ignored while attempting a match in a string
    - m Multi-line search: a multi-line input string should be treated as multiple lines

### Character Escapes

The backslash in a regex escapes a character that would otherwise be interpreted literally. If a { started the quantifier then it would read what is inside, but putting a \ before it tells the code to search the string for a {.

## Author

Jackson Smith

[Link](https://github.com/Tank2532)
