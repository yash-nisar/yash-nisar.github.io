---
layout: post
title: "GSoC ’17 Post #2: Enhancing the coala testing API"
modified:
categories: blog
excerpt: ""
tags: []
image:
  feature:
share: true
date: 2017-06-01
---
## About the bear testing framework
coala has a wonderful testing API that can be used to write tests for bears
with ease. Software testing is a process of executing a program or application
with the intent of finding software bugs, preventing them from entering your
codebase, and making sure that everything works as expected.

coala supports 3 documented methods for testing bears, namely :
* `check_validity(...)`

  `check_validity` asserts if your bear yields any results for a particular
  check with a list of strings.
* `check_results(...)`

  `check_results` asserts if your bear results match the actual results on
  execution on the command line interface.
* `verify_local_bears(...)`

  `verify_local_bear` asserts that a check of the given lines with the given
  local bear either yields or does not yield any results.

The tests should have 100% coverage and zero redundancy and it is advised to use
`check_results` since developers can verify the bear output and any upstream
changes can easily be caught via the given method.
## The Problem
### Overview
The current
[testing API](http://api.coala.io/en/latest/Developers/Writing_Tests.html)
doesn’t provide useful results as a traceback if a given test fails. It becomes
a strenuous and a time consuming job to follow the traceback searching
for errors.

Eg. For the `check_results(...)` method, I received a strange output when I had
a minor difference of `line=5` instead of `line=6` in the given code snippet :

```
[Result.from_values('ElmLintBear',
                     message=result_message_bad_function,
                     file=fname,
                     line=5,
                     severity=RESULT_SEVERITY.NORMAL)]
```
The given output below appear to be strange as both the Result objects contain
the same number of characters (632) due to which testing transforms to a
challenging task. Hit and trial methods or the usage of a debugger are the
only possible ways to overcome these bugs.
```
E           AssertionError: Lists differ: [<Result object(id=0xce0383d576a84f34848d66d0ddc87479, origin=[632 chars]710>] != [<Result object(id=0x7e58527926a345f8a2bb36305c58f9f6, origin=[632 chars]400>]
E           
E           First differing element 0:
E           <Result object(id=0xce0383d576a84f34848d66d0ddc87479, origin=[631 chars]0710>
E           <Result object(id=0x7e58527926a345f8a2bb36305c58f9f6, origin=[631 chars]0400>
E           
E           Diff is 2804 characters long. Set self.maxDiff to None to see it. : The local bear 'ElmLintBear' doesn't yield the right results. Or the order may be wrong.
E           Running bear ElmLintBear...
E           Running 'elm-format /tmp/tmpzu0n4474 --yes'
```

### Analysis
The ugly message is generated due to the `check_results(...)` method of the
`LocalBearTestHelper` class. The following code snippet is responsible for the
origin of the bug :
```
if not check_order:
   self.assertEqual(sorted(bear_output), sorted(results), msg=msg)
else:
   self.assertEqual(bear_output, results, msg=msg)
```
The expected (ie. `bear_output`) and observed (ie. `results`) Result objects
are compared by the `assertEqual(...)` method, which on finding an inequality
yields a bewildering message on the console.

## Proposed Solution
The idea is to compare all fields of the Result object, one at a time, and
complain accordingly for dissimilarity of values. Once `assertEqual()` fails,
the attribute mismatch can be precisely and explicitly mentioned.  The following
can be achieved by annotating every class that uses `@generate_eq(...)` or
`@generate_ordering(...)` with a special field (eg. `__compare_fields__`) which
contains the fields of the Result object that we use for comparison.
```
cls.__comparable_fields__ = tuple(member for member in members)
```
We then write a generic assertion function detecting this field and apply the
principle of comparing them in a dynamic manner with less code duplication.
```
def assertFieldsEqual(self, object1, object2):
   attributes = Result.__comparable_fields__
   for attribute in attributes:
       self.assertEqual(getattr(object1[0], attribute), getattr(object2[0], attribute), msg='{} mismatch'.format(attribute))
```
After registering this function as an `assertEqual` function, we call the above
function implicitly.

The sample output in case of an origin mismatch would look like :
```
E   AssertionError: 'StylintBear' != 'StylintBea'
E   - StylintBear
E   ?           -
E   + StylintBea
E    : origin mismatch
```
The above message is field specific and quite helpful and will prevent bear
writers from scratching their heads and applying trial and error techniques to
get their tests passed.

Another sample output containing a message_base mismatch would look like :
```
E   AssertionError: 'prefer alphabetical when sorting properties  sortOrder' != 'prefer alphabetical when sorting properties'
E   - prefer alphabetical when sorting properties  sortOrder
E   ?                                            -----------
E   + prefer alphabetical when sorting properties
E    : message_base mismatch
```
## Conclusion
The coding phase has begun, work is going on in full swing and I'm thankful
my mentor [@Makman2](https://github.com/Makman2) for dropping in subtle hints
whenever I seem to get stuck. We're enjoying so far and lets see what the first
coding phase brings for us. I'll keep things updated on my blog so stick around.

> " Invariably, you’ll find that if the language is any good, your users are
going to take it to places where you never thought it would be taken. " –
Guido Van Rossum, creator of Python
