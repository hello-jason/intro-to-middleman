name: introduction
class: middle, center

![Middleman logo](images/middleman-logo.svg)

# Introduction to Middleman

**[https://middlemanapp.com/](https://middlemanapp.com/)**

<small>by [Jason Cross](http://hellojason.net)</small>

---

name: history

# Brief History of Middleman

* Built on Ruby programming language, inspired by Ruby on Rails

--

* Fork of [StaticMatic](https://github.com/staticmatic/staticmatic) by [Thomas Reynolds](http://awardwinningfjords.com/) (which he [has regretted](http://awardwinningfjords.com/2012/12/30/dont-fork.html))

???

* Article written by Thomas where he insists forking is a responsibility. "I should have contributed to StaticMatic...to the existing community and improved it."

--

* Allows for [Sass](http://sass-lang.com/), [CoffeeScript](http://coffeescript.org/), asset management with [Sprockets](https://github.com/sstephenson/sprockets), and HTML templating (ERb, Haml, Slim) -- *all completely optional*

--

* Currently at version 3.3.10, working on version 4

???

* Documentation on the Middleman website about upgrading to v4.

---

# Great for Beginners

* No database; just static HTML, CSS, and JavaScript (if you need it)

--

* Opinionated if you want, overwritable if you don't

???

* Comes out the box with directory structure, ERb templating No database to worry about

--

# Great for Advanced Projects

* Many websites are now built with an API. Frontend can use this API to pull data from a separate backend application.

--

* Many designers and developers simply deliver static HTML/JS/CSS to their clients

???

* Makes applications easier to maintain and more scalable

---

name: installation

# Installation and setup

## Dependencies

https://middlemanapp.com/basics/install/

* Ruby language

* RubyGems

--

## Create new project

* cd into a directory and run `middleman init` to create a new project

```tree
├── config.rb
├── Gemfile
├── Gemfile.lock
├── source
    ├── images
        ├── background.png
        ├── middleman.png
        ├── index.html.erb
        ├── javascripts
        ├── all.js
    ├── layouts
        ├── layout.erb
    ├── stylesheets
        ├── all.css
        ├── normalize.css
```

--

## Setting up Middleman

![RTFM](images/rtfm.png)
**RTFM**

We will be using the command line, but it's not that bad

---

# Introduction

## livereload

* Browser plugin

--

* Enable livereload in `config.rb`

--

## Recommended gems and purposes

* Lots of Middleman-specific gems (some RoR gems work)

--

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
