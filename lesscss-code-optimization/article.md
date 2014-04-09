LessCSS Code Optimization
=========================

I use _LessCss_ as **_CSS_ preprocessor** in my every day projects and I really like the
benefits I gain from a developing time perspective. **I can't work without it anymore!**

> Unfortunately _CSS_ preprocessors are not known to generate optimised _CSS_ code!

There are a lot of discussions around this argument and the most often 
given answer is something like:

> - Preprocessors are not optimization tools
> - If you write bad _LessCss_ then you obtain bad _CSS_

**I could not agree more!**

This article is about to point out the problem and **to present a possible _LessCss_ 
best practice** in order **to generate optimised _CSS_** code out of the box.

## Given Real Problem:

The following _LessCss_ source code represent a classic multi-file approach where **different 
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
- [Optimised](http://codepen.io/mpeg/pen/bmztk) - exploit _Less_ features to produce nice _CSS_ code!

## Post Processors Are Not So Good!