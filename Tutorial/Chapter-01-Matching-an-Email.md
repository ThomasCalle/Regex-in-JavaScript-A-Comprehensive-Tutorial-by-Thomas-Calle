# Regex in JavaScript: A Comprehensive Tutorial by Thomas Calle

# Chapter 01: Matching an Email: Understanding the Components by Thomas Calle

# Summary
In this Regex Tutorial, you will learn how to validate the featured email address regular expression (regex) **Regex Featured in This Tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`. The tutorial provides a comprehensive breakdown and explanation of each component within the regex, simplifying the validation process for easy understanding. Upon completing this tutorial, academics and new-comers alike will gain a deeper understanding and comprehension of how the regex functions to validate and confirm the entry of a valid email address.

## Table of Contents:
- [Overview](#overview)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Author](#author)

## Anchors

**Anchor Start:** **Anchor End:**

Regular expressions are powerful tools for matching patterns in text. Anchors, which are special characters in regular expressions, play an essential role in defining the position of the pattern within the input string. In the context of email validation, like in the regex featured in this tutorial `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, it is crucial to ensure that the entire input string matches the specified pattern, rather than just a part of it.

**Anchors Come in (2) Main Types:**
1. Start Anchor `^`: This asserts that the pattern must match the start of the string.
2. End Anchor `$`: This asserts that the pattern must match the end of the string.

Anchors essentially define the boundaries of the text that the regular expression should match. For example, the regular expression `^hello$` matches only the string "hello" and nothing else. It won't match "hello world" or "say hello" because the pattern is not at the start or end of the string, respectively.
In the context of email validation, anchors are invaluable because they help ensure that the entire email address adheres to the specified pattern. This is essential for accurate validation, as it prevents partial matches or unwanted results.
By setting boundaries at the start and end of the string, anchors guarantee that the pattern matches only the intended text. They are critical components of pattern matching in text processing, particularly when validating email addresses using a regex like `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`. In conclusion, anchors play a vital role in defining the position of the pattern within the input string and ensure accurate and reliable validation.


## Quantifiers

In regular expressions(regex), quantifiers are used to specify how many times a pattern should match. Quantifiers are placed after a character, character class, or group, in order to determine the minimum and maximum number of times preceding pattern occur.

The `+` quantifier means "one or more," and used after the pattern `[a-z0-9_\.-]` in the first capturing group `([a-z0-9_\.-]+)`. This indicates that the pattern `[a-z0-9_\.-]` should occur at least once, but it can also occur multiple times consecutively. Thus, the group will match one or more lowercase letters, digits, underscores, dots, or hyphens.

Similarly, the `+` quantifier is used after the pattern `[\da-z\.-]` in the second capturing group `([\da-z\.-]+)`. This group matches one or more digits, lowercase letters, dots, or hyphens.

The `{2,6}` quantifier is used after the character class `[a-z\.]` in the third capturing group `([a-z\.]{2,6})`. This group matches a sequence of `2` to `6` lowercase letters or dots. This means that the email address must end with a two to six letter top-level domain, such as .com, .edu, or .co.uk.

Putting it all together, the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` matches a valid email address that starts with one or more lowercase letters, digits, underscores, dots, or hyphens, followed by the "@" symbol, followed by one or more digits, lowercase letters, dots, or hyphens, followed by a period and a two to six letter top-level domain.

## Grouping Constructs

Grouping constructs in regular expressions(regex) are used to group together one or more characters or sub-expressions, and treat them as a single unit within the expression. They are enclosed among the parentheses () and serve the following purposes:

- Applying quantifiers to a group of characters.
- Capturing a the designated part part of the match for later use.
- Creating backreference for previously matched group.
- Applying alternation to a group of characters

Our **regex featured in this tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` contains three (3) `Grouping Constructs` enlcosed among the parentheses `()`. Each group captures a different part of the email address: the 1. Local-Part, 2. Domain, and 3. Top-level Domain.

Firstly, the 'Local-Part' `([a-z0-9_\.-]+)` matches the username of the email address. Secondly, the 'Domain' `([\da-z\.-]+)` corresponds and matches the domian name. Thirdly, the 'Top-Level Domain' `([a-z\.]{2,6})` aligns and matches the top-level domain. Furthering our distinction of the three (3) `Grouping Constructs` please, review my comprehensive breakdown of the following below: 1. The Local-part, 2. Domain and 3. Top-Level Domain.

### 1. Local-Part:
Firstly, the `([a-z0-9_\.-]+)` matches the username of the email address.

The group represents the local-part of the email address which helps to ensure that the username follows a valid format (the part before the `@` symbol) and matches one or more characters that can be:
* Lowercase letters: `a-z`
* Numbers: `0-9`
* Underscores: `_`
* Dots: `.`
* Hyphens: `-`

### 2. Domain:
Secondly, `([\da-z\.-]+)` corresponds and matches the 'Domain' name.

The group represents the domain of the email address (the part between the `@` symbol and the final period `.`). This helps to ensure that the domain name follows a valid format and matches one or more characters that can be:
* Numbers: `\d`
* Lowercase letters: `a-z`
* Dots: `.`
* Hyphens: `-`

### 3. Top-Level Domain:
Thirdly, `([a-z\.]{2,6})` aligns and matches the 'Top-Level Domain'.

The group represents the 'Top-Level Domain' of the email address (the part after the final period `.`). This helps to ensure that only the valid top-level domains are accepted and matches between 2 to 6 characters that can be:
* Lowercase letters: `a-z`
* Dots: `.`

**Conclusion:** The above `Grouping Constructs` are useful for capturing specific parts of the matched email address, which can then be accessed or manipulated separately. Example: regular expression(regex) validates email addresses, username and domain name can then be independently obtained and assessed for accuracy, the top-level domain can then be used to ensure only accuractly sourced domain extensions are accepted.

In conclusion, `Grouping Constructs` effectively group characters and sub-expressions together, in order to perform operations on them collectively as a single unit. Thus, allowing the use of complex and flexibly adapted regular expressions(regex).

### Conclusion: Grouping Constructs Explanation

Our **regex featured in this tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` can be read as follows:

1. `^` matches the start of the string.
2. `([a-z0-9_\.-]+)` matches the local-part(user name) of the email addresss containing: lowercase letters, digits, underscores, periods, or hyphens.
3. `@` matches the `@` symbol.
4. `([\da-z\.-]+)` matches/captures the domain of the email address: with digits, lowercase letters, periods, or hyphens.
5. `\.` matches the final period `.`.
6. `([a-z\.]{2,6})` matches/captures the top-level domain containing: lowercase letters or periods with a length between 2 and 6 characters.
7. `$` matches the end of the string.

## Author

Follow me on Github at [Thomas Calle](https://github.com/ThomasCalle). Additional questions or concerns? feel free to contact me.

Until next, see you on the otherside!

© 2023 [Thomas Calle](https://github.com/ThomasCalle). Confidential and Proprietary. All Rights Reserved.
