# Regex Tutorial 

Regex is short for regular expression, a regex is a string of text that allows you to create patterns that help match, locate, and manage text. A regular expression is simply a pattern of characters that are used to validate character combinations. This tutorial will take a commonly used regex pattern used in programming and break it down to explain what it does and how.

## Summary

We will be walking through the following regex, explaining what each component does.

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

### Anchors

Anchors do not match any character at all. Instead, they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. The caret ^ defines the beginning of the string. The dollar sign $ defines the end of the string.

These are special sequences which match an empty substring:

    ^ matches at the beginning of the target string
    $ matches at the end of the target string
    \b matches on a word boundary, i.e., the previous or subsequent character is not a word character
### Quantifiers

Regular expressions use quantifiers to generate unbounded matching possibilities and other matching amount specifications. An atom can optionally be followed by one of these quantifiers:

    *   representing 0 or more occurrences of the atom,
    +   representing 1 or more occurrence of the atom,
    ?   representing 0 or 1 occurrences of the atom,
    the bound {n}   representing exactly n occurrences of the atom,
    the bound {m,n}   representing between m and n occurrences of the atom.

The quantifier can optionally be followed by "?" indicating that the match be minimal (non-greedy, reluctant) as opposed to the default maximal (greedy) match.
### Grouping Constructs

Capturing groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. For example, the regular expression (dog) creates a single group containing the letters "d" "o" and "g". The portion of the input string that matches the capturing group will be saved in memory for later recall via backreferences. 

Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. 

You can use grouping constructs to do the following:

    -Match a subexpression that is repeated in the input string.
    -Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.
    -Include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods.
    -Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.
### Bracket Expressions

A bracket expression represents a character set via a list of characters enclosed by the square brackets: '[' and ']'. It normally matches the target string with any single character from the list.

If the character list begins with '^', it matches any single character not from the rest of the list.

If two characters in the list are separated by '–', this is shorthand for the (inclusive) range of characters between those two. It is illegal for two ranges to share an endpoint, e.g. a-c-e. Ranges are collating-sequence dependent and should be avoided for portability.

Most special characters lose their special status and become literals within brackets. Additionally,

        – is literal at the end or beginning of a bracket expression
        ^ is literal if not at the beginning of a bracket expression

The backslash character, \, retains its meaning in bracket expressions, permitting the usage of the special escape sequences: such as \n, \t, \w, \d, etc.
### Character Classes
### The OR Operator
### Flags
### Character Escapes

These are special sequences representing commonly used character sets:

    \w is word (program identifier) character: [A-Za-z0-9_]
    \W is non-word character: [^A-Za-z0-9_]
    \s is a whitespace character: [ \f\n\r\t]
    \S is a non-whitespace character: [^ \f\n\r\t]
    \d is a digit character: [0-9]
    \D is a non-digit character: [^0-9]
## Author

Tammy Gagliano is an Alabama native. She is an aspiring Full Stack Developer with many years experience in all areas of life. When she's not sitting in front of the computer she enjoys spending time with family and friends, dancing, volleyball, and cooking! 

GitHub Repository
    https://github.com/TammyGagliano/regex-tutorial

