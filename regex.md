# **Regex Cheatsheet**

## Basic Symbols

- **`.`** (Dot): Matches any single character except newline (`\n`).
- **`^`**: Matches the start of a string.
- **`$`**: Matches the end of a string.
- **`[ ]`**: A character class. Matches any one of the characters inside the square brackets. For example, `[abc]` matches either "a", "b", or "c".
- **`|`**: Logical OR operator. Matches patterns on either side of the `|`. For example, `a|b` matches either "a" or "b".

## Quantifiers

- **`*`**: Matches 0 or more occurrences of the preceding element.
- **`+`**: Matches 1 or more occurrences of the preceding element.
- **`?`**: Makes the preceding element optional (0 or 1 occurrence).
- **`{n}`**: Matches exactly `n` occurrences of the preceding element.
- **`{n,}`**: Matches `n` or more occurrences of the preceding element.
- **`{n,m}`**: Matches from `n` to `m` occurrences of the preceding element.

## Special Characters

- **`\`** (Backslash): Used to escape special characters or denote character classes. For example, `\d` matches any digit, and `\\` matches a literal backslash.
- **`\w`**: Matches any word character (equivalent to `[a-zA-Z0-9_]`).
- **`\d`**: Matches any digit (equivalent to `[0-9]`).
- **`\s`**: Matches any whitespace character (spaces, tabs, newlines).

## Assertions

- **`(?=...)`** (Lookahead): A positive lookahead assertion. For example, `X(?=Y)` matches "X" only if "X" is followed by "Y".
- **`(?!...)`** (Negative Lookahead): A negative lookahead assertion. For example, `X(?!Y)` matches "X" only if "X" is not followed by "Y".
- **`(?<=...)`** (Lookbehind): A positive lookbehind assertion. For example, `(?<=Y)X` matches "X" only if "X" is preceded by "Y".
- **`(?<!...)`** (Negative Lookbehind): A negative lookbehind assertion. For example, `(?<!Y)X` matches "X" only if "X" is not preceded by "Y".
- **`(?i)`**: An inline flag for case-insensitive matching.
- **`\g<0>`**: Refers to the entire match. This is useful in replacement strings.

## Using the Explained Symbols in Context

Consider the following regex pattern:

```regex
r'(?<=[a-z0-9])([A-Z])|(?<=[A-Z])([A-Z])(?=[a-z])', r'_\g<0>'
```

This regex pattern is used to convert CamelCase strings to snake_case by inserting underscores before uppercase letters in specific contexts:

- **`(?<=[a-z0-9])([A-Z])`**: Matches an uppercase letter (`[A-Z]`) that directly follows a lowercase letter or digit (`[a-z0-9]`). It uses a lookbehind assertion `(?<=...)` to check for the preceding character without including it in the match.

- **`|`**: Acts as an OR operator, separating two conditions within the pattern.

- **`(?<=[A-Z])([A-Z])(?=[a-z])`**: Matches an uppercase letter that is both preceded by another uppercase letter and followed by a lowercase letter. It combines a lookbehind `(?<=...)` and a lookahead `(?=...)` to ensure the match is positioned between uppercase and lowercase letters.

- **`r'_\g<0>'`**: Specifies the replacement format. `_\g<0>` indicates that an underscore should be inserted before the matched uppercase letter. `\g<0>` refers to the entire match captured by either part of the pattern.

This pattern effectively inserts underscores to transition CamelCase to snake_case, ensuring proper separation of concatenated words within a string.