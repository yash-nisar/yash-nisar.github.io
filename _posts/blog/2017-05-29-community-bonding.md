---
layout: post
title: "GSoC ’17 Post #1: Community bonding ends"
modified:
categories: blog
excerpt: ""
tags: []
image:
  feature:
share: true
date: 2017-05-29
---
## Project abstract
The aim of the project is to ease the process of testing bears in coala by
significantly improving the testing API to yield favorable, easy to understand
results, add support for at least 8 additional useful linter bears, integrate
the MarkdownBear with useful plugins, and enhance documentation to include the
newly written Linter bears.

## What are Linter Bears ?
### Bears in coala
A bear is meant to do some analysis on source code. It can check your code
for potential problems, calculate metrics and even provide corrections for
your code. A bear contains the actual subroutine that is responsible for
checking code for certain specifications.

### Linters
[Linting](https://en.wikipedia.org/wiki/Lint_(software)) is the process of
checking the source code for Programmatic as well as
Stylistic errors. This is most helpful in identifying some common and uncommon
mistakes that are made during coding. A Linter is a program that supports
linting (verifying code quality). They are available for most languages
like JavaScript, CSS, HTML, Python, etc.

### Fusion of the two terminologies
[Linter Bears](http://api.coala.io/en/latest/Developers/Writing_Linter_Bears.html)
are bears that are capable of wrapping third party open source
linters, and to be sustainable even allows you to write custom code analysis
routines, thus extending the modular functionality of coala. You don't have to
go through the hassle of learning how to use various tools for different
programming languages. With over 64 supported languages(and counting), things
get much simpler under a single roof.

## Linter Bears to be implemented
##### [StylintBear](https://github.com/SimenB/stylint)
To catch little mistakes (duplication of rules for instance) and to enforce a
code style guide. This is particularly important with Stylus, which is
unopinionated when it comes to syntax. Like Stylus itself, this linter opts
for flexibility over rigidity.
##### [TextLintBear](https://github.com/textlint/textlint)
`textlint` is an open source text linting utility written in JavaScript for
text and Markdown. It is hard to lint natural language texts, but we try to
resolve this issue by pluggable approach.
##### [TravisLintBear](https://docs.travis-ci.com/user/travis-lint)
Useful for Validating your `.travis.yml` file before committing it reduces
common build errors such as
* invalid YAML
* missing `language` key
* unsupported runtime versions of Ruby, PHP, OTP, etc
* deprecated features or runtime aliases

##### [PugLintBear](https://github.com/pugjs/pug-lint)
An unopinionated and configurable linter and style checker for
Pug (formerly Jade).
##### [AstyleBear](http://astyle.sourceforge.net/)
Artistic Style is a source code indenter, formatter, and beautifier for
the C, C++, C++/CLI, Objective‑C, C# and Java programming languages. A filter
written in C++ that automatically re-indents and re-formats C / C++ /
Objective‑C / C++/CLI / C# / Java source files. It can be used from a
command line, or it can be incorporated as a library in another program.
##### [ReekBear](https://github.com/troessner/reek)
Reek is a tool that examines Ruby classes, modules and methods and reports any
Code Smells it finds. Reek focuses on high-level code smells, so we can't tell
you how to fix warnings in a generic fashion; this is and will always be
completely dependent on your domain language and business logic.
##### [CSSCombBear](https://github.com/csscomb/csscomb.js)
CSScomb is a coding style formatter for CSS. You can easily write your own
configuration to make your style sheets beautiful and consistent.
##### [HttpoliceBear](https://github.com/vfaronov/httpolice)
HTTPolice is a lint for HTTP requests and responses. It checks them for
conformance to standards and best practices. As a command-line tool, it can
read HAR files or raw HTTP/1.x TCP streams.

### Conclusion
The community bonding has come to an end and I've nearly managed to complete
my milestone. It has been a wonderful time so far. I've manually installed and
tested all the linters that I'm going to integrate and went through their
configurations. I've also designed the modified testing API yielding useful
results which will be described in the upcoming blog. Till then, let the
coding begin !
