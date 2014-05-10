# jQuery Hello World
---

_jQuery_ is a _Javascript_ library which facilitates the writing of complex UI behaviors code by **removing any cross browser incompatibility**.

> This article is a **really basic introduction to _jQuery_**, It's pourpose is to
> explain what _jQuery_ is and how to integrate it into an _HTML_ page.  
> 
> **You need some basic _HTML_ skills** in order to fuly comprehend this article. 

<!--more-->

## Quick & Dirty Example

The best way to understand _jQuery_ is to run a simple example then try to understand _WHY_ it works.

> In this example we **append** an `<p>Hello World</p>` code to the page's `BODY`.  
> This action alter the page's _DOM_ structure introducing a new node.

### HTML:

    <html>
    <head>
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/2.1.0/jquery.min.js"></script>
        <script>
        $(document).ready(function() {
            $('body').append('<p>Hello World by jQuery</p>');
        });
        </script>
    </head>
    <body>
        <p>Hello World by HTML</p>
    </body>
    </html>

<!--<iframe src="http://cdpn.io/rIsev" width="100%" height="90px" style="border: 1px solid black"></iframe>-->

<small>[open the full commented source file for this example](./example/01-hello-world.html)</small>

Code above contains a fully functional jQuery script which **add a new DOM element to the page**. Manipulating the page DOM structure is indeed one of the most often used jQuery capabilities.

### Understanding the Example

> 1\. link jQuery library file

The first `script` tag **links jQuery library** from Google CDN (we'll discuss this later). This instruction include the library into the page, **all jQuery based code must be placed after this instruction** in order to work!

> 2\. use jQuery through the global symbol `$`

The second `script` block contains the example's code. Here jQuery is available to be used through **the `$` global symbol which basically _IS_ jQuery** for your code perspective.

> The expression **global symbol** means a _Javascript object_ which is available in 
> every scripts after it's been declared. (*)

A _jQuery script_ is basically a piece of Javascript where jQuery API are used with the _global symbol_ `$.apiMethod()`.

The first instruction in our example it's a wrapper whose purpose is to **run jQuery code when the page is ready**:

    $(document).ready(...);
    
> jQuery is used to manipulate page's DOM structure, in order to do this job without errors 
> that DOM structure must be loaded and ready to be used!

### Understanding a jQuery Instruction

The only other instruction in our first example is:

    $('body').append('...');
    
that should be read like: 

> take the page's body and append "..." to it

We should split this simple line of code in two distinct responsibilities:

    1) $('body')        // take the page's body
    2) .append('...')   // append "..." to it
    
The first instruction **take a CSS like selector and return a jQuery Object** which can be manipulated via jQuery API methods.

> **This is the core concept around jQuery**.  
> When you deeply understand this point then you'll master jQuery.

You can **use all CSS3 selectors** with `$(...)` in order to obtain a _jQuery Object_ which represents all matched elements in the page.

Then you can run any jQuery API method on that object in order to modify it.

> A _jQuery Object_ should match both a single DOM Element or a list of elements, 
> it really doesn't matter because jQuery take care of this when you apply some API.


### Add Some Fun!

In above example we matched the page's `body` in order to append a string.

Now we cant try a different approach:

- we create a **new jQuery Object** which contains the new paragraph
- we append that object to the page's body
- we add some style to the new object
- we add a fade-in effect in order to animate the action
    
Here is the code, we modify only the real example's code, the `document.ready` wrapper does not change:

    $('<p>Hello World by jQuery</p>')
        .appendTo('body')
        .css('background', 'yellow')
        .hide()
        .fadeIn(2000);
      
The first instruction looks like the one we used to match the page's body `$('body')`, the difference here is that we give jQuery with **a portion of HTML code instead of a CSS selector** so jQuery understand and create an new object.

With this brand new object we can play with all jQuery's API methods, **we can also chain jQuery methods** one after one to queue instructions to be applied to that object!

- append
- css
- hide
- fadeIn

<!--<iframe src="http://cdpn.io/zoeug" width="100%" height="90px" style="border: 1px solid black"></iframe>-->

<small>[open the full commented source file for this example](./example/02-chain-methods.html)</small>

### Even More Fun With Callbacks

In the previous example we used a **basic animation method** `fadeIn()` to give a smooth effect to the "append" action. We also use a yellow background to highlight the new content in the page.

> Can we remove the background color when the animation is complete?

**Of course you can!**, many jQuery methods accepts a _function_ to be executed when they finish their job:

    // pseudo code
    $.doSomething(doSomethingElse)
    
    // real jquery
    $('p').fadeOut(function() {
        $(this).remove();
    });
    
that should be read like:

> take all "p" in the page and fade them out  
> when an animation is complete, remove that item

This when we create a new function as param for another function **we create a _callback_ method**. 

Now our example should progress to:

    .fadeIn(2000, function() {
        $(this).css('background', null);
    });

<!--<iframe src="http://cdpn.io/oBAlI" width="100%" height="90px" style="border: 1px solid black"></iframe>-->

<small>[open the full commented source file for this example](./example/03-api-callbacks.html)</small>

Here we're introducing a new concept `$(this)` called "scope".

When jQuery run a callback she gives that callback with a **reference to the subject of the current action**, this reference is called **callback's scope** and it's available as `this` variable.

Following code:

    $(this).apiMethod()
    
should be read as:

> with the current scope do _apiMethod_

**IMPORTANT:** Callback's scope, more generally **execution scope**, is the second really important concept to understand when coding in jQuery / Javascript.



## Which problem does jQuery solve?

> Well, jQuery provides the developer with a **simple and cross browser API to interact with the [page's DOM](http://en.wikipedia.org/wiki/Document_Object_Model)**.

[jQuery](http://en.wikipedia.org/wiki/JQuery) was released on January 2006 with the explicit scope to **provide a unified API to manipulate the DOM** in different browsers.

> It was the the most fierce period of the [browser war](http://en.wikipedia.org/wiki/Browser_wars) but still IE6 was causing a lot of troubles to many developers.

The simplest operations like add or remove a class name from a _DIV_ were a nightmare of many different implementations, setup a click handler was rocket science for many people.

jQuery allow to select items with a _CSS like_ syntax then apply actions to the selection. Suddenly a huge amount of HTML guys were able to write jQuery code which is much more easy and explicit than pure Javascript.

    // pseudo code
    getThatButton.onClick(... do something ...)
    
    // VanillaJS (pure Javascript)
    var btn = document.getElementById('that-button');
    if (btn.addEventListener) {
        btn.addEventListener('click', function() { ... });
    } else {
        obj.attachEvent('onclick', function() { ... });
    }
    
    // jQuery
    $('#that-button').on('click', function() { ... });



## Download or CDN?

## Any Drawback?

[[footprint size compared to micro libraries or VanillaJS; understand when is worth to use it and when is worth to use alternatives]]

## Fat & Happy VS Thin & Agile

[[talk about full dist vs custom build; benefit of small custom build, links to howtos]]

**\(\*)** Some concepts are explained in a very simple way, sometimes the simple way does not match the correct way 100%.