Title: Blogging with Markdown, Pelican and GitHub pages: Part 1
Date: 2014-12-10 00:00
Tags: blogging, pelican, markdown, github-pages
Summary: Quick and Easy way of getting started with Pelican and GitHub pages


Pelican is a static site generator. It accepts lightly formatted plain text files, like Markdown or reStructuredText,
   and generate static pages which can be hosted almost everywhere. If you have a GitHub profile, you can jot down
   articles at the comfort of your favorite IDE and publish them on GitHub pages with couple of commands.

## Groundwork

Install Python and PIP

## GitHub repository and branches

```
$ git clone
$ git checkout -b source
```

## Installation

```
$ mkvirtualenv pelican
$ workon pelican
$ setvirtualenvproject 
$ pip install pelican Markdown ghp-import
```

## Pelican Quickstart

```
pelican quickstart
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
 




[Link to Header](#header)