---
title: "Sprawling Hugo Docs Impede First Time Users"
date: 2021-08-01
lastMod: 2021-08-18
categories:
  - uncategorized
tags:
  - hugo
  - documentation
---

Although the [Hugo docs][hugo-docs] include many valuable topics guides,
they don't offer a readable, beginner's track. In this post, I describe
why this track is needed, what it ought to contain, and how much of it
can be sourced from existing doc pages.

<!--more-->

Let me start off by acknowledging what the Hugo documentation writers
did right. Templates were thoroughly introduced without assuming prior
Go experience, each builtin function was clearly explained, and
variables were appropriately grouped by their context. Unfortunately,
those good parts of the docs are only suitable for intermediate users
(ones who already have a fair command of the Hugo basics), whereas
beginners have to scrap by with the inadequate [Getting
Started][hugo-getting-started] section.

### The missing bridge to advance topic guides

It's the "Getting Started" section that contains the closest attempt at
a beginner's track, namely the seven-step [Quick
Start][hugo-quick-start] page, but it's too brief to give the foundation
beginners need. The seven steps consist of the terminal commands that
perform essential tasks, such as creating a site, adding a theme, adding
content, and generating a site for either development or production.
They work well as a brief tour of Hugo that can be completed in five
minutes or less, but what doc page are beginners supposed read next? Of
the six pages in the "Getting Started" section, only one of them, the
[Directory Structure][hugo-dir-structure] page, presents any new and
immediately helpful information.

In the absence of any other beginner friendly material, readers must
dive into the various topic guides (such as Content Management and
Templates), which contain an exhausting amount of detail and lack the
goal-oriented flow of a beginner's track.

Just take a look at the enormous [Intro to
Templating][hugo-intro-to-templating] page. It contains 2,600 words and
it's only one of the 24 pages in the "Templates" section. Other sections
like [Content Management][hugo-content-management] are not quite as
overwhelming (it has 22 pages of up to 1,060 words per page), but they
are still problematic when considering that beginners, people trying use
core Hugo functionality, are not looking to read every detail under the
sun about Hugo.

### Outline for beginner's track
Below is rough idea of what the beginner's track would include.

1. 7-step Quick Start page
1. Directory Structure
1. Content Format + Front Matter
1. Definition + Example of a Shortcode
1. Intro to Templates (either a shorter or subdivided version)
1. Template Types (only the most essential ones)
    1. Base
    1. List
    1. Taxonomy
    1. Partial
1. Site variables

All items in the above outline correspond to one or more existing doc
page. Turning the outline into pages wouldn't be heavy undertaking, but
attention to clarity and simplicity is needed.

### Conclusion

The Hugo docs need a beginner's track with substantial material to
soften the transition readers make from the "Quick Start" page to the
detailed topic guides. This will be a valuable addition because the
"Quick Start" page is overly brief and topic guides are a challenging
read given how lengthy and zoomed in they are.

[hugo-docs]: https://gohugo.io/documentation/
[hugo-getting-started]: https://gohugo.io/getting-started/
[hugo-quick-start]: https://gohugo.io/getting-started/quick-start/
[hugo-dir-structure]: https://gohugo.io/getting-started/directory-structure/
[hugo-content-management]: https://gohugo.io/categories/content-management
[hugo-intro-to-templating]: https://gohugo.io/templates/introduction/
