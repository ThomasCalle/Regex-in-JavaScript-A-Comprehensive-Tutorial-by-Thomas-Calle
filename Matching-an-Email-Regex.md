# Matching an Email Regex: Understanding the Components by Thomas Calle

Welcome to this comprehensive tutorial on matching email regular expressions (regex) using JavaScript in the field of Computer Science. Upon completing the tutorial, both newcomers and academics alike will have a clear comprehension and understanding of regex components, achieved through detailed explanations and example analysis. In this tutorial, we will delve into email regex, breaking down the components of a regex pattern designed to validate email addresses and explaining how each part contributes to ensuring accurate and reliable email validation.

<br>

# Summary
Throughout this tutorial, the featured regular expression (regex) as seen below, will be referenced for analysis in regards to each regex component to ensure new-comers and academics alike are able to understand and grasp material with absolute clarity. The regex components discussed in this document include: anchors, quantifiers, grouping constructs, bracket expressions, character classes, the OR operator, flags, and character escapes.

***The Regex Featured in This Tutorial is Below:***
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
<br>

## Table of Contents:
- [Overview](#overview)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [Author](#author)

## Anchors

Regular expressions are powerful tools for matching patterns in text. Anchors, which are special characters in regular expressions, play an essential role in defining the position of the pattern within the input string. In the context of email validation, like in the regex featured in this tutorial `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, it is crucial to ensure that the entire input string matches the specified pattern, rather than just a part of it.

### Anchors Come in (2) Main Types:
1. Start Anchor `^`: This asserts that the pattern must match the start of the string.
2. End Anchor `$`: This asserts that the pattern must match the end of the string.

Anchors essentially define the boundaries of the text that the regular expression should match. 
<br>
**Example One:** the regex `^hello$` matches only the string `"hello"` and nothing else. It won't match `"hello world"` or `"say hello"` because the pattern is not at the start or end of the string, respectively.
<br>
**Example Two:** the regex `^hello` matches any string where `"hello"` is at the start of the string. It will match `"hello"` in `"hello world"`, but it will not match `"hello"` in `"world hello"` because the string does not start with `"hello"`.
<br>
**Example Three:** the regular expression `hello$` matches any string where `"hello"` is at the end of the string.  It will match `"hello"` in `"world hello"` but it will not match` "hello"` in `"hello world"` because the string does not end with `"hello"`.



In the context of email validation, anchors are invaluable because they help ensure that the entire email address adheres to the specified pattern. This is essential for accurate validation, as it prevents partial matches or unwanted results.
By setting boundaries at the start and end of the string, anchors guarantee that the pattern matches only the intended text. They are critical components of pattern matching in text processing, particularly when validating email addresses using a regex like `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`. In conclusion, anchors play a vital role in defining the position of the pattern within the input string and ensure accurate and reliable validation.


## Quantifiers

In regular expressions(regex), quantifiers are used to specify how many times a pattern should match. Quantifiers are placed after a character, character class, or group, in order to determine the minimum and maximum number of times preceding patterns should occur.

The `+` quantifier means "one or more," and is used after the pattern `[a-z0-9_\.-]` in the first capturing group `([a-z0-9_\.-]+)`. This indicates that the pattern `[a-z0-9_\.-]` should occur at least once, but it can also occur multiple times consecutively. Thus, the group will match one or more lowercase letters, digits, underscores, dots, or hyphens.

Similarly, the `+` quantifier is used after the pattern `[\da-z\.-]` in the second capturing group `([\da-z\.-]+)`. This group matches one or more digits, lowercase letters, dots, or hyphens.

The `{2,6}` quantifier is used after the character class `[a-z\.]` in the third capturing group `([a-z\.]{2,6})`. This group matches a sequence of 2 to 6 lowercase letters or dots. This means that the email address must end with a two to six letter top-level domain, such as .com, .edu, or .co.uk.

Putting it all together, the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` matches a valid email address that starts with one or more lowercase letters, digits, underscores, dots, or hyphens, followed by the `@` symbol, followed by one or more digits, lowercase letters, dots, or hyphens, followed by a period and a two to six letter top-level domain.

**Example:** In regex, quantifiers specify how many times a pattern should match. They are placed after a character, character class, or group to determine the minimum and maximum occurrences of the preceding pattern.

Given the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`:

1. Quantifier `+` : Matches "one or more" occurrences.
   - `([a-z0-9_\.-]+)`: Matches one or more lowercase letters, digits, underscores, dots, or hyphens.
   - `([\da-z\.-]+)`: Matches one or more digits, lowercase letters, dots, or hyphens.

2. Quantifier `{2,6}` : Matches between 2 and 6 occurrences.
   - `([a-z\.]{2,6})`: Matches a sequence of 2 to 6 lowercase letters or dots.

The regex above matches valid email addresses with the following pattern:
- One or more lowercase letters, digits, underscores, dots, or hyphens
- Followed by the `@` symbol
- Followed by one or more digits, lowercase letters, dots, or hyphens
- Followed by a period
- Ending with a two to six letter top-level domain (e.g., .com, .edu, .co.uk)

### Conclusion

Quantifiers are essential in regex as they allow you to control the number of occurrences of a pattern. Therefore, understanding how to properly use quantifiers, you are able create more precise and flexible regular expressions throughout your studies for various use cases.

## Grouping Constructs

Grouping constructs in regular expressions (regex) are used to group together one or more characters or sub-expressions, and treat them as a single unit within the expression. They are enclosed among the parentheses `()` and serve the following purposes:

- Applying quantifiers to a group of characters.
- Capturing the designated part of the match for later use.
- Creating backreference for previously matched group.
- Applying alternation to a group of characters

Our **regex featured in this tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` contains (3) Grouping Constructs enlcosed among the parentheses `()`. Each group captures a different part of the email address: 1. Local-Part, 2. Domain, and 3. Top-level Domain.

Firstly, the **Local-Part** `([a-z0-9_\.-]+)` matches the username of the email address. Secondly, the **Domain** `([\da-z\.-]+)` corresponds and matches the domain name. Thirdly, the **Top-Level Domain** `([a-z\.]{2,6})` aligns and matches the top-level domain. Furthering our distinction of the (3) Grouping Constructs, a comprehensive breakdown of the following has been provdided below for your review:

### 1. Local-Part:
Firstly, the `([a-z0-9_\.-]+)` matches the username of the email address.

The group represents the local-part of the email address which helps to ensure that the username follows a valid format (the part before the `@` symbol) and matches one or more characters that can be:
* Lowercase letters: `a-z`
* Numbers: `0-9`
* Underscores: `_`
* Dots: `.`
* Hyphens: `-`

**Example:** Consider the email address: `john_doe.123@example.com`

The Local-Part of the email address is `john_doe.123`. It matches the regex `([a-z0-9_\.-]+)` for the following reasons:

* It contains lowercase letters: `j`, `o`, `h`, `n`, `d`, `o`, and `e`
* It contains numbers: `1`, `2`, and `3`
* It contains an underscore: `_`
* It contains a dot: `.`

This Local-Part follows a valid format and is in compliance with the regex pattern provided. The regex pattern `([a-z0-9_\.-]+)` effectively captures the username portion of the email address as seen above, by allowing a combination of lowercase letters, numbers, underscores, dots, and hyphens.


### 2. Domain:
Secondly, `([\da-z\.-]+)` corresponds and matches the **Domain** name.

The group represents the domain of the email address (the part between the `@` symbol and the final period `.`). This helps to ensure that the domain name follows a valid format and matches one or more characters that can be:
* Numbers: `\d`
* Lowercase letters: `a-z`
* Dots: `.`
* Hyphens: `-`

**Example:** Consider the email address: `jane.smith@sub-domain123.example.com`

The Domain of the email address is sub-domain123.example. It matches the regex `([\da-z\.-]+)` for the following reasons:

It contains lowercase letters: `s`, `u`, `b`, `d`, `o`, `m`, `a`, `i`, `n`, `e`, `x`, `a`, `m`, `p`, `l`, and `e`
* It contains numbers: `1`, `2`, and `3`
* It contains a dot: `.`
* It contains a hyphen: `-`

This Domain follows a valid format and is in compliance with the regex pattern provided above. The regex pattern `([\da-z\.-]+)` effectively captures the domain name portion of the email.

### 3. Top-Level Domain:
Thirdly, `([a-z\.]{2,6})` aligns and matches the **Top-Level Domain**.

The group represents the **Top-Level Domain** of the email address (the part after the final period `.`). This helps to ensure that only the valid top-level domains are accepted and matches between `2` to `6` characters that can be:
* Lowercase letters: `a-z`
* Dots: `.`

**Example:** Consider the email address: `john_doe.123@example.com`

The Top-Level Domain of the email address is `com`. It matches the regex `([a-z\.]{2,6})` for the following reasons:

* It contains lowercase letters: `c`, `o`, and `m`
* It has a length of 3 characters, which falls within the valid range of `2` to `6` characters.

The Top-Level Domain follows a valid format and is in compliance with the regex pattern provided above. The regex pattern `([a-z\.]{2,6})` effectively captures the top-level domain portion of the email address by allowing a combination of lowercase letters and dots, with a length constraint of between 2 to 6 characters.

### Conclusion:

In conclusion, the Grouping Constructs section of the tutorial thus far focus on understanding and dissecting our regex pattern `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` for validating email addresses. This regex pattern consists of three main grouping constructs: 1) Local-Part, 2) Domain, and 3) Top-Level Domain. Therefore, each of these groups serves a specific purpose in the validation process. The Local-Part ensures the username portion of the email address follows a valid format, the Domain checks the compliance of the domain name, and the Top-Level Domain verifies the validity of the top-level domain. Thereby, utilizing these grouping constructs, the regex pattern effectively captures and validates different components of an email address, ensuring that it adheres to the accepted standards.

## Bracket Expressions

Bracket expressions are a fundamental concept in regular expressions (regex), used to define a set of characters that can be matched within a single position in a text string. They are denoted by square brackets `[...]`, and any character enclosed within these brackets will become a part of the allowed set. Bracket expressions can contain individual characters, and even define character ranges using a hyphen `-`, such as `a-z` for all lowercase letters or `0-9` for digits. But, what's the purpose? Simply, the bracket expressions, creates flexible patterns that match various combinations of characters in your target text.

In our **regex featured in this tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` there are (3) main bracket expressions:

### 1. Bracket Expression:
The bracket expression `[a-z0-9_\.-]` matches any single character in the range `a-z`, `0-9`, or one of the characters `_`, `.`, or `-`. Thus the expression is used to match the **Grouping Constructs: local part** the username part of the email address. 

Here's the breakdown of this expression:
- `a-z`: Matches lowercase letter from `a` to `z`.
- `0-9`: Matches digit from `0` to `9`.
- `_`: Matches underscore character.
- `\.`: Matches literal period (dot) character. The backslash is used to escape the dot since it has a special meaning in regex.
- `-`: Matces the hyphen character.

**Example:** Consider the following email address: `thomas_1234-@bootcamp.edu`

The local part, of the username, is `thomas_1234-`.

Now let's break it down according to the bracket expression `[a-z0-9_\.-]`:
- `thomas` contains lowercase letters `t`, `h`, `o`, `m`, and `s`, matching the `a-z` part of the expression.
- `_` is an underscore character, matching the `_` part of the expression.
- `1234` contains digits `1`, `2`, `3`, and `4`, matching the `0-9` part of the expression.
- `-` is a hyphen character, matching the `-` part of the expression.
- `.` is a literal period (dot) character, matching the `\.` part of the expression.

In the example, the bracket expression `[a-z0-9_\.-]` successfully matches the local part `thomas_1234-` of the email address.

### 2. Bracket Expression:
The bracket expression `\da-z\.-` matches any single character in the range `0-9`, `a-z`, or one of the characters `.`, or `-`. Thus the expression is used to match the **Grouping Constructs: domain** part of the email address.

Here's the breakdown of this expression:
- `\d`: Matches digit from `0` to `9`. This is a shorthand for `[0-9]`.
- `a-z`: Matches lowercase letter from `a` to `z`.
- `\.`: Matches the literal period (dot) character.
- `-`: Matches hyphen character.

**Example:** Consider the following email address: `thomas1234@boot-camp2023.edu`

The domain part of the email address is `boot-camp2023.edu`.

Now let's break it down according to the bracket expression `[\da-z\.-]`
- `boot` contains lowercase letters `b`, `o`, and `t`, matching the `a-z` part of the expression.
- `-` is a hyphen character, matching the `-` part of the expression.-
- `camp` contains lowercase letters `c`, `a`, `m`, and `p`, matching the `a-z` part of the expression.
- `2023` contains digits `2`, `0`, `2`, and `3`, matching the `\d` part of the expression.
- `\.` is a literal period (dot) character, matching the `\.` part of the expression.
- `edu` contains lowercase letters `e`, `d`, and `u`, matching the `a-z` part of the expression.

In this example, the bracket expression `[\da-z\.-]` successfully matches the domain part `boot-camp2023.edu` of the email address.

### 3. Bracket Expression:
The bracket expression `[a-z\.]{2,6}` matches any single character in the range `a-z` or the literal period (dot) character. The expression is then followed by a quantifier `{2,6}`, which specifies that the matched characters must occur between `2 and 6` times, inclusive. Thus used to match the **Grouping Constructs: top-level domain** of the email address. 

Here's the breakdown of this expression:
- `a-z`: Matches lowercase letter from `a` to `z`.
- `\.`: Matches literal period (dot) character.
- `{2,6}`: Matches quantifier that specifies the number of times the preceding expression (i.e., `[a-z\.]`) must be matched, which is between 2 and 6 times, inclusive.

**Example:** Consider the following email address: `thomas_1234.email@bootcamp123.examp.le`

The top-level domain part of the email address is `examp.le`.

Now let's break it down according to the bracket expression `[a-z\.]{2,6}`:
- `examp.le` contains lowercase letters `a-z` (specifically, `e`, `x`, `a`, `m`, and `p`), matching the `a-z` part of the expression.
- `\.` is a literal period (dot) character, matching the `\. `part of the expression.
- `examp.le` the entire top-level domain part `examp.le` matches the `{2,6}` quantifier, as it consists of 6 characters in total (5 letters and 1 dot).

In the example, the bracket expression `[a-z\.]{2,6}` successfully matches the top-level domain part `examp.le` of the email address.

#### Conclusion
In brief, our featured regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` efficiently matches valid email addresses by utilizing bracket expressions to define character sets for the username, domain, and top-level domain parts of the email address as we discussed earlier. These bracket expressions combined with other regex components, ensures proper structure and formality for email addresses, making it a valuable tool in a variety of applications.

## Character Classes

Character classes, known as character sets, are a short and more concise regular expressions(regex) that represent specific sets of characters. Through the use of character classes, you can simplify and shorten regex patterns, thereby making them readable and easier to understand.

In our **regex featured in this tutorial:** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` uses various regex elements, including `character classes`, `character sets`, `metacharacters`, and `repeating character classes`. These elements ensure the regex are assesed and sourced accurately to match the email addresses.

### Character Classes and Character Sets:
The featured email regex uses two primary character classes: `\d` and `..` Character sets are defined within square brackets, such as `[a-z]`, `[0-9]`, and `[.-]`. These sets represent multiple characters, allowing a single character match from the specified range.

**Example:** Consider the following `/[a-zA-Z0-9]/`

This regex pattern matches a single alphanumeric character, which can be an uppercase letter, a lowercase letter, or a digit. The character class `\d` matches a digit, while [a-z] and [A-Z] are character sets that match lowercase and uppercase letters, respectively. Combining these character sets within square brackets creates a pattern that matches any single alphanumeric character.

### Metacharacters Inside Character Classes:
The metacharacters are characters with special meanings in regex, such as the dot `(.)`. Inside character classes, some metacharacters lose their special meaning and are treated as literals. In our featured email regex, the hyphen `(-)` and the dot `(.)` are metacharacters placed inside character classes `[a-z0-9_.-]` and `[\da-z.-]`. The dot (.) does not need to be escaped with a backslash, and the hyphen is used as a literal character without escaping, as it is placed at the beginning or end of the character set.

**Example:** Consider the following `/[\dA-Za-z.,-]/`

This regex pattern matches a single digit, an uppercase letter, a lowercase letter, a literal period `(.)`, a comma `(,)`, or a hyphen `(-)`. The character classes `\d`, `[A-Z]`, and `[a-z]` match digits, uppercase letters, and lowercase letters, respectively. The metacharacters `.` and `-` are placed inside the character class without any special meaning, as they are treated as literals. The hyphen `(-)` is used as a literal character without escaping because it is placed at the beginning or end of the character set.

### Repeating Character Classes:
The email regex uses the `+` and `{2,6}` quantifiers to indicate repeating character classes as discussed before. The plus sign `(+)` matches one or more occurrences of the preceding character class or set, as in `[a-z0-9_.-]+` and `[\da-z.-]+`. Therefore the curly braces `({2,6})` define a specific range of repetitions for the preceding character class or set, as in `[a-z.]{2,6}`, which matches `2 to 6` occurrences of lowercase letters or the literal period (dot) characters found.

**Example:** Consider the following `/A{2,4}/`

This regex pattern matches a string containing the uppercase letter `A` repeated `2 to 4` times. The character class `[A]` matches the uppercase letter `A`, and the quantifier `{2,4}` specifies that it should be repeated `2 to 4` times.

In this example, the regex pattern would match strings such as `"AA"`, `"AAA"`, and `"AAAA"`. However, it would not match strings with just one `A` or more than four `A`s in a row.

#### Conclusion

Character classes play a crucial role in making regular expressions more concise and easier to read. They allow us to define specific sets of characters and patterns using simple syntax. The character sets, metacharacters inside character classes, and repeating character classes all work together to create versatile regex patterns. By understanding how to use these elements, we can create more efficient and effective regex patterns for various use cases, such as matching email addresses, as demonstrated in this tutorial.

## Character Escapes

Character escapes are an essential aspect of regex, allowing for accurate pattern matching by suppressing the special meaning of metacharacters and representing characters that cannot be directly typed. Consider the context of our **regex featured in this tutorial** `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` throughout the section and examples, as we can identify the use of character escapes and their purposes:

### Backslash: 
The backslash is a common escape character used to treat metacharacters as literals in regex. Throughout our featured regex, the dot `(.)` is escaped with a backslash, exactly like this `\.`. Thus ensuring the dot is treated as a literal period instead of a metaphorical wildcard.

**Example:** Consider the following two email addresses:
1. `thomas.val@bootcamp.edu` **(valid)**
2. `thomas@inval@bootcamp.edu` **(invalid)**

The regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` contains the backslash to escape the dot `(.)` in the pattern. Among this regex, `\.` is used to match a literal period within the email address. This ensures that the regex correctly matches valid email addresses, as seen in the first example, while it is not matching the invalid email addresses, as seen in the second example.

If the dot `(.)` were not escaped, it would act as a wildcard character, potentially matching any character in its place, and resulting in the regex incorrectly matching invalid email addresses.

By escaping the dot `(.)` with a backslash (like this: `\.`), we ensure that the regex only matches valid email addresses with literal periods in the appropriate positions, preventing the dot from acting as a wildcard and allowing for more accurate pattern matching.

### Metacharacters: 
Metacharacters have siginifcant meaning in regex, such as the dot `(.)`, plus sign `(+)`, and caret `(^)`. In character classes, the hyphen `-` typically denotes a range between two characters (e.g., `a-z`, `0-9`). However, if the hyphen is placed at the beginning or end of the character class, or if it is escaped with a backslash, it is treated as a literal character. In our featured email regex, the hyphen `(-)` is used as a literal character inside the character classes `[a-z0-9_\.-]` and `[\da-z\.-]`, where it is placed at the beginning or end of the character class. As a result, there is no need to escape it with a backslash in this context.

**Example:** Consider the following two email addresses:
1. `thomas-val@bootcamp.com` **(valid)**
2. `thomas--val@bootcamp.com` **(valid)**
3. `thomas@val_bootcamp.com` **(invalid)**

Among the provided regex, the hyphen `(-)` is used as a literal character inside the character classes `[a-z0-9_\.-]` and `[\da-z\.-]`. Thereby, placing the hyphen at the beginning or end of the character class, we can include it as a literal character without escaping it with a backslash. Therefore, the regex accurately matches the valid email addresses containing hyphens, such as the three email addresses as seen above. Correct handling of the hyphen metacharacter allows the regex to match valid email addresses of the first and second email which include hyphens in both the username and domain parts of the address.

The third email address, `thomas@val_bootcamp.com`, is invalid due to it containing an underscore _ in the domain part of the address. The underscore is not allowed in domain names according to the email regex pattern we have used throught the entire tutorial. The character class `[\da-z\.-]` in the domain part will only allow digits, lowercase letters, dots, and hyphens. Therefore, the underscore is not included in this character class, as the regex does not match the third email address, which is why it has been labled invalid.

### Escape sequences: 
Escape sequences, are characters that can not be directly typed or represented in a string, so escape sequences are the implemented, then used. These sequences start with a backslash `(\)` followed by a letter or combination of letters. In the email regex, `\d` is an escape sequence that represents any digit from `0` to `9`, serving as a shorthand for the use of `[0-9]`.

**Example:** Consider the following two email addresses:
1. `thomas.val2023@bootcamp.com` **(valid)**
2. `thomas123_val@bootcamp.com` **(valid)**
3. `tval@bootcamp7.com` **(valid)**
4. `thomas.val@2023bootcamp.com` **(invalid)**

Among the provided regex, the escape sequence `\d` is used to represent any digit from `0` to `9`. It serves as a shorthand for the character class `[0-9]` and allows the regex to match valid email addresses containing digits.

throughout the example, the regex accurately matches valid email addresses that contain digits, such as the 1st email, 2nd email, and 3rd email addresses as seen above. That said, it does not match the 4th email address, `thomas.val@2023bootcamp.com`, as it is invalid due to it starting with a digit right after the `'@'` symbol, which is not allowed among the given regex pattern. The use of the escape sequence `\d` allows the regex to match valid email addresses with digits in both the username and domain parts of the address, as long as the domain does not start with a digit immediately after the `'@'` symbol.

#### Conclusion
Character escapes serve a crucial role for ensuring accurately matching text patterns by interpreting special characters as literals. They help suppress the special meanings of metacharacters and represent characters that can't be directly typed. Thereby, ensuring the proper functioning of regex expressions that contribute to reliable email validation. 

## Author

Follow me on Github at [Thomas Calle](https://github.com/ThomasCalle). Additional questions or concerns? feel free to contact me.

Until next, see you on the otherside!

**Deployed GitHub-Gist Link:**
[Deployed GitHub-Gist Link: Click Here](https://gist.github.com/ThomasCalle/df5f3d3441f4206d9087f9643ffff91e)

**GitHub Repository:**
[GitHub Repository: Click Here](https://github.com/ThomasCalle/Regex-in-JavaScript-A-Comprehensive-Tutorial-by-Thomas-Calle)

© 2023 [Thomas Calle](https://github.com/ThomasCalle). Confidential and Proprietary. All Rights Reserved.
