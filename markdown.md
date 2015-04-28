name: introduction
class: middle, center

![Middleman logo](images/middleman-logo.svg)

# Introduction to Middleman

**[https://middlemanapp.com/](https://middlemanapp.com/)**

<small>by [Jason Cross](http://hellojason.net)</small>

???

I first learned about Middleman when we took over a client's website hosting a while back.

Now, I use it for my personal website.

I can use all the tools that I love (SCSS, Slim, Git) and host it all for free on GitHub Pages.

---

name: what-is-middleman

# What is Middleman?

Simplest definition: **static site generator**

--

The term **static** (or flat) means that page that can be delivered to users exactly as it is stored (typically .html, css, .js).

???

This differs from a dynamic web page, which is generated on a web server before it is delivered to the user, often querying data out of a database and so forth.

--

* Middleman is installed and runs on your local computer. It does not run on a server.

--

* You **build** the site locally, which creates HTML, CSS, and JavaScript files, then upload those files to a web server.

???

Lots of hosting options, including free ones like GitHub Pages

--

* Gives you access to all the tools of modern web stacks.

???

Preprocessors, html templating, image optimization, favicon generation, full-blown programming language (ruby)

--

* Fork of [StaticMatic](https://github.com/staticmatic/staticmatic) by [Thomas Reynolds](http://awardwinningfjords.com/) (which he [has regretted](http://awardwinningfjords.com/2012/12/30/dont-fork.html))

???

* Article written by Thomas where he insists forking is a responsibility. "I should have contributed to StaticMatic...to the existing community and improved it."

* StaticMatic was abandoned in 2010. Thomas is still active in Middleman.

---

# Great for Beginners

*"Beginners"* referring to people who are comfortable with, or at least interested in, HTML/CSS

???

I think Middleman is the perfect next step for people writing HTML in Notepad/Sublime.

--

* Built-in web server

???

No need to configure nginx or apache. Middleman includes a web server.

--

* Comes very slightly opinionated, and easy to modify.

???

Comes out the box with a directory structure and folders to put your layouts, images, stylesheets, etc. Low barrier to entry.

--

* One template correlates directly to one html page*. No routes. `file name becomes slug/permalink`

```tree
├── source
    ├── about.html.erb   // example.com/about
    ├── contact.html.erb // example.com/contact
    ├── index.html.erb   // example.com/
```

???

Create a new page `about.html.erb` and it will available example.com/about when you build the project.

The asterisk is because you can have data files (yml, json) that Middleman can use to generate several pages.

--

* No need for a database or special server-side language(s) on production server

???

Middleman outputs normal HTML, CSS, and JS files which can run on nearly any server.

---

# Great for Advanced Projects

* **Separation of concerns** - A static frontend app on Middleman can uses JavaScript to talk with an API and pull data from some other backend application.

???

Modern web development has seen separation of concerns where the frontend application, the API, and the backend application are 3 different applications entirely.

--

* Serve static files to users, then let the client request information via something like ajax

--

**Automation & Sugar**

* Bundler for gem management, One line deploys ([middleman-deploy](https://github.com/middleman-contrib/middleman-deploy)), Image compression ([middleman-imageoptim](https://github.com/plasticine/middleman-imageoptim)), Favicon generation ([middleman-favicon-maker](https://github.com/follmann/middleman-favicon-maker)), Blogging in markdown ([middleman-blog](https://github.com/middleman/middleman-blog))

--

* Allows for [SCSS](http://SCSS-lang.com/), [CoffeeScript](http://coffeescript.org/), asset management with [Sprockets](https://github.com/sstephenson/sprockets), and HTML templating (ERb, Haml, Slim) -- *all completely optional*

![SCSS](images/logo-sass.jpg)
![coffeescript](images/logo-coffeescript.jpg)
![slim](images/logo-slim.jpg)
![HAML](images/logo-haml.jpg)

---

name: dependencies

### Middleman Dependencies

**2 primary requirements** before we can run Middleman (one-time installations)

--

1. Ruby language >= 1.9.3

  **OS X** - included in Yosemite and Mavericks<br>
  **Linux** - easy with [rbenv](https://github.com/sstephenson/rbenv) and [rvm](https://rvm.io/)<br>
  **Windows** - [RubyInstaller](http://rubyinstaller.org/) (but expect issues getting projects going)

???

Ruby 2.0 is included in Yosemite and Mavericks. Mountain Lion, Lion, and Snow Leopard ship with Ruby 1.8.7.

For **Windows**, I recommend having a Virtual Box with CentOS (or some other distro)

--

1. RubyGems

  Standalone pieces of functionality are packaged into `gems`, and Middleman itself is a gem. Visit [rubygems.org](https://rubygems.org/) to install RubyGems onto your computer.

???

There are lots of Middleman-specific gems. Some Ruby on Rails gems work with Middleman.

--

![RTFM](images/rtfm.png)

**More information**

Official Middleman documentation is very good.

[https://middlemanapp.com/basics/install/](https://middlemanapp.com/basics/install/)

???

Don't overlook the offical documentation when figuring things out.

---

name: install-middleman
class: middle

### Installing Middleman

With ruby and RubyGems installed, we need to install Middleman itself.

Middleman is just a gem. Install it with RubyGems (one-time installation):

```bash
gem install middleman
```

???

This gives us the `middleman` command on our command line

---

name: new-project

### Creating a New Middleman Project

Working with Middleman requires using the command line. There are **very few** commands to learn.

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

This creates a new directory called *project-name* and puts all these files and folders into it.

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

See Middleman's opinionated decisions: your project files go into `source`, images in `images`, and css in `stylesheets`.

The initialization command allows you to pass in additional parameters, such as custom [project templates](https://directory.middlemanapp.com/#/templates/all).

---

name: server

### Starting a local server

```bash
# in project directory
middleman
```

???

Spins up a local web server (using webrick), running your site at the given address.

--

Visit the URL (with port number) in your browser

```bash
== The Middleman is loading
*== The Middleman is standing watch at http://0.0.0.0:4567
== Inspect your site configuration at http://0.0.0.0:4567/__middleman/
```

![Middleman is watching](images/middleman-init-index.jpg)

--

name: make-stuff

---

name: layouts

# Layouts

A common method for reusing bits of html is to put it into other files and include those files into pages.

```html
<!-- header.php -->
<html>
  <head>
    <title>Welcome to Refresh</title>
  </head>
  <body>
```

```html
<!-- footer.php -->
  <footer>Copyright 2015</footer>
  </body>
</html>
```

???

PHP implementation of this method

--

```php
/*  hello.php */
* <?php include('header.php') ?>
  <h1>Hello Refresh</h1>
  <p>This is some content for this page</p>
* <?php include('footer.php') ?>
```

???

Works well enough, but must be included many times across all your templates. Lots of duplication

---

name: middleman-layouts

# Layouts in Middleman

In Middleman, this concept is reversed.

* A **layout** is used for the overall page scaffold, such as header, navigation, footer; things that get repeated on most pages.

???

This is true for other frameworks as well.

--

* Unique content on each page is injected through the `yield` call.

???

Yield concept also applicable to Ruby on Rails, Jekyll, Node apps.

--

You can have multiple layouts, but the default one should be called `layout.html.erb`.

???

Remember, Middleman comes opinionated. It looks for this file in a folder called layouts.

We read the filename from right to left. When this example builds it will compile `erb` into `html`.

Other template engines can be used instead of erb, such as `haml` or `slim`.

---

name: layout-with-content

```html
<!-- layout.html.erb -->
<html>
  <head>
    <title>Welcome to Refresh</title>
  </head>
  <body>
*   <%= yield %>
  </body>
</html>
```

???

Example layout

--

```html
<!-- about.html.erb -->
<h1>About Refresh</h1>
<p>This is some content for this page.</p>
```

???

Example `about` page
--

```html
<!-- example.com/about -->
<html>
  <head>
    <title>Welcome to Refresh</title>
  </head>
  <body>
*   <h1>About Refresh</h1>
*   <p>This is some content for this page.</p>
  </body>
</html>
```

???

When this page is built, the layout is rendered around that page and its content is put into the `yield` area.

---

name: templates

### Templates

Create a new template for each page of your site in the **source** directory.

```tree
├── source
  ├── index.html.erb
  ├── about.html.erb
  ├── contact.html.erb
```

```erb
<!-- index.html.erb -->
<h1>Welcome to Refresh</h1>
<%= image_tag 'logo.png' %>
<p>Glad to have you here.</p>
```

```html
<!-- about.html.erb -->
<h1>About Refresh</h1>
<p>This is some content for this page.</p>
```

```html
<!-- contact.html.erb -->
<h1>Contact Us</h1>
<p>We're on <%= link_to 'meetup', 'http://www.meetup.com/refresh-baton-rouge/' %>
```

???

Middleman refers to each `page` as a `template`. Since we have a layout, each template only contains the content for that page. Templates and HTML pages are 1-to-1.

---

### Partials

Partials let you split out pieces of functionality to be reused across several pages, as needed. Put an `underscore` before file names.

```erb
*<!-- _back-to-blog.html.erb -->
<p>Go back to the <a href="#{url_articles}">blog archive</a></p>
```

```erb
<!-- article-welcome-to-refresh.html.erb -->
<h1>Groovy article about Refresh</h1>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
<hr>
*<%= partial "back-to-blog" %>
```

---

name: frontmatter

### Frontmatter

Frontmatter allows page-specific content to be included at the top of a template, between a set of 3 dashes.

--

```html
<!-- about.html.erb -->
*---
*title: About Refresh Baton Rouge
*meta_description: Some descriptive text that might be used in search results.
*---

<h1>Hello Refresh</h1>
<p>This is some content for this page.</p>
```

???

Frontmatter assigns this content to a variable.

--

This content is assigned to a variable that can be used in other layouts.

```erb
<!-- layout.html.erb -->
<html>
  <head>
*   <% if current_page.data.title %>
*     <title>#{current_page.data.title}</title>
*   <% else %>
*     <title>Refresh Baton Rouge</title>
*   <% end %>
  </head>
</html>
```

???

Ruby variables are available in your pages in the format #{variable_name}

---

name: building

### Building

The `build` command builds your project into a folder called `build`.

```bash
middleman build
```

---

name: config-rb

### config.rb

Middleman comes opinionated, but you can change things. All configuration is done in the `config.rb` file.

```ruby
set :js_dir, 'js'
set :css_dir, 'css'
```

Development environment

```ruby
configure :development do
  # do things only in development
end
```

???

One benefit of ruby is that it was designed to be easy to read. 

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

---

name: deploying

### Deploying

* Simplest deployment method is to FTP contents of the `build` directory to web server

--

* `middleman-deploy` gem allows for automated deployments with a single command

```bash
middleman deploy
```

???

Allows rsync, git, ftp, sftp

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

???

* middleman init welcome-to-refresh
* activate livereload
* middleman server
* create a new template `welcome.html.erb`
