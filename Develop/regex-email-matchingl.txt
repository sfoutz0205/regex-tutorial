# Regex Tutorial - Matching an Email

A regular expression (shortened as regex or regexp; also referred to as rational expression) is a specially encoded sequence
of characters that define a search pattern, mainly for use in pattern matching with strings, or string matching. Regular
expressions are used in search engines, search and replace dialogs of word processors, to name a few, and many programming
languages provide regex capabilities either built-in or via libraries.

## Summary

In this tutorial, we will take a closer look at the following regular expression. It can be used to verify whether a given input string
is a valid email id:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Each component of this regex has a unique responsibility to make sure that a user enters an email address that begins with an
unspecified number of characters preceding the @ symbol, followed by a domain.

## Table of Contents

- [Anchors](#anchors)
- [Grouping and Capturing](#grouping-and-capturing)
- [Character Classes](#character-classes)
- [Quantifiers](#quantifiers)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

Anchors don't actually match specific characters, but rather, they are used to match a particular position within the string,
such as the beginning or end of a line of text or word. As seen in the regex above, the carat (^) is used to match the
beginning of the string, and the dollar sign ($) matches the end. 

** Note the regex actually begins and ends with a forward slash. This is what we call a delimiter, and serve simply as a
boundary for our regular expression. The forward slash is the most commonly used delimiter, however, depending on the syntax
your programming language uses, you may also see the following symbols used for this purpose: #,%,+,~.

Examples of the (^) & ($) anchors would be:

^Cats matches any string that begins with the word 'Cats'

fluffy$ would match any string that ends with the word 'fluffy'

### Grouping and Capturing

Next we see a portion of the regular expression excased in parentheses. All matches found in a regular expressions are
assigned to groups and stored in memory to be referenced later on. Any subpattern inside a pair of parentheses will be
extracted and captured as a separate group. 

In this example, we see three different capturing groups, each containing a character set and a quantifier.

([a-z0-9_\.-]+), ([\da-z\.-]+), and ([a-z\.]{2,6})

Now lets take a closer look inside these capturing groups...

### Character Classes

Character classes, or character sets, are one of the most commonly used features of regular expressions and are contained
within square brackets. Within the square brackets of a character class can be many different search rules. In this case,
these include a mixture of ranges and single characters. 

1. [a-z0-9_\.-]

The first character class we see includes two ranges 'a-z' and '0-9' followed by three single characters '_', '.', and '-'.
This means it will match any email address with a username containing any letter, any digit, and any of these three
characters. 

** The '\' character before the '.' because on it's own the '.' is a special character with special meaning. This meaning
needs to be 'escaped' using the '\' to instruct a match to the literal character '.'

2. [\da-z\.-]

The second character class, used to match the mail server name, includes '/d' which is another way to match any digit 0-9 but
also includes other unicode digits, followed by the familiar range a-z, the literal '.', and the '-' characters. 

3. [a-z\.]

The final character class, used to match the domain name, includes another a-z range and the literal '.' character.

### Quantifiers

Quantifiers are used to specify how often the proceeding character, group, or character class must be present. Here we see two
different examples of quantifiers:

+ - match the proceeding token 1 or more times.
{m,n} — match the proceeding token from n to m times.

The '+' quantifier appears within the first two capture groups, directly after the character sets, instrucing the regex to
match of 1 or more of each of the different rules outlined within the proceeding character class. 

The third capture group includes the other example of a quantifier '{2,6}', instructing the regex to match between 2 and 6 of
each token within the proceeding character class. This is because any valid domain name (.com, .org, etc) are between 2 and 6
characters long. 

### Greedy and Lazy Match

Quantifiers, by default, are 'greedy'. This means that they match as many instances of a token character set as possible, or
the longest match that can be found with a match attempt that starts at a given position in the string. Alternatively, when a
'?' is appended to the quantifier, it is made 'lazy', meaning it will match as few instances of the token or character set as
needed. This is In this case, we see the greedy approach used. 


## Author

This tutorial was created Sophie Foutz as an assignment on learning to understand regular expression. I am currently a student
of the coding bootcamp through the University of Utah, and will be finishing the program in January 2021. Visit my github page
to view additional projects. 

https://github.com/sfoutz0205