# Regex Academy: Hex How-to

Today let's look at a regular expression that is used to match hexidecimal code! 

A regular expression is like an equation, where a string of characters are used to create a pattern of search. These character can be either literal or meta.

Hexadecimal is a base-16 number system. There are 16 possible digits used to these numbers. The values in a hexidecimal are 0-9 and A-F. The reason for this is so that you can take large binary and decimal numbers and represent them with fewer digits.

## Summary

The regex for hexidecimal looks like this: 

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

If you're working in design of any kind you'll probably encounter hexidecimal codes for numbers that follow this regex. These codes will represent colors! The colors will usually come in 3 or 6 digit codes. This regex can account for both. Let's break it down into sections. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)


## Regex Components

### Anchors

Anchors are used in this regex for character positioning. 

There are 2 anchors here:

`^`

and:

`$`

This `^` anchor is used to represent the beginning of a string. 
`^BCD` would match a string beginning with BCD.

This `$` anchor represents the end of a string.
`DEF$` should match a string ending with DEF. 

Using both of these characters lets our expression define the beginning and end of our hex code.

### Quantifiers

The hexadecimal regex uses two types of quantifiers:

`?`

and:

`{n}`

This `?` quantifier matches a preceding character in our regex 0 or 1 times. 
In our regex:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

There's a `#` symbol before our `?` which tells us that our expression will match a string that begins with `#` or it won't.

This `{n}` quantifier, which appears as `{6}` and `{3}` in our regex, indicates that our expression will contain either 6 or 3 characters.

### OR Operator

There is only the `|` OR operator in our regex:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

It simply tells us that our regex will match either:

`[a-f0-9]{6}`

or:

`[a-f0-9]{3}`

You can use this OR operator multiple times:

`[x-z4-7]{9}|[j-l2-4]{14}|[b-f3-8]{5}`

This expression would look for `[x-z4-7]{9}`, `[j-l2-4]{14}`, or `[b-f3-8]{5}`

### Character Classes

The character class of our regex `[a-f0-9]` tells the expression the range of letters and numbers that are required for a hexadecimal match. In this instance our expression will look for the letters a through f and the and numbers 0-9. 

### Flags

Flags affect the search patterns of regular expressions. They can be thought of as advanced search options.

For instance, our anchors `^` and `$` would be affected by the `m` flag in our hex code:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/m`

The `m` flag would be used if we were searching multi-line code to match our hex code. With how short the length of hexadecimal codes are, the anchors `^` and `$` provide the parameters needed to execute our query in most instances.

### Grouping and Capturing

The portion of our regex that is encased in parentheses is used for grouping and capturing:

`([a-f0-9]{6}|[a-f0-9]{3})`

The parantheses group the limiting repetition quantifiers `[a-f0-9]{3}` and
`[a-f0-9{6}]` of our expression together, where they can be compared by our OR operator.

### Bracket Expressions

The bracket expression `[a-f0-9]` contains the character class of our regex in square brackets to indicate that it needs to match the hex code.

### Greedy and Lazy Match

The hexadecimal regex doesn't contain a greedy or lazy match. For example if we added another `?` to our regex, making it look like this:

`/^#??([a-f0-9]{6}|[a-f0-9]{3})$/`

the addition of `?` quantifier next to another one would force a lazy match but it wouldn't serve the purpose of our regex. We already use the `?` quantifier to handle a singular purpose and with the relatively low complexity of the hexadecimal regex it wouldn't need further match modes to work more efficiently if the user has the hexidecimal code on hand.

## Author

This Gist brought to you by Scott Schulman. A full-stack web developer in training through the University of Denver, Colorado. 

My GitHub profile: https://github.com/itlleat
