!SLIDE

# Asset Pipeline

Ruby Tuesday #20 

November 22, 2011

!SLIDE

# about.me/xdite

鄭伊廷 ( xdite@about.me )

Lead Developer / Manager of Techbang

!SLIDE

# Specialties

* Rapid development ( most in Rails )
* Technical training ( most in Ruby / Rails )
* Search Engine Optimization ( SEO )
* Website Scaling
* Website Marketing



!SLIDE

# Techbang

* (3C | Photography | Game ) News Portal
* Taiwan Alexa #67
* powered by Ruby on Rails

!SLIDE

# Techbang

* Responsive Design
* HTML5 semantics
* Asset Pipeline
* …etc.

<div class="footnote">
We are crazy...
</div>

!SLIDE

# Asset Pipeline

* built-in feature since Rails 3.1.0 +
* Asset Framework
* Integrate :
  - SASS / SCSS / Compass
  - CoffeeScript

!SLIDE


# Major Features 

 #1 asset compress / minify for frontend-scaling

!SLIDE


# Major Features 

 #2 write SCSS / CoffeeScript directly

!SLIDE

# Major Features 

 #3 integrate with 3rd party plugin


!SLIDE

# Major Changes

* public/ => assets/
* direct access => serve by Sprockets

!SLIDE

# Sprockets

* Ruby library for compiling and serving web assets.
* declarative dependency management for JavaScript and CSS assets
* Rack middleware

<div class="source">
https://github.com/sstephenson/sprockets
</div>

!SLIDE

# Philosophy

* Fast by Default
* Better way to write CSS / Javascript
* Manage assets more easily
* Leverage 3rd party works


!SLIDE

# Let's talk about SCALING

Fast by Default

!SLIDE

# Frontend Scaling

* C/P value
* Network Latency: 500ms -> 5ms
* DB query: 50ms -> 20ms

!SLIDE

# before Rails 3.1

* Minimize HTTP Requests
* Use a CDN + Split Components Across Domains
* <del>Gzip Components</del>
* <del>Minify JavaScript and CSS</del>
* <del>CSS Sprites</del>

<div class="source">
 Best Practices for Speeding Up Your Web Site http://developer.yahoo.com/performance/rules.html
</div>

!SLIDE smaller

# Minimize HTTP Requests

<pre>
&lt;%= stylesheets_include_tag &quot;aaa&quot;, &quot;bbb&quot;, :cache =&gt; true %&gt;
&lt;%= javascrupt_link_tag &quot;ccc&quot;, &quot;ddd&quot;, :cache =&gt; &quot;customized-functions&quot; %&gt;

</pre>

!SLIDE smaller

# CDN + Split Components Across Domains

<pre>
 config.asset_host = "cdn%d.example.org"
</pre>

* http://cdn0.example.org
* http://cdn1.example.org
* http://cdn2.example.org
* http://cdn3.example.org

!SLIDE

# after Rails 3.1

* Gzip Components ( w/ Sprocket)
* Minify JavaScript and CSS ( w/ Sprockets)
* CSS Sprites ( w/ Compass)

<div class="source">
 Best Practices for Speeding Up Your Web Site http://developer.yahoo.com/performance/rules.html
</div>

!SLIDE

# Let's talk about futures: 
SCSS & CoffeeScript

!SLIDE

# SASS / SCSS / Compass

* `SASS` : from `Haml` project


!SLIDE smaller

# Haml 

<pre>
# Haml
 %ul{:id => "list", :class => "menu"}
    %li= "Item 1"
    %li= "Item 2"
</pre>
<pre>
# HTML
 &lt;ul id=&quot;list&quot; class=&quot;menu&quot;&gt;
      &lt;li&gt;Item 1&lt;/li&gt;
      &lt;li&gt;Item 2&lt;/li&gt;
 &lt;/ul&gt;
</pre>

!SLIDE smaller

# Sass 

<pre>
# SASS
 .content
    margin: 2em 0
    h1
      font-size: 2em
</pre>
<pre>
# CSS
  .content{
    margin: 2em 0;
   }
   .content h1{
      font-size: 2em;
   }
</pre>

!SLIDE smaller

# SCSS (Sassy CSS)
The natural way to write css
<pre>
# SASS
 .content
    margin: 2em 0
    h1
      font-size: 2em
</pre>
<pre>
# SCSS
  .content{
    margin: 2em 0;
    h1 {font-size: 2em }
  }
</pre>

!SLIDE

# Sass / SCSS basics

* Variables
* Nesting
* Mixins
* Selector Inheritance
* CSS3

!SLIDE smaller

# Sass / SCSS advanced

* `extend` : 可將某些已經寫好的樣式，直接套入另外一組樣式中重複使用。
* `mixin` : 可以預先寫好自定要被 mixin 的 function ，需要用時 include 進來
* `import` : 可以把太長的 SCSS 拆開成一個一個的 partial，要用時 import 進來。

!SLIDE smaller

# Compass

* `Sass framework powered by community`
* mixins:
  - Blueprint / 960 / Susy / YUI
* Powerful CSS3 helpers
  - Background Gradients
  - Border radius
  - CSS3 Pie

!SLIDE smaller

# Rules of Writing SCSS

結構變得更加清晰

* by feature
* by special block
* by default block ( header / footer / sidebar )
* by (Rails) controller
* by page specific

!SLIDE

# CoffeeScript

The beautiful way to write Javascript

!SLIDE smaller

# Problems of JavaScript

* JavaScript is a functional language
* JavaScript is an object oriented language, but it's prototype based
* JavaScript is very dynamic and is a lot closer to Lisp than C/Java, but it has a C/Java syntax
* Even JavaScript's name is confusing as JavaScript has very little to do with Java

!SLIDE smaller

## What doest CoffeeScript do?

* 改善 Syntax : JavaScript 目前使用的是與本身型態不搭嘎的 C / Java 語法。<br>
  - CoffeeScript 改採用了深受 Lisp 影響的 `Ruby` + `Python` 的混合語法。


!SLIDE smaller

## What doest CoffeeScript do?


* 借鑑其他語言的好處 : CoffeeScript 從其他語言借了不少好處，寫起來更方便。

<pre>
 # Array ( from `Python`)
 list = [1, 2, 3, 4, 5]
 # list comprehensions 
 cubes = (math.cube num for num in list)
</pre>

<pre>
# String ( from `Ruby`)
author = "Wittgenstein"
quote  = "A picture is a fact. -- #{ author }"
</pre>

!SLIDE smaller

## What doest CoffeeScript do?


* 留下 Good Parts，並在設計上極力消除 JavaScript 原生特性會產生的缺點，例如:
  - 消除到處污染的全域變數
  - Protected code
  - 使用 -> 和 indent(縮排) 讓撰寫 function 更不容易出錯
  - 更容易偵測 syntax error 並攔阻

!SLIDE smaller 

## What doest CoffeeScript do?

* 實作物件導向變簡單了

<pre>
class Animal
  constructor: (@name) ->

  move: (meters) ->
    alert @name + " moved #{meters}m."

class Horse extends Animal
  move: ->
    alert "Galloping..."
    super 45

sam = new Horse "Sammy the Python"
sam.move()
</pre>

!SLIDE smaller

## What doest CoffeeScript do?

* 也更好寫測試了…
* [ 抱歉沒有 code，因為我實在懶得寫測試 XD ]


!SLIDE 

## Asset Pipeline

This is the future!

!SLIDE

## Asset Organization

* app/assets
* lib/assets 
* vendor/assets.

!SLIDE

## DHH in RailsConf 2001

* `empty folders` and `empty files` are two of `the pivotal innovations` in Rails that have encouraged us to `write clean applications` since the framework appeared.

* With `clean folders`, though, people will `think more carefully about where they put things`. 

!SLIDE

## One more thing…

Asset as Gem

!SLIDE

## Asset As Gem

`Rails Engine`

<pre>
├── lib
│   └── bootstrap 
│       
└── vendor
    └── assets
        ├── javascripts
        └── stylesheets
</pre>

!SLIDE

## Asset As Gem

require from 'jquery-rails'

<pre>
//= require jquery
//= require jquery_ujs
</pre>

require from 'bootstrap'
<pre>
//= require bootstrap
</pre>

!SLIDE smaller

# Conclusion

* JavaScript and CSS have been treated as `'second class citizens'` and considered `less important` to get right structurally than the Ruby code. 

* Asset Pipeline force developers to organize codes.

!SLIDE smaller

# Conclusion

乾淨整潔的架構是否能夠影響程式設計師，專注在設計出更棒更創新的程式碼？


!SLIDE 

# Q & A

我知道大家一定有很多問題，歡迎舉手問...