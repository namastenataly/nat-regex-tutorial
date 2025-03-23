# Matching a URL with Regex

Regular expressions (regex) can be a powerful tool for validating and extracting text patterns like URLs. In this tutorial, we'll break down how to match a URL using regex. You'll learn how to construct the pattern, understand its components, and apply it in real-world scenarios.

## Summary

In this tutorial, we’ll build a regex pattern that matches common URL formats like `https://www.example.com`, `http://example.com/page`, `www.example.org`, and `example.net`.

Here's the final regex we’ll explore:

```regex
^(https?:\/\/)?(www\.)?[a-zA-Z0-9\-]+\.[a-z]{2,}(\/\S*)?$
```

We’ll break it down and explain each component using regex concepts like anchors, quantifiers, character classes, and more.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

```regex
^ ... $
```
- `^` asserts the start of the line.
- `$` asserts the end of the line.
- Ensures the entire string must match the pattern, not just part of it.

---

### Quantifiers

```regex
s?   -> matches zero or one "s" character  
+    -> matches one or more of the preceding token  
{2,} -> matches at least two characters (used in TLDs)
```

Used in:
```regex
https?    // optional "s"
[a-z]{2,} // TLDs like .com, .org, .io, etc.
```

---

### OR Operator

In this case, we use optional groups rather than explicit OR `|`, but an equivalent OR pattern could be:
```regex
(http|https)
```
However, we simplify it using `s?`:
```regex
https?
```

---

### Character Classes

```regex
[a-zA-Z0-9\-]
```
- Matches any letter (uppercase/lowercase), digit, or hyphen.
- Used for domain names.

```regex
\S
```
- Matches any non-whitespace character.
- Used in path matching: `/\S*`

---

### Flags

In many regex engines, we can add the `i` flag to make the pattern case-insensitive:

```regex
/^(https?:\/\/)?(www\.)?[a-zA-Z0-9\-]+\.[a-z]{2,}(\/\S*)?$/i
```

---

### Grouping and Capturing

```regex
(https?:\/\/)?     // Optional protocol
(www\.)?           // Optional www.
(\/\S*)?           // Optional path
```

- Parentheses `()` are used for grouping.
- `?` makes each group optional.

---

### Bracket Expressions

```regex
[a-zA-Z0-9\-]
```

- Square brackets `[]` define a set of allowed characters.
- Hyphen `-` inside brackets means a range.
- `\.` is used to match a literal dot.

---

### Greedy and Lazy Match

This regex uses greedy matching by default:
```regex
\S*  // matches as many non-whitespace characters as possible
```

We’re not using lazy quantifiers (`*?`, `+?`) here because we want to capture the entire path.

---

### Boundaries

We don't use `\b` word boundaries in this pattern, but we use `^` and `$` as full string boundaries instead.

---

### Back-references

Back-references (like `\1`) are not used in this pattern, but they are useful when you want to match repeated groups. For example:
```regex
(<div>).*?\1
```

---

### Look-ahead and Look-behind

This pattern doesn’t use lookaheads or lookbehinds, but here’s a quick note:

- **Lookahead**: `(?=...)` — Asserts that what follows matches.
- **Lookbehind**: `(?<=...)` — Asserts that what precedes matches.

Example (not used here):
```regex
(?<=@)\w+       // Matches a word following '@'
```

---

## Author

Created by Nataly Gonzalez, a full stack developer in the making.  
Want more regex tutorials or want to contribute? Reach out on GitHub!

