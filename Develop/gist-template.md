# Match an Email with Regex

This document will explain how to identify an email in various applications by using the expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/.
This expression will be helpful to users who want to validate emails using various technologies such as SQL, NoSQL, MongoDB, etc.


## Summary

This tutorial will explain each component of the email matching regex and how it works.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

The ^ used at the beginning of the expression indicates the beginning of the expression and the $ at the end symbolizes its end.
There are no flags in this expression which means the entry will be case sensitive and will not accept a multi-line submission.  

### Quantifiers

The + character is the first quantifier used in this expression and is used at the end of the first and second capture groups. Its purpose is to connect the first capture group to the second group and the second capture group to the third.  The other quantifier is the {2,6} expression which will allow for a range of 2-6 characters in the third capture group.

### Character Classes

The only class in this expression is \d and comes in the second capture group. It represents any single character that is a digit.

### Grouping and Capturing

The first capture group is ([a-z0-9_\.-]+). It will match the name part of an email address. Individual components are broken out as follows:

- a-z matches a single alphabetical character
- 0-9 matches a single numerical character
- _ matches the underscore character
- \. matches the period character
- "-" matches the hyphen character
- the @ component placed outside the () falls in the first capture group and checks for the @ character

The second capture group is ([\da-z\.-]+). It will match the email service provider part of an email address. Individual components are broken out as follows:

- \d matches a single numerical character (equivalent to 0-9 above)
- a-z matches a single alphabetical character (same as above)
- \. matches the period character (same as above)
- "-" matches the hyphen character (same as above)
- the \. component placed outside the () falls in the second capture group and checks for the period character

The third capture group is ([a-z\.]{2,6}). It will capture the ".com" part of an email address. The individual components are broken out as follows:

- a-z again matches a single alphabetical character
- \. again matches the period character
- {2,6} uses the greedy match quantifier {} to allow for this capture group to only be 2-6 characters long.

### Bracket Expressions

This regex contains one bracket expression in each capture group and allow for any combination of the characters contained within them. For instance, capture group 1 taken as a whole will match any combination of letters, numbers, underscores, hyphens and periods in any order. Letters will be case sensitive.

### Greedy and Lazy Match

The + symbol is a greedy quantifier as it allows for as unlimited characters that satisfy the expression inside the brackets for capture groups 1 and 2.
The {} expression is also greedy when matching {2,6}.  

## Author

Check out my other projects at https://github.com/mlow1992