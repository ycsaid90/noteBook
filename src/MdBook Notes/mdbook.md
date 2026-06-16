# How to create a Book

## Install mdbook
```bash
cargo install mdbook
```
## Create a new book
```bash
mdbook init my-book
```
## Build the book
```bash
cd my-book
mdbook build
```
## Serve the book
```bash
mdbook serve
```

## Add a mdbook picture
```markdown
![ProfileImage](images/image.jpg)
![ProfileImage]<img src="../images/1765899302483.jpg" alt="Yadira Photo" width="300">
```

## Summary
The `SUMMARY.md` file is used to define the structure of the book. It is a markdown file that contains a list of links to the chapters and sections of the book. The links should be in the format `[Chapter Title](path/to/chapter.md)`. The `SUMMARY.md` file should be located in the root directory of the book.

## Customization
You can customize the appearance of your book by creating a `book.toml` file in the root directory of the book. This file allows you to specify various settings such as the title, author, theme, and more. For example:
```toml
[book]
title = "My Awesome Book"
author = "Yadira Cardoso Said"
theme = "light"
```
You can also create custom themes by creating a `theme` directory in the root of your book and adding your CSS files there. You can then specify your custom theme in the `book.toml` file.

## Conclusion
MdBook is a powerful tool for creating documentation and books in markdown format.
It provides a simple way to organize your content and generate a static website for your book.
With its simple command-line interface, you can quickly build and serve your book locally for testing and sharing.
Whether you're writing technical documentation, a tutorial, or a full-fledged book, MdBook can help you create a professional-looking and well-structured output with ease.
[Official Guide](https://rust-lang.github.io/mdBook/guide/creating.html)

