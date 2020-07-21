---
layout: post
category : lessons
tagline: "How to test your Jekyll site locally"
tags : [intro, beginner, jekyll, tutorial]
img : helium-theme-post.jpg
img-mobile : 
img2 : 
img3 : 
author : Ed Anisko
title2 : 
title3 : 
css: 
js: 
bgcolor: ff5a71
keywords: helium, html, css, landing page, jekyll, ruby, web marketing, advertising
canonical: https://heliumjk.github.io
---
{% include JB/setup %}

In this tutorial I will teach you *how to test your Jekyll Bootstrap3* site locally.
<!--more-->

Jekyll is a parsing engine bundled as a ruby gem used to build static websites from
dynamic components such as templates, partials, liquid code, markdown, etc. Jekyll is known as "a simple, blog aware, static site generator".

To test your site locally, you'll need

1. [ruby](https://www.ruby-lang.org/en/)
2. [Jekyll](https://http://jekyllrb.com/)
3. [github-pages](https://github.com/github/pages-gem) gem


### Installing ruby

There are
[lots of different ways to install ruby](https://www.ruby-lang.org/en/installation/).


In Mac OS X, older versions of ruby will already be installed.  But I
use the [Ruby Version Manager (RVM)](http://rvm.io/) to have a more
recent version.  You could also use [Homebrew](http://brew.sh/).

In Windows, use [RubyInstaller](http://rubyinstaller.org/). (In most
of this tutorial, I've assumed you're using a Mac or some flavor of
Unix. It's possible that none of this was usable for Windows
folks. Sorry!)


### Installing the github-pages gem

Run the following command:
``` HTML
    gem install github-pages

```
This will install the `github-pages` gem and all dependencies
(including [jekyll](http://jekyllrb.com/)).

Later, to update the gem, type:
``` HTML
    gem update github-pages

```
### Testing your site locally

To construct and test your site locally, go into the directory and
type
``` HTML
    jekyll build

```
This will create (or modify) a `_site/` directory, containing
everything from `assets/`, and then the `index.md` and all
`pages/*.md` files, converted to html. (So there'll be
`_site/index.html` and the various `_site/pages/*.html`.)

Type the following in order to &ldquo;serve&rdquo; the site.
This will first run `build`, and so it does _not_ need to be
preceded by `jekyll build`.
``` HTML
    jekyll serve

```
To make jekyll automatically re-build your changes you can also add the `--watch` option:
``` HTML
    jekyll serve --watch
    
```
Now open your browser and go to <http://localhost:4000>.

Read the complete tutorial on <http://jekyllrb.com/docs/usage/>.

## Testing images

![Lost in space]({{ BASE_PATH }}/assets/img/big/lost_in_404_space.jpg){: .image-fluid }

***
#### #Code
``` HTML
	
	![Lost in space]({{ BASE_PATH }}/assets/img/big/lost_in_404_space.jpg){: .image-fluid }

```

### IMG With description on hover

![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe1.jpg "Description of lost in space image"){: .image-fluid }

***
#### #Code
``` HTML
	
	![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe1.jpg "Description of lost in space image"){: .image-fluid }

```

### With floating in markdown

| In markdown you can quikly use tables to align your images in right way, remember to style as you like the CSS of your table to have a amazing results. Use to size your pics in right way for best results. | ![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe2.jpg "Description of lost in space image"){: .image-fluid } |

***
#### #Code
``` HTML

	| In markdown you can quikly use tables to align your images in right way, remember to style as you like the CSS of your table to have a amazing results. Use to size your pics in right way for best results. | ![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe2.jpg "Description of lost in space image"){: .image-fluid } |


```

| ![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe3.jpg "Description of lost in space image"){: .image-fluid } | I am text to the right I am text to the right I am text to the right I am text to the right |

***
#### #Code
``` HTML

	| ![Lost in space with description]({{ BASE_PATH }}/assets/img/big/universe3.jpg "Description of lost in space image"){: .image-fluid } | I am text to the right I am text to the right I am text to the right I am text to the right |

```

### Video embed sample
<div class="video-container">
<iframe width="560" height="315" src="https://www.youtube.com/embed/ikbYpAHkurs?ecver=1" frameborder="0" allowfullscreen></iframe>
</div>

***
#### #Code
``` HTML
	<div class="video-container">
	<iframe width="560" height="315" src="https://www.youtube.com/embed/ikbYpAHkurs?ecver=1" frameborder="0" allowfullscreen></iframe>
	</div>

```

## License

[MIT](http://opensource.org/licenses/MIT)
