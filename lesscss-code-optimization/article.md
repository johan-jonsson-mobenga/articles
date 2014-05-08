# LessCSS Code Optimization
---

I use LessCss as **CSS preprocessor** in my every day projects and I really like the
benefits I gain from a developing time perspective. **I can't work without it anymore!**

> Unfortunately CSS preprocessors are not known to generate optimised CSS code!

There are a lot of discussions around this argument and the most often 
given answer is something like:

> - Preprocessors are not optimization tools
> - If you write bad LessCss then you obtain bad CSS

**I could not agree more!**

This article is about to point out the problem and **to present a possible _LessCss_ 
best practice** in order **to generate optimised CSS** code out of the box.

## Given Real Problem:

The following LessCss source code represent a classic multi-file approach where **different 
responsabilities are spreaded into many source files**.


    // structure.less
    .btn {
        display:block;
        border: 2px solid black;
    }
    
    // colors.less
    .btn {
        background: #ddd;
        color: #444;
        text-shadow: 0 1px 0 #fff;
    }
    
    // font.less
    .btn {
        font-family: Tahoma;
        font-size: 14pt;
    }
    
The generated code is far to be good!

    .btn {
        display: block;
        border: 2px solid black;
    }
    .btn {
        background: #ddd;
        color: #444;
        text-shadow: 0 1px 0 #fff;
    }
    .btn {
        font-family: Tahoma;
        font-size: 14pt;
    }

[Play with this code!](http://codepen.io/mpeg/pen/fnzwc)

> The same selector `.btn` is repeated over and over again causing the 
> browser to resolve the _xpath_ many times. 

Code above is really slow to render <small>(ok, it's slow from a CSS rendering perspective!)</small>, but you can figure out the consequenques of this approach 
extended to a real project stylesheet!

> I wish to compact all these instructions into a single selector like the following:

    .btn {
        display: block;
        border: 2px solid black;
        background: #ddd;
        color: #444;
        text-shadow: 0 1px 0 #fff;
        font-family: Tahoma;
        font-size: 14pt;
    }

## Here Is a Possible Solution:

The way I propose to solve this problem combines two preprocessor concepts:

- [non outputting mixins](http://lesscss.org/features/#mixins-feature-not-outputting-the-mixin)
- [extend inside ruleset](http://lesscss.org/features/#extend-feature-extend-inside-ruleset)

The goal is to write a non outputting mixin, extend it serveral times and apply it to a single
selector only when every other manipulations are over.


    // classes.less
    .classBtn() {}
    
    // structure.less
    .classBtn() {
        &:extend(.classBtn);
        display:block;
        border: 2px solid black;
    }
    
    // colors.less
    .classBtn() {
        &:extend(.classBtn);
        background: #ddd;
        color: #444;
        text-shadow: 0 1px 0 #fff;
    }
    
    // fontx.less
    .classBtn() {
        &:extend(.classBtn);
        font-family: Tahoma;
        font-size: 14pt;
    }
    
    // selectors.less
    .btn {
        .classBtn;
    }
    
The generated code looks exactly how I wished:

    .btn {
        display: block;
        border: 2px solid black;
        background: #ddd;
        color: #444;
        text-shadow: 0 1px 0 #fff;
        font-family: Tahoma;
        font-size: 14pt;
    }

### Live Examples

- [Unoptimised](http://codepen.io/mpeg/pen/fnzwc) - standard _Less_ code
- [Optimised](http://codepen.io/mpeg/pen/bmztk) - exploit _Less_ features to produce nice CSS code!

## Preprocessors Are Not Optimisation Tools!

When it comes to **CSS code optimisation** all the major CSS preprocessors sucks a lot.

None of them are able to run the minimal amount of optimisation like removing overridden properties or packing many instances of the same selector.

**I think this is the right behavior of such kind of tools!**

> They are preprocessor, not optimisation tools!

Nevertheless preprocessors give the developer a lot of powers over the basic CSS standard: you can nest selectors, you can use variables, mixins... 

> With great powers comes great responsibility  
> <small>Francois-Marie Arouet (Voltaire)</small>

When you decide to use a preprocessor then you start learning it's rules and features.  
**Very seldom you study about the risk in using them!**

Well, the risk in using (or abusing) preprocessors are in the generated CSS performances, or in the **defect of performances!** 

- code repetition
- deep selectors
- verbose selectors

All of these are possible **causes of bad CSS performances** and must be well understood and considered when it comes to write CSS for a complex page or WebApp!

### Live Examples

You can see what I'm talking about in these simple Codepen examples.

I explicitly wrote some code repetition and I can observe that nothing is done by the preprocessor to optimise my code:

- [LessCss Test](http://codepen.io/mpeg/pen/JjrED)
- [SASS Test](http://codepen.io/mpeg/pen/gliCH)
- [Stylus Test](http://codepen.io/mpeg/pen/HpefF)
