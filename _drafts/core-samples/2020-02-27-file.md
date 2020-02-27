---
layout: post
category: lessons
tagline: Example how post on Jekyll Helium
tags:
- jekyll
- code
img: syntax-hightlight.jpg
img2: 
img3: 
author: Antonio Trento
title2: 
title3: 
css: 
js: 
bgcolor: ff5a71
keywords: helium, html, css, landing page, jekyll, ruby, web marketing, advertising
canonical: https://fullit.github.io
title: ''

---
{% include JB/setup %}

Testing this shit out, Houston.

<!--more-->

## Testing code snippet highlight

The following example shows how to highlight a piece of code throughout the use of Javascript:

{% highlight javascript %}

    /*jshint browser: true, strict: true, undef: true */
    /*global define: false */
    
    ( function( window ) {
    
    'use strict';
    
    // class helper functions from bonzo https://github.com/ded/bonzo
    
    function classReg( className ) {
      return new RegExp("(^|\\s+)" + className + "(\\s+|$)");
    }
    
    // classList support for class management
    // altho to be fair, the api sucks because it won't accept multiple classes at once
    var hasClass, addClass, removeClass;
    
    if ( 'classList' in document.documentElement ) {
      hasClass = function( elem, c ) {
        return elem.classList.contains( c );
      };
      addClass = function( elem, c ) {
        elem.classList.add( c );
      };
      removeClass = function( elem, c ) {
        elem.classList.remove( c );
      };
    }
    else {
      hasClass = function( elem, c ) {
        return classReg( c ).test( elem.className );
      };
      addClass = function( elem, c ) {
        if ( !hasClass( elem, c ) ) {
          elem.className = elem.className + ' ' + c;
        }
      };
      removeClass = function( elem, c ) {
        elem.className = elem.className.replace( classReg( c ), ' ' );
      };
    }
    
    function toggleClass( elem, c ) {
      var fn = hasClass( elem, c ) ? removeClass : addClass;
      fn( elem, c );
    }
    
    var classie = {
      // full names
      hasClass: hasClass,
      addClass: addClass,
      removeClass: removeClass,
      toggleClass: toggleClass,
      // short names
      has: hasClass,
      add: addClass,
      remove: removeClass,
      toggle: toggleClass
    };
    
    // transport
    if ( typeof define === 'function' && define.amd ) {
      // AMD
      define( classie );
    } else {
      // browser global
      window.classie = classie;
    }
    
    })( window );

{% endhighlight %}

## Code highlighting with rounge and Prism

Another snippet rendered with the CSS code syntax:

``` CSS
    @import url('https://fonts.googleapis.com/css?family=Alfa+Slab+One|Gentium+Book+Basic');
    /* Reset CSS
     * --------------------------------------- */
    body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,
    form,fieldset,input,textarea,p,blockquote,th,td {
        padding: 0;
        margin: 0;
    }
    a{
        text-decoration:none;
    }
    table {
        border-spacing: 0;
    }
    fieldset,img {
        border: 0;
    }
    address,caption,cite,code,dfn,em,strong,th,var {
        font-weight: normal;
        font-style: normal;
    }
```

## Using snippet rendered with the HTML code syntax

``` HTML

<div id="fullpage">
    <div data-anchor="0section" class="section" id="section0">

        <h1 class="heavy">Ready to follow <br />your <span class="pink">dreams?</span></h1>
        <br /><h2 class="large-blur">
            <span class="highlight-container"><span class="highlight">
                Put your dreams on first and follow that!
            </span></span>

            <br />

                            

        </h2>
            <div class="intro-scroll-down">
              <a data-menuanchor="1section" href="#1section">
                <span class="mouse">
                  <span class="mouse-dot"></span>
                </span>
              </a>
            </div>



    </div>
```

**Check the markdown of this example in order to fully comprehend the correct syntax.**

[Here](https://github.com/sentenza/sentenza.github.io/issues/1) you can find more detailed information.