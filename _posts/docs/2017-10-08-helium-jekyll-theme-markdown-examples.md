---
layout: post
category : docs
tagline: "Example helium post in markdown and html classes"
tags : [jekyll, code, markdown]
img : markdown-samples.jpg
img2 : 
img3 : 
author : Ed Anisko
title2 : 
title3 : 
css: 
js: 
bgcolor: 
keywords: html, css, markdown, jekyll, docs, jekyllthemes, theme
canonical: https://fullit.github.io

---
{% include JB/setup %}
Markdown samples usefull when you start write your blog 🎉 🎆.

<!--more-->

# Examples

{:.sub-title}
#### in markdown cannot guarantee it work well


{:.bg-danger}
Test paragraph with **bg-danger** custom class.

{:.bg-success}
Test paragraph with **bg-success** custom class.

{:.bg-info}
Test paragraph with **bg-info** custom class.

{:.bg-warning}
Test paragraph with **bg-warning** custom class.

----
{:.sub-title}
#### in markdown
```
{:.bg-danger}
Test paragraph with **bg-danger** custom class.

{:.bg-success}
Test paragraph with **bg-success** custom class.

{:.bg-info}
Test paragraph with **bg-info** custom class.

{:.bg-warning}
Test paragraph with **bg-warning** custom class.

```
----

**Test Bold**

*Test coursive*

A divider: `----`


----

This is \*\*not\*\* in bold.

* This
* is
* a list

> This is quoted

1. with
1. numbers

[This is a link](https://edaniko.github.io)

----

**Default**. Text paragraph basic color

{:.text-primary}
**.text-primary**: Text paragraph using Primary color

{:.text-success}
**.text-success**: Text paragraph using Success color

{:.text-info}
**.text-info**: Text paragraph using Info Color

{:.text-warning}
**.text-warning**: Text paragraph using Warning color

{:.text-danger}
**.text-danger**: Text paragraph using Danger color

----

# Heading h1
## Heading h2
### Heading h3
#### Heading h4
##### Heading h5
###### Heading h6

{:.sub-title}
#### Subtitle h class using `{:.sub-title}`

----
# Video

{:.sub-title}
#### Not in markdown

<iframe width="560" height="315" src="https://www.youtube.com/embed/Po16lsLfpMk" frameborder="0" allowfullscreen></iframe>

----
{:.sub-title}
#### in HTML
```
<iframe width="560" height="315" src="https://www.youtube.com/embed/Po16lsLfpMk" 
frameborder="0" allowfullscreen></iframe>
```
----
## Paragraphs

{:.lead}
**A large paragraph** using `{:.lead}`: But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system
**Regular Paragraph**: But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system
{:.text-sm}
**Small Paragraph** using `{:.text-sm}`: But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system
{:.text-xs}
**Extra Small Paragraph** using `{:.text-xs}`: But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system

----

# Alerts

{:.sub-title}
#### in markdown cannot guarantee it work well


If are you looking to html version explore [Labels Alerts]({{ "/labels-alerts" | relative_url }}) and [Components]({{ "/components" | relative_url }})


{:.massage-box .alert-success}
**Test Message alert success** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-info}
**Test Message alert info** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-danger}
**Test Message alert danger** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-warning}
**Test Message alert warning** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

----

{:.sub-title}
#### in markdown

```
{:.massage-box .alert-success}
**Test Message alert success** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-info}
**Test Message alert info** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-danger}
**Test Message alert danger** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.

{:.massage-box .alert-warning}
**Test Message alert warning** 
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt a in, ullam.
```
----

# Labels

{:.sub-title}
#### in markdown cannot guarantee it work well


{:.label .label-default-filled}
Default

{:.label .label-success-filled}
Success

{:.label .label-info-filled}
Info

{:.label .label-warning-filled}
Warning

{:.label .label-danger-filled} 
Danger

----

{:.sub-title}
#### in markdown

```
{:.label .label-default-filled}
Default

{:.label .label-success-filled}
Success

{:.label .label-info-filled}
Info

{:.label .label-warning-filled}
Warning

{:.label .label-danger-filled} 
Danger
```
----

# Class nesting samples
```
*   list item

*   list item {.classA}
    {.classB}
{.classC}
```


`{.some-class .proposed-syntax}`
A paragraph of text.

vs

```
<p class="some-class" markdown="1">
  A paragraph of text.
</p>
```
## Tables

When you compare the code for tables, the ability to add a class via markdown attributes makes a world of difference:


Some | Basic | Table 
-----|-------|------
a    | b     | c
d    | e     | f



{:.sub-title}
#### in markdown

```
{.table .table-striped}
Some | Basic | Table 
-----|-------|------
a    | b     | c
d    | e     | f
```

----
# Dynamic ADS Block

{:.sub-title}
#### It autoresize in base of the container dimensions, avaible if you edit _confi.yaml file

<div>
{% include ads-block.html %}
</div>

----

{:.sub-title}
#### in HTML and liquid

```
<div>
```
&#123;&#37; include ads-block.html &#37;&#125;
```
<div>
```
----

{:.sub-title}
# Copy Sample


# A Study In Scarlet

## PART I.

(Being a reprint from the reminiscences of John H. Watson, M.D., late of the Army 
Medical Department.)

1.  ### Mr. Sherlock Holmes

    In the year 1878 I took my degree of Doctor of Medicine of the 
    University of London, and proceeded to Netley to go through 
    the course prescribed for surgeons in the army. Having completed 
    my studies there, I was duly attached to the Fifth Northumberland 
    Fusiliers as Assistant Surgeon. The regiment was stationed in 
    India at the time, and before I could join it, the second [...]

    The campaign brought honours and promotion to many, but for me 
    it had nothing but misfortune and disaster. I was removed from my 
    brigade and attached to the Berkshires, with whom I served at 
    the fatal battle of Maiwand. There I was struck on the [...]            {.randomClass}

2.  ### More content

    Worn with pain, and weak from the prolonged hardships which 
    I had undergone, I was removed, with a great train of wounded 
    sufferers, to the base hospital at Peshawar. Here I rallied, and had 
    already improved so far as to be able to walk about the [...]
p.s. I tend to agree on the adding classes/IDs to every possible element to be overkill.

----

{:.sub-title}
#### in markdown


```
# A Study In Scarlet

## PART I.

(Being a reprint from the reminiscences of John H. Watson, M.D., late of the Army 
Medical Department.)

1.  ### Mr. Sherlock Holmes

    In the year 1878 I took my degree of Doctor of Medicine of the 
    University of London, and proceeded to Netley to go through 
    the course prescribed for surgeons in the army. Having completed 
    my studies there, I was duly attached to the Fifth Northumberland 
    Fusiliers as Assistant Surgeon. The regiment was stationed in 
    India at the time, and before I could join it, the second [...]

    The campaign brought honours and promotion to many, but for me 
    it had nothing but misfortune and disaster. I was removed from my 
    brigade and attached to the Berkshires, with whom I served at 
    the fatal battle of Maiwand. There I was struck on the [...]            {.randomClass}

2.  ### More content

    Worn with pain, and weak from the prolonged hardships which 
    I had undergone, I was removed, with a great train of wounded 
    sufferers, to the base hospital at Peshawar. Here I rallied, and had 
    already improved so far as to be able to walk about the [...]
p.s. I tend to agree on the adding classes/IDs to every possible element to be overkill.

```

----
### Other features
----


# Lists (Uneder construction)

1.  Red one
2.  Green two
3.  Blue three


*   A list item.

    With multiple paragraphs.

*   Another item in the list.

# LINKS

Markdown supports two styles for creating links: inline and reference. With both styles, you use square brackets to delimit the text you want to turn into a link.

Inline-style links use parentheses immediately after the link text. For example:

```
This is an [example link](http://example.com/).
Output:

<p>This is an <a href="http://example.com/">
example link</a>.</p>
```
Optionally, you may include a title attribute in the parentheses:

```
This is an [example link](http://example.com/ "With a Title").
```
Output:

```
<p>This is an <a href="http://example.com/" title="With a Title">
example link</a>.</p>
```

Reference-style links allow you to refer to your links by names, which you define elsewhere in your document:

```
I get 10 times more traffic from [Google][1] than from
[Yahoo][2] or [MSN][3].

[1]: http://google.com/        "Google"
[2]: http://search.yahoo.com/  "Yahoo Search"
[3]: http://search.msn.com/    "MSN Search"
```
Output:

```
<p>I get 10 times more traffic from <a href="http://google.com/"
title="Google">Google</a> than from <a href="http://search.yahoo.com/"
title="Yahoo Search">Yahoo</a> or <a href="http://search.msn.com/"
title="MSN Search">MSN</a>.</p>
```

The title attribute is optional. Link names may contain letters, numbers and spaces, but are not case sensitive:

```
I start my morning with a cup of coffee and
[The New York Times][NY Times].

[ny times]: http://www.nytimes.com
```

Output:

```
<p>I start my morning with a cup of coffee and
<a href="http://www.nytimes.com/">The New York Times</a>.</p>
```

# IMAGES

Image syntax is very much like link syntax.

Inline (titles are optional):

```
![alt text](/path/to/img.jpg "Title")
```

Reference-style:

```
![alt text][id]

[id]: /path/to/img.jpg "Title"
```

Both of the above examples produce the same output:

`<img src="/path/to/img.jpg" alt="alt text" title="Title" />`


# CODE

In a regular paragraph, you can create code span by wrapping text in backtick quotes. Any ampersands (&) and angle brackets (< or >) will automatically be translated into HTML entities. This makes it easy to use Markdown to write about HTML example code:

```
I strongly recommend against using any `<blink>` tags.


I wish SmartyPants used named entities like `&mdash;`
instead of decimal-encoded entites like `&#8212;`.
```

Output:

```
<p>I strongly recommend against using any
<code>&lt;blink&gt;</code> tags.</p>

<p>I wish SmartyPants used named entities like
<code>&amp;mdash;</code> instead of decimal-encoded
entites like <code>&amp;#8212;</code>.</p>
To specify an entire block of pre-formatted code, indent every line of the block by 4 spaces or 1 tab. Just like with code spans, &, <, and > characters will be escaped automatically.
```
# Markdown:
```
If you want your page to validate under XHTML 1.0 Strict,
you've got to put paragraph tags in your blockquotes:

    <blockquote>
        <p>For example.</p>
    </blockquote>
```
Output:
```
<p>If you want your page to validate under XHTML 1.0 Strict,
you've got to put paragraph tags in your blockquotes:</p>

<pre><code>&lt;blockquote&gt;
    &lt;p&gt;For example.&lt;/p&gt;
&lt;/blockquote&gt;
</code></pre>
```
