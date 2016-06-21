#Emmet Tutorial, Meteor NYC Meetup, Tuesday, June 21, 2016
##The Basics

####Type what you want, press <TAB> for Emmet magic :D--
    
    `div<TAB>` (expands to) `<div></div>`
    `p<TAB>` (expands to) `<p></p>`
  
    `custom-block<TAB>` (expands to) `<custom-block></custom-block>`

    (Maybe for those Angular fans)

    `like-button<TAB>` (expands to) `<like-button></like-button>`

###Something a bit more useful
####A div with a class

    `div.class<TAB>` (expands to) `<div class="class"></div>`

####A div with an id

    `div#cool-id<TAB>` (expands to) `<div id="cool-id"></div>`

####A Div with both

    `div#cool-id.class<TAB>` (expands to) `<div id="cool-id" class="class"></div>`

####Insanity 

    `div.this.is.an.insane.demonstaration.of.emmet#itreallyworks<TAB>`
      (expands to) 
    `<div class="this is an insane demonstaration of emmet" id="itreallyworks"></div>`

####For Meteor (Blaze)

    Custom attributes are wrapped in [Brackets] like:

    `div.cool-class[ng-repeat="angular-stuff"]<TAB>` (expands to) 
    `<div class="cool-class" ng-repeat="angular-stuff"></div>`

####A Blaze example:

    `template[name=templateName].class-name#top-item <TAB>` (expands to) 

    `<template name="templateName" class="class-name" id="top-item"></template>` 

###Nesting!

You can easily create nested block with the ">" character.  For example:
    
    `div>p <TAB>` (expands to) 
    ```html
    <div>
        <p></p>
    </div>
    ```
    Useful for Meteor as in:

    `template[name=templateName]>div.row>p.paragraph <TAB>` (expands to):
    ```html
    <template name="templateName">
        <div class="row">
            <p class="paragraph"></p>
        </div>
    </template>
    ```html

    Nesting with multiplier:
    
    `div.test>ul.the-list>li.the-item*5<TAB>` (expands to):
    
    ```html
    <div class="test">
        <ul class="the-list">
            <li class="the-item"></li>
            <li class="the-item"></li>
            <li class="the-item"></li>
            <li class="the-item"></li>
            <li class="the-item"></li>
        </ul>
    </div>
    ```
    (Side note: the * operator multiplies things.  Like p*8 turns to:)
    ```html
    
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    <p></p>
    ```
###Siblings and Climbing

    Sometimes you don't just want to nest.  You can create elements at the same DOM level with the "+" operator and climb to a previous level with the "^" operator 
    (one DOM level climbed per caret.)  Examples:
    
    ```
    div.container>div.header+div.menubar+div.content-area 
    ```
    will expand to:
    ```html
    <div class="container">
        <div class="header"></div>
        <div class="menubar"></div>
        <div class="content-area"></div>
    </div>
    ```
    ```
    div.container>div.headder>div.menubar+div.logo^div.content+div.article 
    ```
    will expand to:
    ```html
    <div class="container">
        <div class="headder">
            <div class="menubar"></div>
            <div class="logo"></div>
        </div>
        <div class="content"></div>
        <div class="article"></div>
    </div> 
    ```
    Grouping:
    
    You can use parens to group elements and ensure everything is nested properly with multiplication, like:
    ```
    div.class>ul.list>(a>li.item)*5
    ```
    expands to:
    ```html
    <div class="class">
        <ul class="list">
            <a href="">
                <li class="item"></li>
            </a>
            <a href="">
                <li class="item"></li>
            </a>
            <a href="">
                <li class="item"></li>
            </a>
            <a href="">
                <li class="item"></li>
            </a>
            <a href="">
                <li class="item"></li>
            </a>
        </ul>
    </div>
    ```
    Without Parens: 
    ```
    div.class>ul.list>a>li.item*5
    ```
    Expands to:
    ```html
    <div class="class">
        <ul class="list"><a href="">
                <li class="item"></li>
                <li class="item"></li>
                <li class="item"></li>
                <li class="item"></li>
                <li class="item"></li>
            </a></ul>
    </div>
    ```
    Ugh! Not what we wanted.  Use the parens!  :D
    
###Ailases

    Boilerplate HTML5 page:
    
    `html:5 <TAB>`
    
    `meta:vp <TAB>`
        
    ...SO MANY MORE (see resources below)
    
    
##CRAZY EXAMPLE
```
div.container>div.header>(div.header+div.menu+div.menu+div.top-social-media)^div.body>(div.left-menu>ul.left-menu>(a>li.left-menu-item)*10)>div.content>(div[ng-repeat="article in articles"]>(a>h1.article-title^p.article+div.comments))^^div.footer>div.bottom-social+div.copyright
```
        
    WILL EXPAND TO:    
 ```html   
<div class="container">
    <div class="header">
        <div class="header"></div>
        <div class="menu"></div>
        <div class="menu"></div>
        <div class="top-social-media"></div>
    </div>
    <div class="body">
        <div class="left-menu">
            <ul class="left-menu">
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
                <a href="">
                    <li class="left-menu-item"></li>
                </a>
            </ul>
        </div>
        <div class="content">
            <div ng-repeat="article in articles">
                <a href="">
                    <h1 class="article-title"></h1></a>
                <p class="article"></p>
                <div class="comments"></div>
            </div>
        </div>
        <div class="footer">
            <div class="bottom-social"></div>
            <div class="copyright"></div>
        </div>
    </div>
</div>
```


###Resources

http://emmet.io/

THE BIBLE: http://docs.emmet.io/cheat-sheet/

http://docs.emmet.io/

https://www.udemy.com/emmet-start-coding-html-and-css-fast-and-easy/ (FREE)

Emmet also works with JSX in Sublime:
http://wesbos.com/emmet-react-jsx-sublime/


HAVE SOME FUN :D
