Title: Blogging with Markdown, Pelican and GitHub pages: Part 1
Date: 2014-12-10 00:00
Tags: blogging, pelican, markdown, github-pages
Summary: Quick and Easy way of getting started with Pelican and GitHub pages

[TOC]

## Basics

[Pelican] is a static site generator. It accepts lightly formatted plain text files, like 
   [Markdown] or [reStructuredText],
   and generate static pages which can be hosted almost everywhere. If you have a GitHub profile, you can write articles at
   the comfort of your favorite IDE and publish them on [GitHub pages] with couple of commands.

**This is pretty much what happens:**

1. Write articles to `content/` subdirectory.
2. Pelican reads `content/` and outputs HTML pages to `output/`.
3. Files in `output/` are published on GitHub

## Groundwork

At the time of the writing, Python 2.7.x is recommended for Pelican. If you don't have PIP setup, head over to 
   [this link][pip] for installation instructions.
   
I use virtualenvwrapper to create environments, and installation instructions can be found [here][venvwrap] 

## GitHub repository and branches

Pages on GitHub are nothing but HTML and static files residing inside a repository. The repo has to follow the naming convention
   `<username>.github.io`. My username is `42hrs` and hence `42hrs.github.io` should be the name of this repo.
   
Create a new repo at [https://github.com/new][github new]
   
After everything's done [http://42hrs.github.io][pages link] is where this blog would live (I've setup 
   a custom domain, but more on that later). Github looks for the HTML files at the root of the `master` branch of this repo.
   
Now, clone the repository.

```
$ git clone https://github.com/42hrs/42hrs.github.io.git
$ cd 42hrs.github.io/
```

One of GitHub's rules is that HTML pages have to reside at the root of the `master` branch of your repository. But Pelican 
   outputs the HTML to a subdirectory `output/` and also has other type of files at the root. So that's not acceptable.
   
Forget about `master` for the timebeing, and create and checkout a new branch named `source`.

```
$ git checkout -b source
```

Always make sure you're on `source` before you do anything. 

```
$ git branch 
  master    # Sacred; Only for the final HTML and static files.
* source    # For Markdown and other pelican-specific files
```


## Installation

Create a new environment, and install the required packages.
```
$ mkvirtualenv pelican
$ workon pelican
$ setvirtualenvproject
$ pip install pelican Markdown ghp-import
```

## Pelican Quickstart

Pelican comes with a handy command `pelican-quickstart` which sets up a complete project for your blog based on answers to 
   a few questions.
   
```
$ pelican quickstart
```

Mostly I chose the default options, but remember to say yes to the following questions.
```
> Where do you want to create your new web site? [.] .
...
> Do you want to generate a Fabfile/Makefile to automate generation and publishing? (Y/n) y
> Do you want an auto-reload & simpleHTTP script to assist with theme and site development? (Y/n) y
...
> Do you want to upload your website using GitHub Pages? (y/N) y
> Is this your personal page (username.github.io)? (y/N) y 
```

Now Pelican will have setup a project inside the current directory with the following files.
```
$ tree
.
|-- content/
|-- develop_server.sh
|-- fabfile.py
|-- Makefile
|-- output/
|-- pelicanconf.py
 -- publishconf.py

2 directories, 5 files
```

A blog has been setup, but without any content. Commit everything to git before writing the first article.
```
$ git add -A
$ git commit -m "Successfully setup a Pelican project"
```

## Writing content

I write in Markdown, and pelican considers each `.md` file inside `content/` as a different article.  
```
$ nano content/hello-world.md
```

Every article needs some metadata. `title` and `date` are mandatory, the rest are optional but recommended
```
Title: My first article with Pelican
Date: 2014-12-18 10:20
Modified: 2010-12-05 19:30
Category: Pelican
Tags: pelican, publishing
Slug: my-first-article-with-pelican
Authors: My Name
Summary: Short version for index and feeds

The content of the article goes here
```

Save the file and close the editor.

## Viewing in browser

To convert the markdown files into HTML, use the following command.
```
$ make html
```

Pelican comes with a way to easily run a local server on your PC. Following command serves the site for preview on the
   at http://localhost:8000.
```
$ make serve
```

To avoid typing the above two commands after every time you need to preview a change in your article, pelican has another
handy command.
```
$  make devserver
```
This watches the files and automatically refreshes the server every time there is change in the articles.

When satisfied with the article, do a git commit.
```
$ git add -A
$ git commit -m "Wrote my first article with Pelican"
```

## Publishing to GitHub

The final step is to publish the HTML pages to GitHub. The current branch is `source` but the HTML files need to be committed
   to the `master` branch. The following command creates the HTML files, commit them to `master` and pushes it to GitHub.
```
$ make publish github
```

Go to [42hrs.github.io][pages link] to view the published blog. There can be a slight delay before GitHub makes it live.

## Writing more articles

To write a new article and publish it on GitHub, follow these steps

1. `git checkout source`
2. Create a new markdown file in `content/` with metadata and content
3. `make devserver` to preview locally
4. `git commit -am "Finished another article"`
5. `make publish github`




[Pelican]:          http://blog.getpelican.com/
[Markdown]:         http://daringfireball.net/projects/markdown/
[reStructuredText]: http://docutils.sourceforge.net/rst.html
[GitHub pages]:     https://pages.github.com/
[venvwrap]:         http://virtualenvwrapper.readthedocs.org/en/latest/install.html
[github new]:       https://github.com/new
[pip]:              https://pip.pypa.io/en/latest/installing.html
[pages link]:       http://42hrs.github.io
