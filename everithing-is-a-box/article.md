Everithing Is A Box
===================

When you first approach the art of **converting a design to a web page**
you really need to **understand that everything is a box**. 

I really mean it, for both web design and the real world outside 
your window. Take a look!

> &raquo; **with HTML:**  
> We are going to use `div` to represent boxes.
> 
> A `div` is normally rendered as a real squared or rectangular area on 
> browser's page so the concept of _"BOX"_ is a good metaphor to use in web design.

## Simplify It!

Every complex image or object from reality should be simplified to a set of boxes 
which are in relation one to each others.

<img src="./fig01-the-human-body.jpg" alt="fig01 - The Human Body" width="250px" />

The image above display a person (I really tried to draw a person!) which is a
very complex object from the real world.

I’m far to understand how the human body works but I can move a step 
toward that knowledge by simplify the problem, I should say:

- my HEAD is responsible of getting food
- my BODY is responsible of using food to make power
- my LEGS are responsible of using power to bring me seeking for food

I still far to fully comprehend the human body but I can happily affirm
that now I know something more than before. 

> Remember: **to solve a problem** is very a different job than 
> **to find a solution** for that problem!




## Relations Between Boxes

As soon as you begin to simplify complex objects into boxes you discover **you need to describe the relation** from one box to the others.

Luckily there are very few way we can organize boxes, the first two of them I call **strong relations**, the last one I call **soft relation**.

A **strong relation** exists since the box is being created and **can't change**: 

> I was born **before** my brother, this **order relation** will never change.

A **soft relation** concern the appeareance of things and **should change in time**.

> Today **I'm more fat** than my brother but I really put all my effort to 
> change this **soft relation**!

Moving the discussion to _web design_, which is the subject of this paper, we can say:

- strong relations are build with HTML
- soft relations are built with CSS



### Parent / Child

The _parent / child_ relation define **who contains who**.

`Box A` should contain `Box B` so i can say:

- `Box A` is `Box B`'s **container**
- `Box B` is `Box A`'s **content**

<img src="./fig02-parent-child.jpg" alt="fig02 - Parent / Child Relation" width="250px" />


It's important to understand than **one box can have one and only one container**.  
It is always simple and quite natural for a box to identify it's container.

    // parent / child example
    <div id="box1">
        <div id="box2"></div>
    </div>
    
Looking at the code above is quite simple to understand that:

- `#box1` is the **parent** of `#box2`
- `#box2` is the **child** of `#box1`

> A good use of **code indentation** make the _parent / child_ relation ridicolous explicit!


### Before / After

On the other side a box should contain many other boxes.  
To be able to identify one particolar box between those contained I should say:

> _"Give me the `box N.3` from `BoxA`"_

This is the second _strong relation_ we use to simplify a complex object into simple boxes.

This **order relation** is something related with the birth of the box. 

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

- `#box1` precede (before) `#box2`
- `#box3` follow (after) `#box2`
- `#box2` is preceded by `#box1` and followed by `#box3`
- `#chest1` preced `#chest2`
- **`#box3` and `#box4` has ho strong relations!**

> Thanks to **code indentation** it's easy to detect this relation among items 
> which share the same container because **they are on the same column**!


### Left / Right

The _left / right_ relation is a **soft relation** because regards **how boxes are arranged into an horizontal space** which is not a natural hierarchical organization.

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





## Rows or Columns?

> Because we are dealing with a browser, then life it's really easy for us!  
> <small>(at least at the beginning!)</small>

Every browsers use a really simple metaphor to render a graphic to the screen of our computers: [the Box Model](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model).
This fact means that we need **to simplify the complex design to a list of boxes and relations** between boxes.

We already learn about which relations should exists between boxes, now it's time to take a shortcut off our analysis time.

> Every box's contents should be arranged in only one way: **OR rows OR columns**!

<img src="./fig05-rows-columns.jpg" alt="fig05 - rows OR columns" width="400px" />

There is no way for a browser to render a mix of rows and columns, all we have to do to convert a design to an HTML is to:

- identify the bigger box within the design
- understand if it contains rows or columns
- draw all child boxes
- **repeat for each identified box**

<img src="./fig6-analysis.jpg" alt="fig05 - rows OR columns" width="600px" />




