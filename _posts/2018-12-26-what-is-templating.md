---
layout: post
title: What is a Templating Engine?
---
## Overview
* What is a templating engine?
* Types of templating engines
* Why use templating engines?
* What are drawbacks of using a templating engine?
* How do templating engines relate to these other web technologies I hear about?
* What would my code look like without a templating engine?
* What are some different templating engines?

I came across this as I read through Google App Engine docs:

> Since HTML that is embedded in code can be difficult to maintain, you should use a templating system, storing HTML
> in a separate file that uses special syntax to specify where the data returned from an application appears.
> You can use your template engine of choice by bundling it with your application code. For your convenience,
> App Engine includes the Django and Jinja2 templating engines.
>
> From [Google App Engine Getting Started Guide](https://cloud.google.com/appengine/docs/standard/python/getting-started/python-standard-env?csw=1)

## So what is a templating engine?
Templates are text documents that contain a mix of static content and blocks of dynamic content. A templating engine
takes the template plus some data values and replaces the dynamic blocks within the template with the data. The rules
that determine how the input data values are mapped into the various dynamic content blocks are either defined within
the template. Templates can have simple variable - value substitution. Some templates can also specify logic like
conditionals or loops that is used to generate the template output.

Templating engines can be used to generate many different kinds of text documents. You can generate config files,
bash scripts, JSON data, HTML documents, etc. For example [Ansible](https://www.ansible.com/), the configuration
management and automation platform, leverages Jinja2 templating within playbooks for simple variable substitution and as
a ansible module that can be used generate scripts, config files and more at runtime.

Eg: ansible template module use
```
- hosts: some-application-host-machine
  vars:
    types: ['type1','type2','other-type']
  tasks:
    - name: Ansible template loop example.
    - template:
        src: my-start-script-template.j2
        dest: /home/user/start-script.sh
        mode: 0777
```

The app engine docs above are specifically referring to *web templating*. So the rest of this post will focus on that.
Web templating is the use of templates to generate HTML content such as web pages that can be viewed in a browser.

## Types of templating engines
1. *Client-side*: server returns raw data. Substitution of data into templates occurs in the browswer. *JavsScript
templating* refers to client-side templating
2. *Server-side*: substitution of data into templates occurs on the server at the time of client request.
This means the server could be applying data specific to the incoming request into the template.
Server returns dynamically generated HTML to browswer.
3. *Out of server*: the server does not dynamically fill out templates in response to client requests.
The server serves static HTML pages that do not change. Those static HTML pages are generated by a separate templating
engine and then handed over to the server. Static site generators are an example of this. This blog uses a static site
 generator. I write posts in markdown syntax. Each post is injected into a HTML template that defines standard layout
 for all posts. The resulting set of static HTML pages is then hosted on a web server. This blog uses the Jekyll static
 site generator which in turn uses the [Liquid](https://shopify.github.io/liquid/) templating engine.

Note [Wikipedia](https://en.wikipedia.org/wiki/Web_template_system#Kinds_of_template_systems) further mentions 2 more types of web templating:
edge side (template is filled on a proxy server between client and server) and distributed (template is filled on
 multiple servers at request time)

## Why use web templating engines?
* *Separation of concerns*. By keeping the presentation details (the template, markup, stylesheets) separate from the
content (data values), you can change how you present the data without refactoring your content.

* *Code reuse* Reuse templates or template fragments. Just inject different data.

* *Reduce volume of data sent from server* Server sends presentation layer stuff
once upfront. After that server only sends raw data on request. Data can be injected into the template on the
client side.

* *Caching* All of the presentation layer stuff can be cached easily
because it doesnt change as much as the data contents. The presentation layer can be cached on the client side or cached in
a Content Delivery Network (CDN) independently of the dynamic data.

Case study: Checkout [this article](https://engineering.linkedin.com/profile/engineering-new-linkedin-profile) by LinkedIn.
They are leveraging templates to inject content into a page. They've gone further
and broken up a single page into many dynamically generated sections. Sections are loaded and refreshed
independently of each other. Each section contains data served by a different server side component. Requests for data
for various sections can be sent and processed concurrently to each other.

## What are drawbacks of using a templating engine?
If your HTML manipulation is very simple you can just use vanilla JavaScript to get the job done. Other than that, I
haven't found any drawbacks or tradeoffs that need to be considered before deciding whether or not to use a templating
engines in general. There might be drawbacks to specific templating engines. If you have very complex template filling in
logic, then some specific templating engines may not offer you a rich enough syntax to meet your needs.

## How do templating engines relate to these other web technologies I hear about?
* Javascript
    * Templating engines are used in conjunction with languages like Javascript.
    * JavaScript itself allows you to multiple ways to dynamically change HTML. The reason for using a templating
    engine in conjunction with JS is because if you are generating or changing complex HTML then your JS code can become
    unweildy. Calling on a template engine to generate the HTML and then injecting the result that into your DOM
    makes your JS code a lot simpler. See below for code examples showing the same logic with and without web templates.
* Django, Angular, React
    * A number of the JavaScript frameworks include templating as one of many functionalities they provide.
    Some have a set templating engine and template syntax built into the framework, others allow developers to configure
     which templating engine the framework should use. Because templating is one of many things the frameworks do for you
     you may hear names of these frameworks in the context of templating and also in several other seemingly unrelated contexts.

## What would my code look like without a templating engine?
To put template engines into perspective, I like to look at what the code would look like if we didnt use them.
Here are some alternate ways you could generate some HTML on the client side.

Eg: The server returns a collection of available fruits. The number of fruits can change.
You want your front end HTML code to look like this:

```HTML
<ul>
    <li>apple</li>
    <li>banana</li>
    <li>cranberry</li>
</ul>
```

### Option 1: String Concatenation
Write Javascript logic that will generate HTML text through string manipulation.
This is the least desirable approach. If your HTML is complex, this would get very messy, very fast.

```javascript
function makeList(fruits) {

    var listContents = [];
    for (i = 0; i < fruits.length; i += 1){
            listContents[i] = '<li>' + fruits[i] + '</li>';
    }
    var HTMLList = '<ul>' + listContents + </ul>

    document.getElementById('someDiv').innerHTML = HTMLList;
}
```

### Option 2: DOM manipulation

```javascript
function makeList(fruits) {

    var myList = document.createElement("UL");
    myList.setAttribute("id", "myUL");

    for (var i = 0; i < fruits.length; i++) {
      var listItem = document.createElement("li");
      listItem.textContent = fruits[i];

      myList.appendChild(listItem);
    }

    document.body.appendChild(myList);
}
```

### Option 3: Client-side templating using a template engine

{% raw %}
```
<template id="fruits-template">
    <ul>
        {{#each fruits}}
         <li>{{this}}</li>
        {{/each}}
    </ul>
</template>
```
{% endraw %}

```javascript
function makeList(fruits) {

    var myFruits = ["apple", "banana", "cranberry"];

    var template = document.getElementById('fruits-template').innerHTML;
    var renderFruits = Handlebars.compile(template);
    var myList = renderFruits({fruits: myFruits});

    document.body.appendChild(myList);
}
```

## What are some different templating engines?
Jinja, Django, Angular, Moustache, HandleBar ... there are dozens of them and they do slightly different things to each
 other. Here are some questions to ask to understand how different templating engines relate to each other

* Are they client-side or server-side templating engines? How can I figure out which of these I need?
* What languages do they work with?
* Are the tied to specific other frameworks?
* What kinds of logic can I embed within the template?
* How can I organize and re-use my template logic?
    * Does the engine support organizing my templates into an inheritance hierarchy?
    * Does the engine support creating modular template snippets that I can reuse and combine together in different combos?
* Who is using this template engine and are they doing anything particularly interesting with it?
* Who is maintainging the code for this templating engine?
* Cost and licensing of the templating engine?

Check out [this article](https://engineering.linkedin.com/frontend/client-side-templating-throwdown-mustache-handlebars-dustjs-and-more)
 from LinkedIn for an evaluation and comparison of templating engines.

Wikipedia has [this table](https://en.wikipedia.org/wiki/Comparison_of_web_template_engines) comparing several web
 templating engines.

## References
* [Engineering the New LinkedIn Profile](https://engineering.linkedin.com/profile/engineering-new-linkedin-profile)
* [What's in a templating language](https://collectiveidea.com/blog/archives/2018/03/06/what-s-in-a-templating-language-part-1)
* [Wikipedia Web Template System](https://en.wikipedia.org/wiki/Web_template_system)

