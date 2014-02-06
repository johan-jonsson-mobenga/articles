Everithing Is A Box
===================

When you first approach the art of **converting a design to a web page**
you really need to **understand that everything is a box**. 

I really mean it, for both web design and the real world outside 
your window. Take a look!

> &raquo; **with HTML** we are going to use `div` to represent boxes.
> 
> A `div` is normally rendered as a real squared or rectangular area on 
> browser's page so the concept of _"BOX"_ is a good metaphor to use in web design.
> <small>(and computer science)</small>

## Simplify It!

Every complex image or object from reality should be simplified to a set of boxes 
which are in relation one to each others.

<img src="./fig01-the-human-body.jpg" alt="fig01 - The Human Body" width="250px" />

The image above display a person (I really tried to draw a person!) which is a
very complex object from the real world.

I’m far to understand how the human body works but I can move a step 
toward that knowledge by simplify the problem. I should say:

- my HEAD is responsible of getting food
- my BODY is responsible of using food to make power
- my LEGS are responsible of using power to bring me seeking for food

I still far to fully comprehend the human body but I can happily affirm
that now I know something more than before. 

> Remember: **to solve a problem** is very a different job than 
> **to find a solution** for that problem!




## Relations Between Boxes

As soon as you begin to simplify complex objects into boxes you discover **you need to describe the relation** from one box to the others. 

> Remember we are talking about to cut a graphic image into a _web page_!   
> **We are not making rocket science here!**

Luckily there are very few way we can organize boxes, the first two of them I call **strong relations**, the last one I call **soft relation**.

A **strong relation** exists since the box is being created and **can't change**: 

> I was born **before** my brother, there is no way to change this **order relation**.

A **soft relation** concern the appeareance of things and **should change in time**.

> Today **I'm more fat** than my brother but I really can put all my effort to 
> change this **soft relation**!

Moving the discussion to _web design_, which is the subject of this paper, we can say:

> - strong relations are built within **HTML**
> - soft relations are built within **CSS**



### Parent / Child - Nesting Relation

The _parent / child_ relation define **who contains who**.

`Box A` should contain `Box B`, so i can say:

- `Box A` is `Box B`'s **CONTAINER**
- `Box B` is `Box A`'s **CONTENT**

<img src="./fig02-parent-child.jpg" alt="fig02 - Parent / Child Relation" width="250px" />


It's important to understand than **one box can have one and only one container** like a human being should have one and only one biological father.

> Luke, I am your father!  
> <small>(Darth Vader)</small>

It is always simple and quite natural for a box to identify it's container.

    // parent / child example
    <div id="box1">
        <div id="box2"></div>
    </div>
    
Looking at the code above is quite simple to understand that:

- `#box1` is the **parent** of `#box2`
- `#box2` is the **child** of `#box1`

> A good use of **code indentation** make the _parent / child_ relation ridicolous explicit!


### Before / After - Order Relation

On the other side a box should contain many other boxes.  
To be able to identify one particolar box between those contained I should say:

> _"Give me the `box N.3` from `BoxA`"_

We use this is the second _strong relation_ to simplify a complex object into a lists of simple boxes.

This **order relation** is something related with the **importance of a box**.  
<small>The more important is the first it come.</small>

> If you think to your bedroom's chest then the "first drawer" is also the first box 
> which have been placed inside it.

<img src="./fig03-before-after.jpg" alt="fig03 - Before / After Relation" width="250px" />

Given a box you can use this relation **to identify adjacent boxes**.

    // before / after example
    <div id="chest1">
        <div id="box1"></div>
        <div id="box2"></div>
        <div id="box3"></div>
    </div>
    <div id="chest2">
        <div id="box4"></div>
        <div id="box5"></div>
    </div>
    
Looking at the code above is quite simple to understand that:

- `#box1` precede `#box2` (before)
- `#box3` follow `#box2` (after)
- `#box2` is preceded by `#box1` and followed by `#box3`
- `#box1` and `#box3` are siblings of `#box2`
- `#chest1` precede `#chest2`
- `#box3` and `#box4` has ho _direct_ strong relations!

> Thanks to **code indentation** it's easy to detect the _order relation_ among items 
> which share the same container because **they are on the same code column**!


### Left / Right - Layout Order

The _left / right_ relation is a **soft relation** because regards **how boxes are arranged into an horizontal space** which is not a strong hierarchical organization. 

> In _web design_ we use this relation to implement **layouts**.

It is really important to understand that _left / right_ relation **does not depend** on _before / after_ relation. It is a relation which i**s built upon visual rules** such CSS rules:

<img src="./fig04-left-right.jpg" alt="fig03 - Before / After Relation" />

Image above show how a strong _before / after_ relation (on the left) should be arranged in two different _left / right_ relations.

> A change in a _left / right_ relation should never affect an existing _before / after_ relation!

    // left / right example
    <div id="chest1">
        <div id="box1" style="float:left"></div>
        <div id="box2" style="float:right"></div>
    </div>
    
    // right / left example
    <div id="chest1">
        <div id="box1" style="float:right"></div>
        <div id="box2" style="float:left"></div>
    </div>

Code above show how the HTML structure of the two different implementation does not change. Both _nesting_ and _order_ relations still, **only _CSS_'s _style_ attribute change**.





## Rows or Columns?

> Because we are dealing with a browser, then life it's really easy for us!  
> <small>(at least at the analysis level!)</small>

All browsers use a really simple metaphor to render contents to the screen: [the Box Model](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model).

This fact means that we need **to simplify the complex designs to a list of boxes and relations between boxes**.

We already learned about which relations should exists between boxes, now it's time to take a shortcut **to cut off our analysis time**.

> Every box's contents should be arranged in only one way:  
> **or ROWS or COLUMNS**!

<img src="./fig05-rows-columns.jpg" alt="fig05 - rows OR columns" width="400px" />

There is no way for a browser to render a mix of rows and columns, all we have to do to convert a design to an HTML is to:

- identify the bigger box within the design
- understand if it contains rows or columns
- draw all child boxes
- **repeat the analysis for each child box**

<img src="./fig6-analysis.jpg" alt="fig05 - rows OR columns" width="600px" />

Image above show how we can simplify a complex web design to a list of boxes level by level.

In the **first level** we can identify two lines which slice the image into three rows. Then we **step into the first row** and we analyze that logo and menu are **two boxes placed one beside the other**, the logo is on the left hand, the menu on the right hand. Then we **move into the secondo row** of the first level ...

    // page structure with strong relations
    <div>
      <div>
        <div>LOGO</div>
        <div>MENU</div>
      </div>
      <div>
        <div>ARTICLE</div>
        <div>SIDEBAR</div>
      </div>
      <div>
        <div>INFO</div>
        <div>INFO</div>
        <div>INFO</div>
        <div>INFO</div>
      </div>
    </div>

Code above show how we can convert a design analysis into an [_HTML source code_ (open example)](./01-strong-relations.html). So far we are dscribing with _HTML tags_ the boxes and the _strong relations_ which exists between those boxes.

> **At this step we take care of:**
> 
> - nesting childs into containers 
> - to give the right order to siblings boxes

**IMPORTANT:**  
brake down your temptation to assign classes and use more refined _HTML5 tags_.  
So far **you must focus only on strong relations** and the very bare structure of the page.  
<small>This is **WHY** we use only _DIVs_ in this step!</small>

## Group Boxes by Properties

So far we've built the [basic structure of our web page](./01-strong-relations.html) with which we simplified the _graphic design_ into boxes. This page structure implements the _strong relations_ which exist between these boxes.

Now it's time to look another time to the layout analysis we did before.  
**This time we focus on _soft relations_ which exists between boxes**.

<img src="./fig6-analysis.jpg" alt="fig05 - rows OR columns" width="600px" />

Looking with focus to the third image we can write following assertion for sure:

- `LOGO`, `MAIN-CONTENT` and `INFO` boxes implement a **left behavior** 
- `MENU` and `SIDEBAR` implement a **right behavior**
- `LOGO` and `SIDEBAR` share the same dimension 
- `MENU` and `MAIN-CONTENT` share the same dimension 
- all `INFO` box share the same dimension

Each assertion represent a specific behavior which apply to one or more boxes.  
We can name these behavios:

- **place-left:** `LOGO`, `MAIN-CONTENT` and `INFO` boxes implement a **left behavior** 
- **place-right:** `MENU` and `SIDEBAR` implement a **right behavior**
- **size-a:** `LOGO` and `SIDEBAR` share the same dimension 
- **size-b:** `MENU` and `MAIN-CONTENT` share the same dimension 
- **size-c:** all `INFO` box share the same dimension

> **BEHAVIORS LIST:**  
> This is called "behaviors list" and it contains the **full instructions 
> on how to build your boxes**. 
>
> We also **gave a short but meaningful name to each behavior**, from now 
> on we'll use the short name to refer to each behavior. 

> This way we **cut out any misunderstanding in communications** between team members.


Stepping into the _HTML code_ we wrote we can use these **behavior names as _CLASSES_** for our _DIVs_:

    // page structure with soft relations
    <div class="main-container">
      <div>
        <div class="place-left size-a">LOGO</div>
        <div class="place-right size-b">MENU</div>
      </div>
      <div>
        <div class="place-left size-b">ARTICLE</div>
        <div class="place-right size-a">SIDEBAR</div>
      </div>
      <div>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
      </div>
    </div>

> If you [open the example page](./02-soft-relations.html) you should notice that 
> it still looks bad: no visual changes had been applied yet. 
> This is because **_soft relations_ needs the support of a _CSS_** to be rendered 
> by the browser! We're almost about to write it.

### What did we gained so far?

So far we have a very clear page structure where some box are grouped by _class_, and we have a straightforward list which exposes, beyond any doubt, which behavior is to be applied to each group.

> We are playing with boxes and labels and we keep a legend of each label's meaning

If a change is introduced to the design then we can easily understand what kind of relations are involved. 

> _HTML_ code still be very simple because **it contains only the knowledge about relations**.




## What's Your Pourpose?

We know we are dealing with _HTML5_ and we know that exists many _tags_ which objective is to **explicit a particular pourpose for a particular box**.

Some _tags_ are straightforward: to implement a _link_ you must use an `<A href="...">` tag,  some others are slightly more subtle. To implement a _sidebar_ you can use many tags:

- `ARTICLE` which is very wrong
- `ASIDE` which is very correct
- `DIV` which is not wront neither correct

The concept of _correct_ and _wrong_ are tied to the **deep meaning of a tag**:

- an `ARTICLE` tag adds a meaning to it's contents: _"my content is an article"_
- a `ASIDE` tag means: _"my content is not really the main content of this page, please consider it only as contour of the real content"_
- ... and so on ...

[You can find a list of HTML5 tags and meanings here](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5/HTML5_element_list)

Because our _HTML code_ still very dry it is not the perfect moment to improve it switching from the generic `DIV` to some more precise tag where necessary:

    // meaningful tags:
    <div class="main-container">
      <header>
        <div class="place-left size-a">LOGO</div>
        <nav class="place-right size-b">MENU</nav>
      </header>
      <main>
        <article class="place-left size-b">ARTICLE</article>
        <aside class="place-right size-a">SIDEBAR</aside>
      </main>
      <section>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
        <div class="place-left size-c">INFO</div>
      </section>
    </div>
    
> If you [open the example page](./03-meaningful-tags.html) you should notice that 
> it still looks bad: no visual changes had been applied yet. 
> This is because **_soft relations_ needs the support of a _CSS_** to be rendered 
> by the browser! We're almost about to write it.

### What did we gained so far?

If you approach your daily job asking yourself _**"why am I doing that?"**_ like I do then you'll find out that to use the most representative and meaningful tags to build your page structure is the only way to do that job.

You really can't use generic or semantic wrong tags. If you still **focusing on the deep meaning** of what you are doing then **you should feel horrified** of the idea to use an `ARTICLE` instead of an `ASIDE`!!!

To deep understand this point give you the _"to be horrified"_ feeling about semantic errors:  
**you won't be able to be mistaken again!**

Sideway this is a very important **internal Search Engine Optimization**: search engines always search to give the text the right meaning to provide more _to-the-point_ search results. 

**_HTML5 Semantic Tags_ are the tool to give the right meanings to the right contents.**

> Both _Google_ and your customer will appreciate your job!



## Paint the Walls

Now it's time to apply some _"painting"_ to out _HTML_ structure.

We've already **analyzed and gived names** to all our boxes behaviors 
- do you remember the _behaviors list_? - so now we only have to solve a simple 
_CSS_ job by **translating each behavior to a CSS definition**:

    .main-container {
      width: 600px;
      margin: auto;
    }
    .place-left {
      float:left;
    }
    .place-right {
      float:right;
    }
    .size-a {
      width: 200px;
    }
    .size-b {
      width: 380px;
    }
    .size-c {
      width: 140px;
    }
    
[open this example](./04-css-styles.html)

Code above represents the bare minimal instructions which translates our
    
need some fix up classes

    <header class="clearfix">
      ...
    </div>
    <main class="clearfix">
      ...
    </div>
    <section class="clearfix">
      ...
    </div>
    
implement floating fix up

    .clearfix:after {
      display:block;
      content: ' ';
      clear:both;
    }
    
[open this example](./05-clearfix.html)
