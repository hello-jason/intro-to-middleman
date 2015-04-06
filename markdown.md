name: introduction
class: middle, center

![Middleman logo](images/middleman-logo.svg)

# Introduction to Middleman

**[https://middlemanapp.com/](https://middlemanapp.com/)**

<small>by [Jason Cross](http://hellojason.net)</small>

---

# Brief History of Middleman

These days, many websites are built with an API in mind. Rather than package the frontend and the backend together, both can be built and deployed independently using the public API to pull data from the backend and display it on the frontend. Static websites are incredibly fast and require very little RAM. A front-end built to stand-alone can be deployed directly to the cloud or a CDN. Many designers and developers simply deliver static HTML/JS/CSS to their clients.

# About Middleman

* Fork of [StaticMatic](https://github.com/staticmatic/staticmatic) by [Thomas Reynolds](http://awardwinningfjords.com/) (which he [has regretted](http://awardwinningfjords.com/2012/12/30/dont-fork.html))

* Built on Ruby programming language

* Allows for [Sass](http://sass-lang.com/), [CoffeeScript](http://coffeescript.org/), asset management with [Sprockets](https://github.com/sstephenson/sprockets), and HTML templating (ERb, Haml, Slim)

* Currently at version 3.3.10, working on version 4

???

# About

* Thomas' article insists forking is a responsibility. "I should have contributed to StaticMatic...to the existing community and improved it."

* If you write HTML/CSS and don't know about preprocessors or html templating, holy crap you're missing out

---

# Gentle to Beginners

* No database; just static HTML, CSS, and JavaScript (if you need it)

* Opinionated if you want, overwritable if you don't

???

# Beginners

* No database to worry about

---

# Great for Advanced Projects

Could be the right tool for a project with distinctive frontend, api, and backend components

---

# Setting up Middleman

**RTFM**

We will be using the command line, but it's not that bad

## Dependencies

https://middlemanapp.com/basics/install/

* Ruby language
* RubyGems


* Installation and setup

---

# Introduction

* livereload
* Recommended gems and purposes - you can sometimes get away gems made for RoR
* config.rb

---

# Commands and usage

* Starting a local server (webrick)

```bash
# in project directory
middleman
```

* Frontmatter

## Building

## Deploying

* middleman-deploy

## Hosting

* [Github Pages](https://pages.github.com/)
* [Bitballoon](https://www.bitballoon.com)
* [Divshot](https://divshot.com/)
* [Forge](https://getforge.com/)

## Advanced

* SEO
* middleman-blog

### Forms

* Bitballoon, integrated into hosting
* [FormAssembly](http://www.formassembly.com/)
* Other SaaS options?

### SEO

* Per-page title, meta description
* XML sitemap
