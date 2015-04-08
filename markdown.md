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

![Sass](images/logo-sass.jpg)
![coffeescript](images/logo-coffeescript.jpg)
![slim](images/logo-slim.jpg)
![HAML](images/logo-haml.jpg)

--

* Currently at version 3.3.10, working on version 4

???

* Documentation on the Middleman website about upgrading to v4.

---

# Great for Beginners

* No database. Just HTML, CSS, and (if needed) JavaScript

--

* Opinionated if you want, overwritable if you don't

???

* Comes out the box with a directory structure and ERb templating. You can change the directory structure, templates to Slim (or Haml, etc).

--

* One HTML file is one page

```tree
├── config.rb
├── Gemfile
├── Gemfile.lock
├── source
    ├── index.html.erb
    ├── images
        ├── background.png
        ├── middleman.png
        ├── javascripts
        ├── all.js
    ├── layouts
        ├── layout.erb
    ├── stylesheets
        ├── all.css
        ├── normalize.css
```

---

# Great for Advanced Projects

* Many websites are now built with an API. Frontend can use this API to pull data from a separate backend application. This keeps applications scalable and easier to maintain.

--

* Many designers and developers simply deliver static HTML/JS/CSS to their clients

--

**Automation**

* One line deploys ([middleman-deploy](https://github.com/middleman-contrib/middleman-deploy))

* Image compression ([middleman-imageoptim](https://github.com/plasticine/middleman-imageoptim))

* Favicon generation ([middleman-favicon-maker](https://github.com/follmann/middleman-favicon-maker))

???

There are lots of Middleman-specific extensions to be had, called gems

---

name: environments

Configure options for specific environments, namely Development and Production.

--

### Development

```ruby
configure :development do
  # do things only in development
end
```

???

One benefit of ruby is that it was designed to be easy to read. 

---

name: installation

### Installation & Setup

**2 primary requirements** (one-time installations):

--

1. Ruby language

  **OS X** - included<br>
  **Linux** - straight-forward with [rbenv](https://github.com/sstephenson/rbenv)<br>
  **Windows** - [RubyInstaller](http://rubyinstaller.org/) (but expect issues getting projects going)

???

Current version of Middleman (3.3.10) requires ruby >= 1.9.3. Latest ruby is current at 2.2.*

On OS X Yosemite and Mavericks, Ruby 2.0 is included. OS X Mountain Lion, Lion, and Snow Leopard ship with Ruby 1.8.7.

--

1. RubyGems

  Extensions to ruby are packaged into `gems`. Visit [rubygems.org](https://rubygems.org/) to install RubyGems and search for availalbe gems.

  Middleman has a lot of Middleman-specific gems

--

![RTFM](images/rtfm.png)

**More information**

Official Middleman documentation is very good.

[https://middlemanapp.com/basics/install/](https://middlemanapp.com/basics/install/)

???


---

name: install-middleman
class: middle

### Installing Middleman

With ruby and RubyGems installed, we need to install Middleman itself.

Middleman is just a gem. Install it with RubyGems (one-time installation):

```bash
gem install middleman
```

---

name: new-project

### Creating a New Middleman Project

Working with Middleman requires using the command line. There are **very few** commands needed to get started.

```bash
middleman init project-name
```

???

In reality, there's only 3 commands we care about:

1. Creating a project (which we're doing here)
1. Starting a Middleman server (so we can see it in our browser)
1. Building a project (so we can put it on a web server)

Middleman commands are preceded with the word `middleman`.

--

This creates a new directory called project-name and puts all these files and folders into it.

```tree
├── config.rb
├── Gemfile
├── Gemfile.lock
├── source
    ├── index.html.erb
    ├── images
        ├── background.png
        ├── middleman.png
        ├── javascripts
        ├── all.js
    ├── layouts
        ├── layout.erb
    ├── stylesheets
        ├── all.css
        ├── normalize.css
```

???

Initialization allows you to pass in additional parameters, such as custom [project templates](https://directory.middlemanapp.com/#/templates/all).

---

### Setting up Middleman

THIS IS WHERE YOU LEFT OFF

---

### Introduction

## livereload

* Browser plugin

--

* Enable livereload in `config.rb`

--

### Recommended gems and purposes

* Lots of Middleman-specific gems (some RoR gems work)

--

* config.rb

---

### Commands and usage

* Starting a local server (webrick)

```bash
# in project directory
middleman
```

---

name: Layouts

# Layouts

* A common method for reusing html is to separate it into partials (such as `header` and `footer`) and include them within each page.

```php
* <?php include('header.php') ?>
    <h1>Hello Refresh</h1>
    <p>This is some content for this page</p>
* <?php include('footer.php') ?>
```

???

This works well enough, but PHP is executed each time a user requests this page. This is inefficient.

--

* In Middleman, the layout is used for the overall scaffold of all pages. Then, the unique content on each page is included through the `yield` call.

???

Yield concept also applicable to Ruby on Rails, Jekyll, Node apps.

--

* A layout is the overall structure used for each page. You can have multiple layouts, but the default one should be called `layout.html.erb`.

???

We read the filename from right to left. When this example builds it will compile `erb` into `html`.

Other template engines can be used instead of erb, such as `haml` or `slim`.

---

name: layout-with-content

*layout.html.erb*

```html
<html>
<head>
  <title>Welcomem to Refresh</title>
</head>
<body>
*  <%= yield %>
</body>
</html>
```

???

Example layout

--

*about.html.erb*

```html
<h1>Hello Refresh</h1>
<p>This is some content for this page.</p>
```

???

Example `about` page
--

*output*

```html
<html>
<head>
  <title>Welcomem to Refresh</title>
</head>
<body>
  *<h1>Hello Refresh</h1>
  *<p>This is some content for this page.</p>
</body>
</html>
```

???

When this page is built, the layout is rendered around that page and its content is put into the `yield` area.

---

name: templates

### Templates

Think of templates as your individual pages -- Home, About, Contact.

---

### Partials

Useful

When sharing content across multiple:

* `layouts` - header, footer
* `templates` - call-to-action graphic only needed on certain templates

---

name: frontmatter

### Frontmatter

Frontmatter allows page-specific variables to be included at the top of a template.

Top of a template:

```html
---
*title: About Refresh Baton Rouge
*meta_description: Some descriptive text that might be used in search results.
---

<h1>Hello Refresh</h1>
<p>This is some content for this page.</p>
```

To show this in HTML:

```html
<title>#{current_page.data.title}</title>
```

???

This data can be referenced from a layout.

---

name: building

### Building

The `build` command builds your project into a folder called `build`.

```bash
middleman build
```

--

Build-specific settings in `config.rb`

```ruby
configure :build do
  # Ignore during build process
  ignore ".git"

  # Asset compression
  activate :minify_css
  activate :minify_javascript
  activate :gzip
end
```

???

Middleman creates website files in a folder called build. Not all files need to be included, such as the .git folder.

---

name: deploying

### Deploying

* Simplest deployment method is to FTP contents of the `build` directory to web server

--

* `middleman-deploy` allows for automated 

```bash
middleman deploy
```

???

Allows rsync, git, ftp

---

name: hosting

### Hosting Options

* **[Github Pages](https://pages.github.com/)** - Most documentation discusses Jekyll, but hosting on the gh-pages branch pertains to any static site.

* **[Bitballoon](https://www.bitballoon.com)** - Great for quickly hosting a static site. Especially useful for prototyping, then upgrade to host with your own domain.

* **[Divshot](https://divshot.com/)**

* **[Forge](https://getforge.com/)**

---

class: middle, center

demo
