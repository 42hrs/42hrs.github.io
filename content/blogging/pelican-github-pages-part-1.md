Title: Blogging with Markdown, Pelican and GitHub pages: Part 1
Date: 2014-12-10 00:00
Tags: blogging, pelican, markdown, github-pages
Summary: Quick and Easy way of getting started with Pelican and GitHub pages


Pelican is a static site generator. It accepts lightly formatted plain text files, like 
   [Markdown](http://daringfireball.net/projects/markdown/) or [reStructuredText](http://docutils.sourceforge.net/rst.html),
   and generate static pages which can be hosted almost everywhere. If you have a GitHub profile, you can write articles at
   the comfort of your favorite IDE and publish them on [GitHub pages](https://pages.github.com/) with couple of commands.

**This is pretty much what happens:**

1. You write articles to `content/` subdirectory.
2. Pelican reads `content/` and outputs HTML pages to `output/`.
3. Files in `output/` are published on GitHub

## Groundwork

Install Python and PIP

## GitHub repository and branches

Pages on GitHub are nothing but HTML and static files residing inside a repository. The repo has to follow the naming convention
   `<your-username>.github.io`. My username is `42hrs` and hence `42hrs.github.io` should be the name of this repo.
   
*Instructions to create the repo goes here*
   
After everything's done [http://42hrs.github.io](http://42hrs.github.io) is where this blog would live (I've setup 
   a custom domain, but more on that later). Github looks for the HTML files at the root of the `master` branch of this repo.
   
Now, clone the repository.

```
$ git clone https://github.com/42hrs/42hrs.github.io.git
$ cd 42hrs.github.io/
```

One of GitHub's rules is that HTML pages have to reside at the root of the `master` branch of your repository. But Pelican 
   outputs the HTML to a subdirectory `output/` and also has other type of files at the root. So that's not acceptable.
   
Forget about `master` for the timebeing, and create and checkout a new branch, `source`.

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

Virtualenv is not necessary, but is recommended. *I'm also using Virtualenvwrapper.*

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
   
Make sure you do 
```
$ pelican quickstart
```



## Writing content

```
$ touch content/hello-world.md
```

## Viewing in browser

```
$ make html
$ make devserver
```

## Publishing to GitHub

```
$ make publish github
```
 




