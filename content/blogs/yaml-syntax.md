---
title: "YAML, The Lingua Franca of IT Infrastructure"
date: 2025-10-08
draft: false
tags: ["YAML", "config", "devops", "tutorial", "serialization"]
summary: "Learn YAML from basics to advanced: syntax, anchors, tags, schemas, best practices, examples in Python/Go, and common pitfalls."
author: "Habibur Rahman"
image: /blogs/yaml.png
---
# YAML
YAML (YAML Ain't Markup Language) is a human-friendly data serialization format commonly used for configuration files, data exchange, and templating.

## YAML Syntax
YAML is indentation-significant (uses **spaces** — never **tabs**).
> [!Note]
> YAML is superset of JSON (Javascript Object Notation). That means any valid JSON file is a valid YAML file.

### Indentation, whitespace & Comments
- `yaml` is indentation-significant, so being consistent with indentation is important. Use **space** not **tab**(tabs are forbidden in yaml).
- Using 02 spaces is a populer convention, some project use 4 spaces, but we have to be consistent.
- Comments starts with a `#` sign & ends with the line. Comments can be anywhere in a yaml file
```yaml
# top-level comment
key: value # inline comment
```
- Blank lines are allowed & actually helpful for readability.

### Scalers: `string`, `number`, `boolean`, `null`
Scalars are simple Values like strings, numbers, boolean, null etc.
```yaml
string_unquoted: hello
string_quoted: "hello world"
int: 42
float: 3.14
bool_true: true
bool_false: false
null_val: null
empty_val: ""
```
Notes: 
- Booleans: Supports `true | false`, `yes | no`, `on | off` -- but prefers `true | false` for clarity
- Null: `null` or `~` or an empty after colon (:)
Quoting:
- Double Quotes `"` allows escape sequences like `\t`, `\n` & other Unicode escapes.
- Single Quotes `'` treats texts literally (no escape). It's useful when string contains a quote or escape sequences.
Example with new line:
```yaml
double_quoted: "Line1\nLine2"  # creates a new line
single_quoted: 'Line1\nLine2'  # includes backslash-n literally
```
Literal block scalar (`|`) and folded block scalar (`>`) for multi-line strings:
```yaml
literal: |
  This text preserves
  line breaks exactly.

folded: >
  This text will
  be folded to a single
  paragraph with newlines converted to spaces.
```

### Collections: Mappings & Sequences
**Mappings** (key: value) and **sequences** (dash `-`) are the main composite types.

Block style (most common):
```yaml
person:
  name: "Sam"
    roles:
      - developer
      - maintainer
```
Flow Style(inline):
```yaml
person: { name: "Sam", roles: ["developer", "maintainer"] }
```
- **Block style** is recommended for readability (indentation).
- **Flow style** uses JSON-like `{}` and `[]` for compactness.

Mixed Nested Example:
```yaml
teams:
  - name: "Alpha"
        members:
          - name: "Lee"
            id: 1
          - name: "Maya"
            id: 2
      - name: "Beta"
        members: []
```

Tags, types, and custom type hints

YAML supports tags to indicate a type or custom constructor. Standard tags include `!!str`, `!!int`, `!!map`, etc.
```yaml
explicit_str: !!str 145 
explicit_int: !!int "15667"
explicit_num_with_comma: !!int +545_000 # 545,000
float: !!float 15.377
boolean: !!bool true # yes,no | on,off | 
infinite: !!float .inf 
not_a_num: .nan
null_value: !!null Null # or null, NULL, ~
~: wth # a null key
```

#### Multi-document files and streaming YAML 
YAML can contain multiple documents separated by `---` and end with `...` (optional).
```yaml
---
name: doc1
value: 1
---
name: doc2
value: 2
...
```

### Anchors, aliases, and merge keys
Anchors (`&`) let you name a node; aliases (`*`) reuse it. Merge keys (`<<`) let you merge mappings.
Example: reuse repeated config bits
```yaml
defaults: &defaults
  timeout: 30
    retries: 3

serviceA:
  <<: *defaults
  url: "https://a.example.com"

serviceB:
  <<: *defaults
  url: "https://b.example.com"
  retries: 5  # override
```
Result: `serviceA` and `serviceB` inherit `timeout` and `retries` from `defaults`.

Caveat: Complex anchor/alias structures can be confusing and harder to edit; use judiciously.

## YAML tools 
You can find so many online converter & validators out there. My personal recommendation is to use `yamllint`. Install it using `pip` or package manager of your choice. or just install by running this command:
```bash
pip install yamllint
```

## Security considerations (very important)

- **Do not** load untrusted YAML with unsafe loaders that allow arbitrary object instantiation or code execution. Example: `yaml.load()` in PyYAML older versions can instantiate arbitrary Python objects. Prefer `safe_load`.
- Anchors and aliases are generally safe, but extremely nested or recursive structures can cause denial-of-service (excessive memory/cpu).
- Avoid custom tags unless you fully control the data producer and consumer.
- Validate config schema before use. Use JSON Schema (via converters) or a dedicated validator library.

## Best practices and style guide

1. **Consistent indentation** — pick 2 or 4 spaces; never mix; never use tabs.
2. **Prefer explicit booleans** (`true`/`false`) instead of `on`/`off` or `yes`/`no`.
3. **Quote when necessary** — strings that start with special characters (like `:`, `*`, `&`, `{`, `}`, `@`, or contain `#`) are safer quoted.
4. **Prefer block style for readability**.
5. **Use anchors sparingly** — they’re powerful but can reduce readability.
6. **Validate** — add schema validation (JSON Schema, custom validators).
7. **Include comments** to explain non-obvious values.
8. **Avoid multi-line folded strings where exact formatting matters**; use literal (`|`) if you need exact newlines.
9. **Use `safe_load`/`safeDump`** when available in your libraries.
10. **Add examples and templates** in your repo for newcomers.

## Cheat Sheet — Quick Reference 
```yaml
# Basic
key: value
list:
  - one
    - two

# Scalars
str: "quotes optional"
int: 10
float: 3.14
bool: true
null: ~

# Multi-line
literal: |
  line1
  line2

folded: >
  this becomes a single paragraph

# Anchor & alias
defaults: &defaults
  a: 1
service:
  <<: *defaults
  b: 2

# Multi-doc
---
doc1: 1
---
doc2: 2
...
```




