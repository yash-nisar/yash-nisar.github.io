---
layout: post
title: "GSoC ’17 Post #6: The journey ends"
modified:
categories: blog
excerpt: ""
tags: []
image:
  feature:
share: true
date: 2017-08-24
---
The coding period is over and this blog post summarizes the work done by me
during the short span of 2 months(June 1 - August 23). I would like to express
my gratitude to [coala](https://coala.io/#/home) for giving me the opportunity
to work on this project and my mentor [@Makman2](https://github.com/Makman2).
A big shoutout to Google for promoting the OSS (Open Source Software) culture.

The coolest part was that I could actually run the [InvalidLinkBear](https://github.com/coala/coala-bears/blob/master/bears/general/InvalidLinkBear.py)
to make sure that all the links were working.
## Work Summary

The milestones achieved were :
1. [Community Bonding](https://gitlab.com/coala/GSoC-2017/milestones/12)
* Designing the new testing API yielding useful results
* Trying out all the linters manually
* Updating the [projects](https://projects.coala.io/) page
2. [Phase 1](https://gitlab.com/coala/GSoC-2017/milestones/13)
* Add doctests for `generate_ordering`
* Add abstract base class to group classes annotated with `generate_eq` or `generate_ordering`
* Performance improvement for `RubocopBear`
* Annotate objects implementing `generate_eq` or `generate_ordering` with a new field
* Fix docker image
* Implementation of the `StylintBear`
* Implementation of settings for the `StylintBear` supported from the coala side
* A basic merge supporting a config file for stylint
* Add `stylint` to docker
* Implementation of the `TextLintBear`
* Add textlint to docker
* Complete the implementation of the testing API yielding useful results
3. [Phase 2](https://gitlab.com/coala/GSoC-2017/milestones/14)
* MarkdownBear: Use `remark-lint` to report useful messages
* MarkdownBear: Add `remark-validate-links` plugin
* MarkdownBear: Replace `markdown_horizontal_rule`
* Implementation of the `TravisLintBear`
* Implementation of the `PugLintBear`
* Implementation of the `ArtisticStyleBear`
* Add all the bears implemented during PHASE 2 to docker
* Design and implement the testing API to yield stderr and stdout
* execute_bear: Improve AssertionError message generation
* LocalBearTestHelper: Remove `check_order=False` from `check_line_result_count`
* Fix breakage for rubocop version > 0.47.1
4. [Phase 3](https://gitlab.com/coala/GSoC-2017/milestones/15)
* Remove `pragma: no cover` from `ElmLintBear`
* TravisLintBear: Check for internet connection
* Fix unexpected keyword argument in `new_process_output(...)`
* Introduce virtual base class for linters and use it to improve the check inside `LocalBearTestHelper`
* Implementation of the `HttpoliceBear`
* Implementation of the `CSSCombBear`
* Implementation of the `HTMLHintBear`
* Add all the bears implemented during PHASE 3 to docker

* Conceptually, [this milestone](https://gitlab.com/coala/GSoC-2017/milestones/43)
turned out to be quite difficult, but basic improvement for that topic has been
approved. (See [this issue](https://gitlab.com/coala/GSoC-2017/issues/104)).


### Repository : coala-bears

|                          Issue reference                         |                       Pull Request                       |                  Commit  shortlog                 |                                                 Commit hash                                                | Status |
|:----------------------------------------------------------------:|:--------------------------------------------------------:|:-------------------------------------------------:|:----------------------------------------------------------------------------------------------------------:|:------:|
| [#754](https://github.com/coala/coala-bears/issues/754)           |  [#1610](https://github.com/coala/coala-bears/pull/1610) | bears/stylus: Add StylintBear                     | [47d3956](https://github.com/coala/coala-bears/commit/47d3956949d62d9489c3c3e4bf7add761e6e385f)            | Merged |
| [#1795](https://github.com/coala/coala-bears/issues/1795) | [#1796](https://github.com/coala/coala-bears/pull/1796) | StylintBear: Implement settings                   | [e4a9d34](https://github.com/coala/coala-bears/commit/e4a9d34dadd344244ef8aafd44172c02e72d010c)            | Merged |
| [#1839](https://github.com/coala/coala-bears/issues/1839) |  [#1841](https://github.com/coala/coala-bears/pull/1841) | RubocopBear: Optional generation of `config_file` | [45dfb62](https://github.com/coala/coala-bears/commit/45dfb6269825eaa1ddcac417a082865bee327bb1)            | Merged |
| [#1576](https://github.com/coala/coala-bears/issues/1576) | [#1597](https://github.com/coala/coala-bears/pull/1597)  | bears/general: Add TextLintBear                   | [d09c8f9](https://github.com/coala/coala-bears/commit/d09c8f9f1f58ac39491caa2c36019067948bcf97) | Merged |
| [#294](https://github.com/coala/coala-bears/issues/294)   | [#1879](https://github.com/coala/coala-bears/pull/1879)  | bears/yaml: Add TravisLintBear                    | [2f004bc](https://github.com/coala/coala-bears/commit/2f004bc082178450515886c66a547e524d2c6b20)            | Merged |
| [#1548](https://github.com/coala/coala-bears/issues/1548)        | [#1890](https://github.com/coala/coala-bears/pull/1890)  | RuboCopBear: Fix CI breakage for version > 0.47.1 | [d35b120](https://github.com/coala/coala-bears/commit/d35b12074bfb0df280cdcbabd1c0acf64470729b)            | Merged |
| [#1907](https://github.com/coala/coala-bears/issues/1907)        | [#1908](https://github.com/coala/coala-bears/pull/1908)  | MarkdownBear: Replace `markdown_horizontal_rule`  | [e2cf115](https://github.com/coala/coala-bears/commit/e2cf115e41c306ac97a55f70c2080751d920ce2c)            | Merged |
| [#924](https://github.com/coala/coala-bears/issues/924)          | [#1919](https://github.com/coala/coala-bears/pull/1919)  | MarkdownBear: Add `validate-links` plugin         | [f68bd91](https://github.com/coala/coala-bears/commit/f68bd91a820293a1c6d376a58a7f60228c33fa3a)            | Merged |
| -                                                                | [#1919](https://github.com/coala/coala-bears/pull/1919)  | MarkdownBear: Rename test classname               | [2a21048](https://github.com/coala/coala-bears/commit/2a21048d5b517d5462cce337a83720a71e16017e)            | Merged |
| -                                                                | [#1919](https://github.com/coala/coala-bears/pull/1919)  | MarkdownBear: Rename `remark_configs_plugins`     | [d83fe5f](https://github.com/coala/coala-bears/commit/d83fe5fb86df425c8afb563c3ab75e87c92d2eb5)            | Merged |
| -                                                                | [#1919](https://github.com/coala/coala-bears/pull/1919)  | MarkdownBear: Improve result message              | [71f6bc5](https://github.com/coala/coala-bears/commit/71f6bc543160f280b96a3eeb0a76c60237893922)            | Merged |
| -                                                                | [#1919](https://github.com/coala/coala-bears/pull/1919)  | MarkdownBear: Rename `remark_configs_settings`    | [d6100ce](https://github.com/coala/coala-bears/commit/d6100ce9c519ad7c314a4323f24e9aa2832aefc9)            | Merged |
| [#290](https://github.com/coala/coala-bears/issues/290)          | [#1936](https://github.com/coala/coala-bears/pull/1936)  | bears/pug: Add PugLintBear                        | [1d31827](https://github.com/coala/coala-bears/commit/1d3182700dc80785ba7be703f439540c156134fc)            | Merged |
| [#388](https://github.com/coala/coala-bears/issues/388)          | [#1882](https://github.com/coala/coala-bears/pull/1882)  | bears/c_languages: Add ArtisticStyleBear          | [65d6304](https://github.com/coala/coala-bears/commit/65d63043ce61ac1637d9b7df9a9682eac1973eda)            | Merged |
| [#926](https://github.com/coala/coala-bears/issues/926)          | [#1942](https://github.com/coala/coala-bears/pull/1942)  | MarkdownBear: Add `remark-lint` settings          | [3dc08bf](https://github.com/coala/coala-bears/commit/3dc08bfceb4d2e91bb8b198bdaa63d3fde06566b)            | Merged |
| -                                                                | [#1958](https://github.com/coala/coala-bears/pull/1958)                                                        | requirements.txt: Update coala                    | [04f490c](https://github.com/coala/coala-bears/commit/04f490c1ab062e3bc9a2e61c7a3bfcaa58f56098)            | Merged |
| [#634](https://github.com/coala/coala-bears/issues/634)          | [#1957](https://github.com/coala/coala-bears/pull/1957)  | bears/css: Add CSSCombBear                        | [2bef3df](https://github.com/coala/coala-bears/commit/2bef3dfe1f8c1f32b02de0b4584568bdbaa49679)            | Merged |
| [#596](https://github.com/coala/coala-bears/issues/596)          | [#1962](https://github.com/coala/coala-bears/pull/1962)  | bears/hypertext: Add HTTPoliceLintBear.py         | [40dd5d4](https://github.com/coala/coala-bears/commit/40dd5d4c14b32140314df19f5b52d14cb03e7c84)            | Merged |
| [#635](https://github.com/coala/coala-bears/issues/635)          | [#1987](https://github.com/coala/coala-bears/pull/1987)  | bears/hypertext: Add HTMLHintBear                 | [b49553a](https://github.com/coala/coala-bears/commit/b49553a8d62cae9989d0778728adb09fecb7fffb)            | Merged |
| [#1996](https://github.com/coala/coala-bears/issues/1996)        | [#1997](https://github.com/coala/coala-bears/pull/1997)  | ElmLintBear: Remove `pragma: no cover`            | [0a25352](https://github.com/coala/coala-bears/commit/0a25352953ee2b3d91e1350d50153e495fc203f2)            | Merged |
| [#1978](https://github.com/coala/coala-bears/issues/1978)  | [#1982](https://github.com/coala/coala-bears/pull/1982)  | TravisLintBear: Check for internet connection     | [f51e54d](https://github.com/coala/coala-bears/commit/f51e54d11477f38364830f568fad969960a81972)            | Merged |
{: .table}

### Repository : coala

| Issue reference                                         |                    Pull Request                   |                                  Commit shortlog | Commit hash                                                                                          | Status   |
|---------------------------------------------------------|:-------------------------------------------------:|-------------------------------------------------:|------------------------------------------------------------------------------------------------------|----------|
| [#4418](https://github.com/coala/coala/issues/4418)     | [#4417](https://github.com/coala/coala/pull/4417) | execute_bear: Improve ``AssertionError`` message | [0edf040](https://github.com/coala/coala/commit/0edf04029b60877395c34b9c22599423df165e55)            | Merged   |
| [#4451](https://github.com/coala/coala/issues/4451)     | [#4453](https://github.com/coala/coala/pull/4453) |        LocalBearTestHelper: Remove `check_order` | [0aa077](https://github.com/coala/coala/commit/0aa07774b4dcb8a62808fa095c42ff8592584efb)             | Merged   |
| [#455](https://github.com/coala/coala-bears/issues/455) | [#4554](https://github.com/coala/coala/pull/4554) |      Show `stdout` and `stderr` for linter bears | [bbb99f9](https://github.com/coala/coala/commit/bbb99f95cd2c5530bae765b2b011e76d85d639b4)            | Merged   |
| [#4576](https://github.com/coala/coala/issues/4576)     | [#4579](https://github.com/coala/coala/pull/4579) | LocalBearTestHelper: Add **process_output_kwargs | [2868324](https://github.com/coala/coala/commit/28683248ee6230130a2dce259a046a8576d7982c)            | Merged   |
| [#4594](https://github.com/coala/coala/issues/4594)     | [#4595](https://github.com/coala/coala/pull/4595) | coalib/abstractions: Add LinterClass.py          | [9f279e4](https://github.com/coala/coala/commit/9f279e47d2be8790d47dae3ec321503682f79095)            | Merged   |
| [#4594](https://github.com/coala/coala/issues/4594)     | [#4595](https://github.com/coala/coala/pull/4595) | Introduce `isinstance(cls, LinterClass)`         | [2816dc6](https://github.com/coala/coala/commit/2816dc6888b7ab27e60f721254f7085ee1020c62)            | Merged   |
| [#4302](https://github.com/coala/coala/issues/4302)     | [#4310](https://github.com/coala/coala/pull/4310) | LocalBearTestHelper: Add ``assertObjectsEqual``  | [7f89dca](https://github.com/coala/coala/pull/4310/commits/7f89dca753d89649b438d9551014c12427a8e103) | Approved |
{: .table}

### Repository : docker-coala-base

| Issue reference                                                      |                         Pull Request                        |                  Commit shortlog                 | Commit hash                                                                                           | Status |
|----------------------------------------------------------------------|:-----------------------------------------------------------:|:------------------------------------------------:|-------------------------------------------------------------------------------------------------------|--------|
| [#181](https://github.com/coala/docker-coala-base/issues/181)        | [#185](https://github.com/coala/docker-coala-base/pull/185) | Remove uninstallation of packages not installed  | [79a0da1](https://github.com/coala/docker-coala-base/commit/79a0da1a55c84299e471f268785eaa601f949d47) | Merged |
| [#184](https://github.com/coala/docker-coala-base/issues/184)        | [#185](https://github.com/coala/docker-coala-base/pull/185) | Install packages libxml2-devel and libxslt-devel | [17c883d](https://github.com/coala/docker-coala-base/commit/17c883d4f53d1761f1d3f6dcc489afabafd01752) | Merged |
| [#182](https://github.com/coala/docker-coala-base/issues/182)  | [#185](https://github.com/coala/docker-coala-base/pull/185) | Use a lower version of node (nodejs6)            | [51fb17d](https://github.com/coala/docker-coala-base/commit/51fb17d9e4c0afe4ec46d585022b01ba39218a1e) | Merged |
| [#213](https://github.com/coala/docker-coala-base/issues/213) | [#208](https://github.com/coala/docker-coala-base/pull/208) | Add dependency `astyle`                          | [ee1fbda](https://github.com/coala/docker-coala-base/commit/ee1fbda306a39efe78a7b83437d7fd8a6b12b1b4) | Merged |
{: .table}

## Conclusion
Many new high quality bears along with an exhaustive documentation were merged
and are usable. There were workflow improvements for developers regarding tests
and bear writing. Developers will now be able to write better bears along with
more robust tests.
Although GSoC has ended, my contributions for OSS won't stop. These 2 months
have evolved my life and I've learnt so many things that would definitely help
me grow as a developer.
