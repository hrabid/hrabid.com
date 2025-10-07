# Markdown Tutorial

Markdown is a lightweight markup language that you can use to add formatting elements to plaintext text documents. Created by John Gruber in 2004, Markdown is now one of the world’s most popular markup languages. It is widely used for formatting readme files, writing messages in online discussion forums, and creating rich text using a plain text editor.

This tutorial will cover everything you need to know about Markdown, from basic syntax to advanced features. Let's dive in!

---
## Basic Syntax

### Headings

Headings are created by adding one or more `#` symbols before the heading text. The number of `#` symbols corresponds to the heading level.

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

### Paragraphs and Line Breaks

To create a paragraph, leave a blank line between lines of text. To create a line break, end a line with two or more spaces.

```markdown
This is a paragraph.

This is another paragraph.  
This is a new line in the same paragraph.
```

### Bold and Italic

- **Bold**: Wrap text with `**` or `__`.
- *Italic*: Wrap text with `*` or `_`.

```markdown
**This is bold text**  
__This is also bold text__  

*This is italic text*  
_This is also italic text_  

**_This is bold and italic text_**
```

### Blockquotes

Blockquotes are created by adding a `>` before the text.

```markdown
> This is a blockquote.
> 
> This is another line in the blockquote.
```

### Lists

#### Unordered Lists

Use `-`, `*`, or `+` to create unordered lists.

```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
* Item 3
+ Item 4
```

#### Ordered Lists

Use numbers followed by a period to create ordered lists.

```markdown
8. First item
9. Second item
   10. Subitem 2.1
   11. Subitem 2.2
12. Third item
```

### Code

- Inline code: Wrap text with `` ` ``.
- Code blocks: Wrap text with ``` ``` ``` or indent with four spaces.

```markdown
This is `inline code`.

```
This is a code block.
```markdown

	This is also a code block.
```

### Horizontal Rules

Create a horizontal rule by using three or more `-`, `*`, or `_` characters.

```markdown
---
***
___
```

### Links

Create links using `[text](URL)`.

```markdown
[Google](https://www.google.com)
```

### Images

Add images using `![alt text](image URL)`.

```markdown
![Markdown Logo](https://markdown-here.com/img/icon256.png)
```

---

## Extended Syntax

### Tables

Create tables using `|` and `-`.

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Data 1   | Data 2   |
| Row 2    | Data 3   | Data 4   |
```

### Task Lists

Create task lists using `- [ ]` for incomplete tasks and `- [x]` for completed tasks.

```markdown
- [x] Task 1
- [ ] Task 2
- [ ] Task 3
```

### Strikethrough

Wrap text with `~~` to create strikethrough text.

```markdown
~~This is strikethrough text.~~
```

### Emoji

Use `:emoji_name:` to add emojis.

```markdown
:smile: :heart: :rocket:
```

>[!caution]
>Some editor may not render this syntax

### Footnotes

Add footnotes using `[^label]` and define them at the bottom of the document.

```markdown
Here is a footnote reference[^1].

[^1]: This is the footnote.
```

### Highlighting

Wrap text with `==` to highlight it.

```markdown
This is ==highlighted text==.
```

### Subscript and Superscript

- Subscript: Wrap text with `~`.
- Superscript: Wrap text with `^`.

```markdown
H~2~O  
E = mc^2^
```

### Expandable & Collapsible Sections
```markdown
<details>
  <summary>Click to expand</summary>

  Hidden content goes here.
</details>
```

---
## GFM (Github Flavoured Markdown)
### Note 
```markdown
> [!Note]
> A Note
```
### Caution 
```markdown
> [!Caution]
> This is a caution
```
### Tip
```markdown
> [!Tip]
> This is a Tip
```
### Important 
```markdown
> [!Important]
> This is a important note 
```

---

## Markdown Editors and Tools

Here are some popular Markdown editors and tools:

- **Visual Studio Code**: A powerful code editor with Markdown support.
- **Typora**: A minimalistic Markdown editor with live preview.
- **Markdown Here**: A browser extension for writing Markdown in emails.
- **Dillinger**: An online Markdown editor.
- **Pandoc**: A universal document converter that supports Markdown.

---

## Best Practices

11. **Keep It Simple**: Use Markdown for its simplicity. Avoid overcomplicating your documents.
12. **Use Consistent Formatting**: Stick to one style for headings, lists, and other elements.
13. **Preview Your Work**: Always preview your Markdown to ensure it renders correctly.
14. **Use Comments Sparingly**: Markdown doesn’t support comments, but some processors allow HTML comments (`<!-- comment -->`).
15. **Organize Your Content**: Use headings, lists, and horizontal rules to structure your document.
