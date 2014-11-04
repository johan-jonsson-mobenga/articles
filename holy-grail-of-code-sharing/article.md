# The Holy Grail of Code Sharing
---

## Our Problem

I work in a service company whose core business is mobile web applications development. 

> We sell development time to customers who **know what but not how to** do business with mobile devices.

We are 130 programmers divided in teams of 6 to 10 guys. Each group is highly committed to it's project and we suffer high time pressure to fulfill our customer expectations.

Projects around the company are not that different, we do tailored based customisations of a shared service, much like a classic web agency company producing custom websites.

> Today there is **close to zero code sharing** around our teams and this fact costs
> a lot of money to the company.

We are a service company and **our trading value is delopers time**.  
When two teams solve the same problem in two different ways they spend the double of the time. 

> And when you sell services the rule of thumb is fairly easy:  
> **"the double the time the half the revenue"**

To share code across teams appear to be the obvious and easy solution to our problem, but **it turned to not being so easy** to really implement code sharing the proper way.

## Our Struggle

Our product is a quite complex mobile web application so we proposed **to split the requirements into smaller chunks** that could be reusable and customisable by many teams.

> We called those chunks _Features_ and for the pourpose of this article you can think to features as _Login_, _Payment_, _Articles_, ...

A _Feature_ is a quite big part of the entire application that **implements a single responsibility** like loggin-in users or make them pay some cash. It's smaller compared to the whole app but still quite of a big thing.

After some hard thinking we came up with a good understanding of the _Features_ that were involved in our apps and we were extremely happy and proud when **we proposed the company to reorganize our developers into _Feature Teams_** whose task is to implement a specific _Feature_ to be reausable by others.

This solution **was hard to hear and accept by management** because involved dramatically change into the company's structure and business model.

> _Feature Teams_ was just a dead end.

Our second approach was drived by the hard boundary to **do not change the company structure**.  
<small>(We learned that lesson the hard way)</small>

Long story short we proposed to let our teams doing their job and to create a side team of experts whose duty is to **take existing custom code and _change it to be more reusable_**.

This time we have also been target of jokes and laughter around the concept of "_more reusable_". What does it mean? I still don't know.

> The third time you try, you are like to succeed.  
> <small>If you are humbe enough to learn from your mistakes</small>

## Our Solution

Our final and succesfull approach was to discard _high accademic thinkings_ and to go straight down to the core of our daily job.

> we do not just write code,  
> **we do solve problems with code!** 

So, insted of sticky ourself in struggling with code sharing we moved on and began to **analyze where were we wasing time** within the company.

> The most time expensive moment in every developer's day is called **_WTF_**.  
> <small>_(What The Fuck)_</small>  
> 
> <small>This is not a bad or unpolite expression. This is the technical name of the worst nightmare of every man or women involved in the process of solving problems with code.</small>

Our **first action point** was to put small and cross-team groups of developers into a room on a weekly basys with the only objective **to share _WTF_ stories**. 

To tell to your mates **were did you find troubles and how did you solve it** is not only about the code you wrote. It is all about the tools you used: 

* search engines queries
* articles, books, blogs & forums
* colleagues that knew that s***

The second action point was to **raise the culture of enterprise code writing**.

_Enterprise Code Writing_ is nothing more than a little group of best practices that we can use when it comes to write code among 130 people, i can list some here:

* single responsibility principle
* open source first
* readability first
* why &raquo; how &raquo; code

This bullet list is made on some fancy expressions, but I have to use them in this article because each of them is worth an entire book.

> The general principle that should drive each of us is:  
> **Don't do bullshit!**

* to build a big module is way more expensive than to code little ones that can work together
* to write my own DOM library is way more time consuming compared to use a jQuery custom build
* to write my own knowledge base about Javascript is just not the way, I can search, read and link valuable articles that are already available online

All **those examples are surprisingly difficult to achive** when it comes to developers, 
the more proud and stubborn people in the planet!  
<small>(and as matter of fact I am one of them!)</small>

## Our Path

When it comes to practical coding we have a simple action point which is **micro coding**.

We left the idea of coding complete and reusable _Features_ way behind us. Today we focus in **writing the less possible amount of code** for the smallest possible of the responsibilies. And we share that.

> Each function, source file or module must solve one single problem, no more than one.

By just doing that our developers have began to **produce reusable code from the very first day of the change**, without introducing any new tool in their chain.

At the beginning we used a simple [DropBox shared folder](dbox) to share our micro libraries, today we evolved a little bit when we introduced our second action point.

Our second practical action point is **Open Source First**.

> If the solutions exists among the Open Source community we use it,  
> if we create our own solution, we publish it back for others to use.

Today we use [CommonJS](commonjs) and [NPM](npm) to write our Javascript, if we need a library we search _NPM_ or _GitHub_, if it exists we use it, if it exists on _GitHub_ but it is not available through _NPM_ we contribute to the project to fix it, then we use through _NPM_.

This behaviour is much more than a merely _giving back to the community_.  

> By actively publish open source code **we get free help from the community** that
> contributes to our repositories by doing bug-traking, bug-fixing and code enhancement.

For writing CSS we embrace the [Object Oriented CSS](oocss) and we use [LessCss](less) to build them, to easy cross-browser we choosed [LessHat](lesshat) which is quite simple and complete.

The third and most important action point was to **challenge our developers**.

> There is nothing better than prizes to light up your willing of doing!

So we introduced **cross team challenges**: groups of 3-4 people from different teams were competing to produce some fun apps or little games. 

The prize was always quite impressive and at the very beginning some managers had an heart attack about that.

> We have a play-room so we created a _ChallengeME_ app to invite a colleague to the 
> table tennis, we do afterworks so we suggested a _PubRating_ app internal 
> to the company... and much more!

Eventually the learning effort that every developer put into **the challenge was affecting the quality of his daily job** so much than no other money could have ever bought this accomplishment!

The best of it is that **we exploited the proudness and stubborness** which is natural in each developer to play a foundamental and positive role within the company: 

> When a developer learn better implementations he can not accept to see legacy code 
> anymore so **he/she coach other colleagues to improve**. For free!

## Conclusions

Today my company is a better place to work, the quality have increased so much and eventually we start to have some really great accomplishments around code sharing and reusability.

We are also planning to move more into a product business model, we can do that today because we have the culture of enterprise coding and reusability built into every one of our developers.

During the last year a great guy left the company because his **improvements were public on _GitHub_** and he was head hunted by one of our direct competitors. 

This is good, he will learn even more from them but he can not stop to hanging out with his old mates, they have become friends through this experience, so **all the knowledge is coming back to us**!

> We started this experience more than one year ago, we faced the problem, 
> we spiked some dead ends but eventually we made it. It took some time but it was worth to.

What we learned is that **code sharing is not about tools but about culture**, is about people and knowledge, is about sharing the objective to spare some time from our daily struggles and use it in a more fun and proficient way.

## Links

* [dbox] https://www.dropbox.com
* [commonjs] http://wiki.commonjs.org/wiki/CommonJS
* [oocss] http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/
* [less] http://lesscss.org/
* [lesshat] http://lesshat.madebysource.com/