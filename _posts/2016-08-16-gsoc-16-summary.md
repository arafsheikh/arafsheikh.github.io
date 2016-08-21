---
layout: post
title: Google Summer of Code '16 Summary
date: 2016-08-16 00:00:00 +0530
permalink: /google-summer-of-code-2016-summary
---

The Google Summer of Code programme has come to an end, and it's been an amazing experience.
I've learnt a lot in these three months. Apart from the technical knowledge gained,
I've learnt how to well communicate with other members of the team, manage deadlines, and maintain code.

This blog post is a final report of my Google Summer of Code project.

## Commits

The tables below list of commits I've made to various `coala` repositories as a part of my project.

### [_coala-eclipse_](https://github.com/coala-analyzer/coala-eclipse)

{:.center}
|  SHA                                                                      |  Description                                                        |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [d5053c7](https://github.com/coala-analyzer/coala-eclipse/commit/d5053c7) |  export: Update installation binary                                 |
| [fbdede5](https://github.com/coala-analyzer/coala-eclipse/commit/fbdede5) |  plugin.xml: Add 'Run coala' button to toolbar                      |
| [ae8d98e](https://github.com/coala-analyzer/coala-eclipse/commit/ae8d98e) |  plugin.xml: Enable coala in all context menus                      |
| [3abe286](https://github.com/coala-analyzer/coala-eclipse/commit/3abe286) |  BearMenu: List bears in ascending order                            |
| [555e68f](https://github.com/coala-analyzer/coala-eclipse/commit/555e68f) |  ExternalUtils: Ask user for non-optional settings                  |
| [2b90dcc](https://github.com/coala-analyzer/coala-eclipse/commit/2b90dcc) |  travis.yml: Disable P2 mirrors                                     |
| [0238e7d](https://github.com/coala-analyzer/coala-eclipse/commit/0238e7d) |  travis.yml: Use pre-release coala                                  |
| [f4283ec](https://github.com/coala-analyzer/coala-eclipse/commit/f4283ec) |  BearMenu: Use coala-json to get list of bears                      |
| [9cf253d](https://github.com/coala-analyzer/coala-eclipse/commit/9cf253d) |  ExternalUtils: Check coala binary before execution                 |
| [01af287](https://github.com/coala-analyzer/coala-eclipse/commit/01af287) |  travis.yml: Add DISPLAY property                                   |
| [69da10e](https://github.com/coala-analyzer/coala-eclipse/commit/69da10e) |  tests: Add QuickFixerTest                                          |
| [cd862e3](https://github.com/coala-analyzer/coala-eclipse/commit/cd862e3) |  coafile: Ignore diff_match_patch.java                              |
| [866ee2a](https://github.com/coala-analyzer/coala-eclipse/commit/866ee2a) |  MarkerTest: Update test                                            |
| [794c21a](https://github.com/coala-analyzer/coala-eclipse/commit/794c21a) |  Add MarkerResolution and QuickFix                                  |
| [7d83c96](https://github.com/coala-analyzer/coala-eclipse/commit/7d83c96) |  RuncoafileHandler.java: Show error dialog instead of logging error |
| [844b84e](https://github.com/coala-analyzer/coala-eclipse/commit/844b84e) |  Rename marker ID to com.coala.core.problem                         |
| [9774379](https://github.com/coala-analyzer/coala-eclipse/commit/9774379) |  ExternalUtils.java: Process all sections                           |
| [1da1c83](https://github.com/coala-analyzer/coala-eclipse/commit/1da1c83) |  tests: Add coafile test                                            |
| [1d7809d](https://github.com/coala-analyzer/coala-eclipse/commit/1d7809d) |  coafileHandler: Handle coafile                                     |
| [6a1bdc9](https://github.com/coala-analyzer/coala-eclipse/commit/6a1bdc9) |  Rename Plugin.java to coafileHandler                               |
| [a622983](https://github.com/coala-analyzer/coala-eclipse/commit/a622983) |  ExternalUtils.java: Rename function                                |
| [4c3befe](https://github.com/coala-analyzer/coala-eclipse/commit/4c3befe) |  tests: Update tests                                                |
| [fa70d22](https://github.com/coala-analyzer/coala-eclipse/commit/fa70d22) |  menu: Add bears to menu                                            |
| [5141977](https://github.com/coala-analyzer/coala-eclipse/commit/5141977) |  Move external utilities to separate class                          |
| [848e7ab](https://github.com/coala-analyzer/coala-eclipse/commit/848e7ab) |  core/plugin.xml: Move menu to PackageExplorer                      |
| [1699842](https://github.com/coala-analyzer/coala-eclipse/commit/1699842) |  coafile: Add .coafile                                              |
| [b74a29d](https://github.com/coala-analyzer/coala-eclipse/commit/b74a29d) |  tests: Refactor for Gitmate                                        |
| [b9119a4](https://github.com/coala-analyzer/coala-eclipse/commit/b9119a4) |  core: Refactor for Gitmate                                         |
| [19994cb](https://github.com/coala-analyzer/coala-eclipse/commit/19994cb) |  README.md: Fix export URL                                          |
| [0422a33](https://github.com/coala-analyzer/coala-eclipse/commit/0422a33) |  README.md: Add build instructions                                  |
| [5c17301](https://github.com/coala-analyzer/coala-eclipse/commit/5c17301) |  README.md: Add Travis badge                                        |
| [a021905](https://github.com/coala-analyzer/coala-eclipse/commit/a021905) |  README.md: Remove alternate install instructions                   |
| [d32eaf5](https://github.com/coala-analyzer/coala-eclipse/commit/d32eaf5) |  export: Add update-site                                            |
| [3448ff9](https://github.com/coala-analyzer/coala-eclipse/commit/3448ff9) |  core: Remove old update-site                                       |
| [55fb691](https://github.com/coala-analyzer/coala-eclipse/commit/55fb691) |  Add update site                                                    |
| [cb97a57](https://github.com/coala-analyzer/coala-eclipse/commit/cb97a57) |  Plugin.java: Use commons-exec to run coala-json                    |
| [60dc1b1](https://github.com/coala-analyzer/coala-eclipse/commit/60dc1b1) |  lib: Add commons-exec                                              |
| [42a0ca2](https://github.com/coala-analyzer/coala-eclipse/commit/42a0ca2) |  tests: Add RunCmdTest                                              |
| [12f5360](https://github.com/coala-analyzer/coala-eclipse/commit/12f5360) |  MarkerTest: Improve test                                           |
| [e5cf094](https://github.com/coala-analyzer/coala-eclipse/commit/e5cf094) |  RemoveMarkers.java: Refactor line length                           |
| [4486410](https://github.com/coala-analyzer/coala-eclipse/commit/4486410) |  Plugin.java: Refactor methods                                      |
| [895a88a](https://github.com/coala-analyzer/coala-eclipse/commit/895a88a) |  Fix travis-ci                                                      |
| [9af350a](https://github.com/coala-analyzer/coala-eclipse/commit/9af350a) |  Moved tests to separate package                                    |
| [a7a142c](https://github.com/coala-analyzer/coala-eclipse/commit/a7a142c) |  Add Travis-Ci                                                      |
| [e376fc1](https://github.com/coala-analyzer/coala-eclipse/commit/e376fc1) |  Add LICENSE                                                        |
| [7e03099](https://github.com/coala-analyzer/coala-eclipse/commit/7e03099) |  Remove ignored files                                               |
| [8be28c5](https://github.com/coala-analyzer/coala-eclipse/commit/8be28c5) |  Add .gitignore                                                     |
| [68758db](https://github.com/coala-analyzer/coala-eclipse/commit/68758db) |  tests: Add MarkerTest                                              |
| [e4426d6](https://github.com/coala-analyzer/coala-eclipse/commit/e4426d6) |  Rename com.coala.plugin to com.coala.core                          |
| [513e6be](https://github.com/coala-analyzer/coala-eclipse/commit/513e6be) |  Clean up                                                           |


### [_coala-bears_](https://github.com/coala-analyzer/coala-bears)

|  SHA                                                                    |  Description                                         |
| ----------------------------------------------------------------------- | ---------------------------------------------------- |
| [359afc5](https://github.com/coala-analyzer/coala-bears/commit/359afc5) |  bears: Use coala-utils for string processing        |
| [d024ce5](https://github.com/coala-analyzer/coala-bears/commit/d024ce5) |  requirements.txt: Update coala                      |
| [9e5b42f](https://github.com/coala-analyzer/coala-bears/commit/9e5b42f) |  ClangComplexityBear: Make ``cursor_kinds`` private  |
| [0fef458](https://github.com/coala-analyzer/coala-bears/commit/0fef458) |  CheckstyleBear: Handle column field correctly       |

### [_coala_](https://github.com/coala-analyzer/coala)

|  SHA                                                              |  Description                                          |
| ------------------------------------------------------------------| ----------------------------------------------------- |
| [f9e46c8](https://github.com/coala-analyzer/coala/commit/f9e46c8) |  coala-json: Add show_bears and filter_by_language    |
| [460a8c1](https://github.com/coala-analyzer/coala/commit/460a8c1) |  ConfigurationGathering: Add get_filtered_bears       |

This in total accounts for a change of <font color="green">+6292</font> / <font color="red">-1802</font> LOC.

## Current state of the plug-in

After working hard for three months on the plug-in, I'm happy to say that the plug-in
is very much usable by the end user. The plug-in will make the life of developers who
use Eclipse easy by allowing them to analyze code directly from within the IDE.

The plug-in provides two primary ways to run the analysis. One by using the pre-configured
`coafile` and other by manually selecting a bear. The first approach is preferred since
it allows running the analysis on the whole project directory, in contrast to the manual
approach which runs the analysis on a specific file.

Once the analysis is initiated the plug-in then communicates with coala using the `coala-json`
binary. After the analysis is complete the results (if any) are marked on the editor
along with the issue message.

![](/images/marker.png)

Another important feature of the plug-in is that it allows the user to automatically fix
the issues if the bear used gives the corrected result. Once the markers are visible in the
`Problems` view the `Quick Fix` option can be selected and the `diff` to correct the issue
will be automatically applied to the source file. This internally uses Google's
[diff-match-patch](https://code.google.com/p/google-diff-match-patch/) library.

There's a lot of other stuff that the plug-in does that I haven't covered in this post
like user interaction for the bears that require user input, dynamic menus, etc. 
I've extensively covered my progress in the bi-weekly posts. Do check them out if you
wish to know more about my project.

## Remaining work

Most of the stuff that I had proposed in my proposal is completed successfully. But I
couldn't complete work on the `coafile` editor. This task turned out to be much more
complicated than I expected it to be. Nevertheless I'll resume work on it as soon as
possible.

Another feature I proposed for the plug-in was the "Bear creation wizard". This was an
experimental feature that I would've discussed with my mentor if my project completed
before the deadline (which obviously didn't happen). Also a similar tool called
[coala_bears_create](https://gitlab.com/coala/coala-bear-management) was implemented
by [mr-karan](http://mr-karan.github.io) in his project.

## Acknowledgements

Finally I would like to thank Google for this amazing opportunity to work with some of the most amazing people,
learn so much, and get paid to have fun. Special thanks to my mentor *Harsh Dattani* for helping me with the project, 
and the folks at *Python Software Foundation* and *coala* for selecting me to be a part of this programme.

.center {
  text-align: center;
}
