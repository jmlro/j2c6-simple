---
title: "Handle Last Element Differently When Looping In Hugo"
date: 2021-07-31
categories:
  - uncategorized
tags:
  - hugo
  - beginner
  - tips
---

When building [smigle][smigle], the Hugo theme for this site, I was
looping over an array and outputting both the current element and some
delimiter text, but I couldn't figure out how to handle the last element
differently from the rest so as to avoid the unwanted trailing
delimiter. In this post, I cover the solutions I found for this
delimiter issue. Hopefully, this short read saves you from the misery I
went through while hunting for advice on Stack Overflow and Discourse.

<!--more-->

## The Task

The task I was trying to accomplish with the `range` builtin function
seemed simple to me. I wanted to build a navbar by looping over an array
of maps, each containing two keys: name and url. One important
requirement of the navbar was that the links needed to be separated by
some delimiter text, a '|' in my case. The tricky part of the
requirement was eliminating the unwanted trailing delimiter.

Having explained the task, let's dive into the code. In the following
code snippet, I create an array of foods and range over the array while
creating links within a paragraph. In reality, your array will probably
come from your config file, but I wanted this example to be
self-contained. 

```html
{{/* Snippet-1 */}}

{{ $array := slice
  (dict "name" "apple" "url" "https://en.wikipedia.org/wiki/Apple")
  (dict "name" "banana" "url" "https://en.wikipedia.org/wiki/Banana")
  (dict "name" "carrot" "url" "https://en.wikipedia.org/wiki/Carrot")
}}

{{/* Build delimited links (has trailing delimiter) */}}
<p>
  {{ range $array }}
    <a href="{{ .url }}">{{ .name }}</a> |
  {{ end }}
</p>
```

The code above produces the unwanted trailing delimiter. The following
code shows two options that both fix the trailing delimiter issue. 

## Two solutions

```html 
{{/* Snippet-2 */}}

{{/* Option-1 - pull out array index */}}
<p>
  {{ range $index, $value := $array }}
    {{ if $index }} | {{ end }}
    <a href="{{ .url }}">{{ .name }}</a>
  {{ end }}
</p>

{{/* Option-2 - limit the array using first and after */}}
<p>
  {{ range first 1 $array }}
    <a href="{{ .url }}">{{ .name }}</a>
  {{ end }}
  {{ range after 1 $array }}
    | <a href="{{ .url }}">{{ .name }}</a>
  {{ end }}
</p>
```

The first option looks more [DRY][dry], but it could be less performant
since it evaluates a condition during each loop iteration. It works by
using the `range` syntax that pulls out the index of the array and then
performing a clever condition check on the index. The condition is met
if the index is truthy, which is the case for all indicies besides the
first one, since 0 is falsey.  When that condition isn't met, only the
link is outputed, and no delimiter. When the condition is met, the link
is prefixed with the delimiter. I came across this option in [this
discourse post][bep-discourse-post] by the Hugo author
[@bep][bep-github].

The second option makes use of the handy `first` and `after` builtin
functions which respectively, limit elements of an array to the first n
elements and advance the iterator's position by n. Those two functions
are used to separate how the first and non-first elements are processed.
I found this option while digging through [this Hugo
theme][sumner-smol-theme] by [@sumnerevans][sumner-github].

## One tempting non-solution

Before I wrap up this post, I want to point out the `delimit` builtin
function, which comes up whenever you do a web search for "hugo range
last delimiter." Although sounding perfectly relevant, this fuction is
not the right tool for the job. This is because `delimit` accepts an
array and a delimiter string and outputs one string with all the array
elements spaced out by the delimiter. Unfortunately, that doesn't give
the flexibility of `range`, which lets you output arbitrary HTML.

```html
{{/* Snippet-3 */}}

{{ $array := slice "apple" "banana" "carrot" }}
<p>
  {{ delimit $array " | " }}
</p>
{{/*
  Outputs:
    <p>apple | banana | carrot</p>
*/}}
```

The above code demonstrates what `delimit` function is capable of. As
you can see, the function doesn't allow for outputing links using the
the array of name/url maps from before.

You've seen two ways of solving the "last delimiter issue" and one
tempting yet unhelpful function. Hopefully, this short lesson helps
advance your Hugo skills and saves you time hunting through Q&A sites.

Thanks for reading!

[smigle]: https://gitlab.com/ian-s-mcb/smigle-hugo-theme
[dry]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[bep-discourse-post]: https://discourse.gohugo.io/t/howto-delimiter-separated-tags/146
[bep-github]: https://github.com/bep/
[sumner-smol-theme]: https://github.com/sumnerevans/smol/blob/master/layouts/partials/footer.html
[sumner-github]: https://github.com/sumnerevans
