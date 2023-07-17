# Computer Science for JavaScript: Regex Tutorial on Matching a URL

Regular expressions or Regex for short, are extremely useful and powerful tool in extracting information from text such as code, log files, spreadsheets, or even documents. One common use case is validating and matching URLs (Uniform Resource Locators). 

In this tutorial, we will learn how to use Regex to verify whether a given string adheres to the standard URL format.

<img width="599" alt="url-regex" src="https://github.com/mcramileux/mcramileux-regex-tutorial/assets/122607160/ac995b9b-c50a-4d4a-b091-a9f2babdabf8">

## Summary

In this gist, I will explain how to use a regular expression that validates URLs by ensuring that it follows a specific pattern:

```regex
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

The series of random characters above looks like a secret code to me but this "secret code" is actually a regular expression sequence of the following regex components that will be discussed below.

Now, let's dive into each Regex Component and learn how to build a robust URL matching pattern using this gist!

## Table of Contents
- [Computer Science for JavaScript: Regex Tutorial on Matching a URL](#computer-science-for-javascript-regex-tutorial-on-matching-a-url)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [Anchors](#anchors)
    - [Quantifiers](#quantifiers)
    - [Grouping Constructs](#grouping-constructs)
    - [Bracket Expressions](#bracket-expressions)
    - [The OR Operator](#the-or-operator)
    - [Flags](#flags)
    - [Character Escapes](#character-escapes)
  - [Author](#author)

## Regex Components
To start writing the series of expressions, it must start with a `/` and end of the string. For example:

`/hello/`

### Anchors
The characters `^` and `$` are both considered to be anchors and how they can be used to match the start and end of a string, respectively.
  
### Quantifiers
Quantifiers allow you to specify how many times you want a particular regex string to match. Quantifiers usually come in two variants: lazy and greedy. By default, regex matching is eager and will match as much as possible, which is not always the desired behavior. Lazy quantifiers allow you to limit how much is matched, and you can further specify how many times matches are found with other limiting characters, such as:

- `+` matches the pattern one or more times
- `*` matches the pattern zero or more times
- `?` matches the pattern zero or one time
- `{}` curly brackets can provide three different ways to set limits for a match:
    - `{n}` matches the pattern exactly n number of times
    - `{n,}` matches the pattern at least n number of times
    - `{n,x}` matches the pattern from a minimum of n number of times to a maximum of x number of times

To breakdown the regex above: 
- `(https?:\/\/)?` is an optional group. The `?` quantifier makes the preceding group match zero or one occurrence. It matches the protocol part of the URL, allowing for either "http://" or "https://".

- `([\da-z\.-]+)` captures the domain name in a group. The `+` quantifier makes the preceding group match one or more occurrences. It matches alphanumeric characters, dots, or hyphens.
  
- `\.([a-z\.]{2,6})` matches the top-level domain (TLD) part of the URL. It starts with a dot and is followed by a group of two to six lowercase letters or dots. The `{2,6}` quantifier specifies that the group should match between 2 to 6 occurrences.

- `([\/\w \.-]*)*` captures optional path segments, query parameters, or fragments of the URL. The `*` quantifier makes the preceding group match zero or more occurrences. It matches any character from the set [/, \w (alphanumeric), space, dot, hyphen].

- `\/?` matches an optional trailing slash (/) at the end of the URL. The `?` quantifier makes the preceding group match zero or one occurrence.
  
### Grouping Constructs
Grouping constructs in regular expressions are used to group together multiple characters or subpatterns and treat them as a single unit. They are denoted by parentheses `(` and `)`.

To group the regex sample above, here's how it looks like:
```regex
(https?:\/\/) ([\da-z\.-]+) ([a-z\.]{2,6}) ([\/\w \.-]*)
```

### Bracket Expressions
Bracket expressions, also known as character classes, are a feature in regular expressions that allow you to define a set or range of characters to match against a single character position in the input string. They are denoted by square brackets `[ ]`.

Within a bracket expression, you can specify a list of characters or character ranges. Some common examples are:

- `[abc]`: Matches either "a", "b", or "c".
- `[0-9]`: Matches any digit from 0 to 9.
- `[a-z]`: Matches any lowercase letter from "a" to "z".
- `[A-Z]`: Matches any uppercase letter from "A" to "Z".
- `[0-9a-fA-F]`: Matches any hexadecimal digit.

A few special characters have special meanings when used inside a bracket expression:

- Hyphen (-): Specifies a character range. For example, `[a-z]` matches any lowercase letter.
- Caret (^): When used as the first character inside the brackets, it negates the character set. For example, `[^0-9]` matches any character that is not a digit.
- Backslash (\): Escapes a special character inside the bracket expression.

To group the regex sample above, here's how it looks like:
```regex 
  [\da-z\.-] [a-z\.] {2,6} [\/\w \.-]
```

Bracket expressions provide a concise way to define character sets and ranges for matching specific characters in a regular expression pattern.

### The OR Operator
The OR operator, denoted by the vertical bar `|` in regular expressions, is used to specify alternatives within a pattern. It allows you to match one pattern or another.

### Flags
Flags are optional parameters that modify the behavior of the pattern matching. They are usually added as suffixes to the regular expression and change how the pattern is interpreted or applied.

### Character Escapes
In regular expressions, character escapes are used to match a specific character that has a special meaning in the regular expression syntax. It allows you to match these special characters literally instead of interpreting them as metacharacters.

Character escapes are typically represented by a backslash `\` followed by the character to be escaped. Here are some common examples of character escapes in regular expressions:

  - `\.` (Escapes the dot (.) character) - it matches a literal dot instead of its special meaning, which is to match any character (except newline) in regular expressions.

  - `\/` (Escapes the forward slash (/) character) - it matches a literal forward slash instead of its special meaning, which is often used as a delimiter in regular expressions.

  - `\\` (Escapes the backslash (\) character) -  it matches a literal backslash instead of its special meaning as an escape character.

  - `\+, \-, \*, etc.` (Escapes special characters like +, -, *, etc.) - it is to match them literally instead of their special meanings in regular expressions.

  - `\d, \w, \s` These are shorthand character classes that match digits (\d), word characters (\w), and whitespace characters (\s), respectively. They are used as escapes to represent these predefined character classes.

By using character escapes, you can match specific characters literally, even if they have special meanings within the regular expression syntax. It helps to distinguish between their literal interpretation and their special behavior as metacharacters.

## Author
Kristine Ramilo, also known as mcramileux on various online platforms including [GitHub](https://github.com/mcramileux), is currently pursuing a Full Stack Bootcamp program at the University of Adelaide. Having accumulated over ten years of experience in the Hospitality Industry, Kristine is embarking on a significant career transition into the Web Development Industry.