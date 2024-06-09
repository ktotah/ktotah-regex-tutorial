# Regex Tutorial: Understanding the Components of a Hex Value Matcher

Regular expressions, or regex, are powerful tools used in programming for pattern matching and text manipulation. In this tutorial, we will break down a regex that **matches hexadecimal color values**, explaining each component in detail to help you understand how it works.


## Summary

This tutorial will explore the components of a regular expression used to **match hexadecimal color values**. The regex we will be examining is:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

This regex checks for hex color values, allowing for both the shorthand (3 characters) and full (6 characters) notations, with an optional `#` at the beginning.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes and Bracket Expressions](#character-classes-and-bracket-expressions)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Author](#author)

## Regex Components

### Anchors

Anchors are used to specify the position within a string where a match must occur.

**Anchor:** `^`

  - **Code Snippet:** `/^#`
  - **Description:** The `^` anchor asserts the position at the start of a string. In this example, `/^#` indicates that the beginning of the string must match the character `#`; however, as you will see in the [Quantifiers](#quantifiers) section, `#` is actually optional within this regex. `#` is used to distinguish a hexadecimal number from a decimal number. 

**Anchor:** `$`

 - **Code Snippet:** `$/`
 - **Description:**  The `$` anchor asserts the position at the end of a string. For example, `5$` indicates that the string must end with `5`. In this regex, the end of the string must match the 6-character or 3-character pattern identified before the `$` anchor.

### Quantifiers

Quantifiers define the number of occurrences of a character or group. In the regex used to match hexadecimal color values, we use:

**Quantifier:** `?`

  - **Code Snippet:** `/^#?`
  - **Description:** `?` makes the preceding character optional. In this regex, `#?` makes the `#` character optional, meaning it can appear at the beginning of the string or not at all.

**Quantifier:** `{`_n_`}`

  - **Code Snippets:** `{6}` and `{3}`
  - **Description:** `{n}` specifies exactly `n` occurrences of the preceding character or group. In the regex used to match hexadecimal color values:
    - `{6}`specifies matching exactly six characters, so `[a-f0-9]{6}` matches any six characters that are either digits (0-9) or letters (a-f).
    - `{3}` specifies matching exactly three characters, so `[a-f0-9]{3}`matches any three characters that are either digits (0-9) or letters (a-f).

### OR Operator

The OR operator `|` is used to match one pattern _or_ another. 

  - **Code Snippet:** `([a-f0-9]{6}|[a-f0-9]{3})`
  - **Description:** In this regex, the OR operator `|` means it will match either a 6-digit hex value _or_ a 3-digit hex value.

### Character Classes and Bracket Expressions

Character classes define a set of characters to match. Bracket expressions, which are a type of character class, are used to list characters or ranges of characters.

  - **Code Snippet:** `[a-f0-9]`
  - **Description:** This matches any character that is a lowercase letter from `a` to `f` or a digit from `0` to `9`. Bracket expressions are used here to define the character class, specifying the range of characters to be matched.

Bracket expressions can also include ranges like `[a-f]`, which matches any character from `a` to `f`, or named character classes like `[[:digit:]]`, which matches any digit.

### Grouping and Capturing

Grouping is done using parentheses (), and it allows us to capture parts of the matching string for later use.

  - **Code Snippet:** `([a-f0-9]{6}|[a-f0-9]{3})` 
  - **Description:** This captures either the 6-character or 3-character hex value.

### Greedy and Lazy Match

Quantifiers are greedy by default, meaning they match as many characters as possible. To make them lazy, you can append a `?` to the quantifier.

- **Examples:** `{6}` is **greedy** and will match _exactly_ six characters, `[a-f0-9]{6}`. If it were a lazy `{6}?`, it would match as few characters as possible (although this is not relevant to this regex). 


## Author

This tutorial was created by Katy Totah. You can find more of my work on [GitHub](https://github.com/ktotah).