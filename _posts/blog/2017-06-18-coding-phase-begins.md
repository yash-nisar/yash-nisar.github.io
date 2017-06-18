---
layout: post
title: "GSoC ’17 Post #3: Unleashing the power of a debugger"
modified:
categories: blog
excerpt: ""
tags: []
image:
  feature:
share: true
date: 2017-06-18
---
## Phase 1: Coding begins
<figure>
<img src="/images/timeline.png">
</figure>

The community bonding is over and the coding period has finally begun. People
have geared up, configured their terminals, development environments and are
ready to utilize the summer in a fruitful manner.

## What I've done so far ?
I've planned to divide the first phase in 2 parts where the first part would
focus on the implementation of bears and the second part on the enhancement
of the testing API.

### Implementation of StylintBear
Attempts to catch little mistakes (duplication of rules for instance) and
enforces a code style guide on Stylus (a dynamic stylesheet language
with the ``.styl`` extension that is compiled into CSS) files.
The ``StylintBear`` is able to catch following problems:
- Duplication of rules
- Mixed spaces and tabs
- Unnecessary brackets
- Missing colon between property and value
- Naming conventions
- Trailing whitespace
- Consistent quotation style
- Use of extra spaces inside parenthesis
- Naming convention when declaring classes, ids, and variables
- Unnecessary leading zeroes on decimal points
- Checks if a property is valid CSS or HTML

### Implementation of TextLintBear
The pluggable linting tool for text and Markdown. It is similar to ``ESLint``,
but covers natural language instead. A wide variety of rules and plugins have
been added in accordance with the bear and we now have extra language
support for :
- HTML
- reStructuredText
- AsciiDoc/Asciidoctor
- Re:VIEW

### Challenges that I had to face
One of the main features that I want to incorporate is to improve the way we
test our bears. Since the current testing API does not yield favourable results,
I had to rely on the Pycharm debugger to extract the expected results. To all
the bear writers out there, here's how you can do that
([Pycharm](https://www.jetbrains.com/pycharm/) specific) :

- Configure your 'Script', 'Script Parameters' and 'Python interpreter' under
`Edit Configurations...`.

<figure>
<img src="/images/edit_configurations.png">
</figure>

- Set breakpoints according to the line you wanna pause execution on and start
debugging.

<figure>
<img src="/images/explore_variables.png">
</figure>

- There is a lot more you can do like stepping into the code,
inspecting variables, investigating the stack, managing breakpoints, etc.

Another obstacle that I had to clear was the [docker](https://www.docker.com/)
breakage. The docker broken from over a month. A thorough research was required
to hunt down the cause and submit patches relating to those bugs. I found a
quick fix, leading to the tree turning green again and fortunately, both of my
bears passed the tests. Apart from those, I also initiated a couple of upstream
contributions and a patch escalating the performance of the ``RubocopBear``.

## What lies ahead ?
We're pretty much on track and you can follow my progress from the burndown
chart given below :

<figure>
<img src="/images/burndown_chart_phase_1.png">
</figure>

I've started working on the testing API and I'm likely to send a Pull
Request by tomorrow. The first evaluation has hardly a few days left all the
milestones need to be achieved in time. Peace.

> “ Debugging is twice as hard as writing the code in the first place.
Therefore, if you write the code as cleverly as possible, you are,
by definition, not smart enough to debug it. ” – Brian Kernighan
