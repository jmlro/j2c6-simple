---
title: "Smigle a Minimalist Blog Theme for Hugo"
date: 2021-08-20
categories:
  - uncategorized
tags:
  - hugo
  - theme
  - project
---

The site you're now reading was built with
[smigle][theme-smigle-profile], a publicly shared blog theme I created
from scratch for the [Hugo static site generator][hugo]. If you're
dissastified with Hugo's [official collection of
themes][hugo-theme-collection] (currently it contains 403 themes) and
want a blog that exactly meets your needs, I recommend building your own
theme. It's a short, straight-forward process, and my hope is that from
reading about my experience building smigle, which took only one
two-week sprint, you'll decide to build your own theme too.

<!--more-->

### Influential themes

As a non-design person, I began smigle as I do with most frontend
designs: I searched for existing designs and borrowed ideas from them.
Here are the top five themes that I drew from, from most to least amount
of influence.

1. [sumnerevans' smol][theme-smol-sumnerevans] - comfortable room for
writing, no-frills layout, prominent header, excellent portfolio page
2. [colorchestra's smol][theme-smol-colorchestra] - appealing design
contraints (no JS, no bloat)
3. [PaperMod][theme-papermod] - loved the simplicity, typography, and
B&W color scheme
4. [Cupper][theme-cupper] - sensible instructions for theme users
5. [Mini][theme-mini] - liked the simplicity

At first glance, you'd may be tempted to say smigle is no different than
sumnerevans' smol. In truth, the general layout and font are the same,
but under the hood, there are many differences. That author based his
theme on colorchestra's theme with same name, but in the process,
reversed "no bloat" ethos of the original smol. sumnerevans' smol has
commenting, search, light/dark mode, and something called openring that
gives highlights of other blogs you read. When I started smigle, I used
the original smol as the base and introduced that sumnerevan's general
layout and font, without including any of the blog features I consider
to be bloat.

### Little touches

After choosing the base layers of smigle, namely the scaffolding from
the original smol and the layout from sumnerevans' smol, I incorporated
several little touches from other themes that made for a better overall
feel.

- [An example site directory][theme-smigle-example-dir] to give users a
  quick way to demonstrate the theme (modeled after cupper)
- A bubble-like layout for the tags and categories pages (modeled after
  mini)
- A yearly grouping in the posts page (modeled after mini)

Then I borrowed one more piece from sumnerevans' theme: the simple,
collapsible portfolio page design. With collapsible content, the
portfolio is still readable as my career continues and my portfolio
grows in length. What made this feature so simple is that the user
interaction was accomplished with only two HTML5 tags, `details` and
`summary`, and all the styling it needed was an off-white background
color, margin, padding, and float right for the date.

### Challenges

Despite having experience with web development and [Jekyll][jekyll] (the
Ruby-based static site generator), I faced some challenges when I built
smigle because I was completely new to Hugo and [Go][go] (the language
it's written in).

- Hugo templates, specifically the `range` and `.` syntax were confusing
- Getting `range` to treat the last element was annoying (as discussed
  in [an earlier post][blog-post-range])
- Overriding a theme's static file paths was confusing

What helped get over these challenges was skimming and rereading the
Hugo docs and searching through the Hugo community
[Discourse][hugo-discourse]. As I pointed out in [an another earlier
post][blog-post-docs], the docs are vast and not well organized for
beginners, but what can you do?

### Favorite parts

As with any project, there some nifty parts to building smigle that made
it a good experience.

- [Rendering a template using a data file][hugo-data-file] (in my case a
  .yaml with portfolio details) was surprisingly easy and powerful. This
  feature enabled me to separate portfolio data from the HTML structure,
  which will make maintaining my portfolio a breeze since it just means
  editing a YAML file. Since a portfolio page was a personal need of
  mine and not pertaining to blog, I keep this page out of the smigle
  theme, but in the site that makes use of smigle.
- Learning a little about the workflow with [git
  submodules][git-submodule] was interesting. This topic came up because
  [the traditional way][hugo-add-theme] of using a Hugo theme involves
  cloning the theme repo as a submodule of your website repo.
- Sharing smigle on [Hugo's official collection of
  themes][hugo-theme-collection] was satisfying since anybody can now
  discover and reuse my work.

[blog-post-range]: /posts/handle-last-element-differently-when-looping-in-hugo/
[blog-post-docs]: /posts/sprawling-hugo-docs-impede-first-time-users/
[git-submodule]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[go]: https://golang.org/
[hugo]: https://gohugo.io/
[hugo-add-theme]: https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme
[hugo-data-file]: https://gohugo.io/templates/data-templates/
[hugo-discourse]: https://discourse.gohugo.io/
[hugo-theme-collection]: https://themes.gohugo.io/
[jekyll]: https://jekyllrb.com/
[theme-smol-sumnerevans]: https://github.com/sumnerevans/smol
[theme-smol-colorchestra]: https://github.com/colorchestra/smol
[theme-cupper]: https://github.com/zwbetz-gh/cupper-hugo-theme
[theme-mini]: https://github.com/nodejh/hugo-theme-mini
[theme-papermod]: https://github.com/adityatelange/hugo-PaperMod
[theme-smigle-example-dir]: https://gitlab.com/ian-s-mcb/smigle-hugo-theme/-/tree/main/exampleSite
[theme-smigle-profile]: https://themes.gohugo.io/themes/smigle-hugo-theme/
[demo]: https://smigle-hugo-theme.netlify.app/
