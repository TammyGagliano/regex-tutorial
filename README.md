# Regex Tutorial 

Regex is short for regular expression, a regex is a string of text that allows you to create patterns that help match, locate, and manage text. A regular expression is simply a pattern of characters that are used to validate character combinations. This tutorial will take a commonly used regex pattern used in programming and break it down to explain what it does and how.

## Summary

I will be walking through the following regex, explaining what each component does. I will be covering and breaking down the components of a regular expression used to match Hex Values. Hex values are commonly used for color using the hexadecimal color code format. In the web we can use hex triplet (hex color code) to represent colors on a web page. For the hex color code, there are two formats, a standard hex triplet and a shorthand hex format, where both formats start with a #.

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

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

With a “character class”, also called “character set”, you can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use [ae]. You could use this in gr[ae]y to match either gray or grey. Very useful if you do not know whether the document you are searching through is written in American or British English.

A character class matches only a single character. gr[ae]y does not match graay, graey or any such thing. The order of the characters inside a character class does not matter. The results are identical.

You can use a hyphen inside a character class to specify a range of characters. [0-9] matches a single digit between 0 and 9. You can use more than one range. [0-9a-fA-F] matches a single hexadecimal digit, case insensitively. You can combine ranges and single characters. [0-9a-fxA-FX] matches a hexadecimal digit or the letter X. Again, the order of the characters and the ranges does not matter.

Character classes are one of the most commonly used features of regular expressions. You can find a word, even if it is misspelled, such as sep[ae]r[ae]te or li[cs]en[cs]e. You can find an identifier in a programming language with [A-Za-z_][A-Za-z_0-9]*. You can find a C-style hexadecimal number with 0[xX][A-Fa-f0-9]+.
### The OR Operator

Alternation is the term in regular expression that is actually a simple “OR”. In a regular expression it is denoted with a vertical line character |. For instance, we need to find programming languages: HTML, PHP, Java or JavaScript.
The corresponding regexp: html|php|java(script)?.

A usage example:

    let regexp = /html|php|css|java(script)?/gi;
    let str = "First HTML appeared, then CSS, then JavaScript";
    alert( str.match(regexp) ); // 'HTML', 'CSS', 'JavaScript'

We already saw a similar thing – square brackets. They allow to choose between multiple characters, for instance gr[ae]y matches gray or grey. Square brackets allow only characters or character classes. Alternation allows any expressions. A regexp A|B|C means one of expressions A, B or C.

For instance:

    gr(a|e)y means exactly the same as gr[ae]y.
    gra|ey means gra or ey.

To apply alternation to a chosen part of the pattern, we can enclose it in parentheses:

    I love HTML|CSS matches I love HTML or CSS.
    I love (HTML|CSS) matches I love HTML or I love CSS.
### Flags

Regular expressions have optional flags that allow for functionality like global searching and case-insensitive searching. These flags can be used separately or together in any order, and are included as part of the regular expression.

To include a flag with the regular expression, use this syntax:

var re = /pattern/flags;
or
var re = new RegExp('pattern', 'flags');

Note that the flags are an integral part of a regular expression. They cannot be added or removed later.

For example, re = /\w+\s/g creates a regular expression that looks for one or more characters followed by a space, and it looks for this combination throughout the string.

    var re = /\w+\s/g;
    var str = 'fee fi fo fum';
    var myArray = str.match(re);
    console.log(myArray);

You could replace the line:

    var re = /\w+\s/g;
    with:
    var re = new RegExp('\\w+\\s', 'g');
    and get the same result.

The m flag is used to specify that a multiline input string should be treated as multiple lines. If the m flag is used, ^ and $ match at the start or end of any line within the input string instead of the start or end of the entire string.
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

