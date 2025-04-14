# Email Address Parsing Using Regex

```python
def is_valid_email(email_address):
    # Regular expression pattern for email validation with the specific criteria:
    # - Username starts with an English letter and can contain alphanumeric chars, -, ., _
    # - Domain contains only English letters
    # - Extension contains only English letters and is 1-3 characters long
    pattern = r'^[a-zA-Z][\w\-\.]*@[a-zA-Z]+\.[a-zA-Z]{1,3}$'
    return bool(re.match(pattern, email_address))
```

### Each component of the regex statement

- `^` is the start of the string
- `[a-zA-Z][\w\-\.]*` - checks if the start of the string begins with an alphanumeric, and then everythign afterwards can be alphanumeric as well including `-`, `.`, `_`
- `@` - Just the at sign
- `[a-zA-Z]` ensures domain is english letters
- `\.` literal period
- `[a-zA-Z]{1,3}` - The extension has english letters and is 1-3 letters long
- `$` end of the string

### Resources / Games to Refer to
- [RegexOne](https://regexone.com/)
- [Regex Crossword](https://regexcrossword.com/)