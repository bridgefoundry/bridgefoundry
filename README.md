Bridge Foundry Web Site
=======================

This site is build with [Jeykll](https://jekyllrb.com/) and hosted on
[Github Pages](https://pages.github.com/) -- pushing the master branch will
update the website.


## Adding a blog post

1. Check out this repo with `git clone` to your local computer.
2. Create a file in the `_posts` directory. The format of the file name is
important! It should be `YYYY-MM-DD-first-few-words-or-desc-of-post.md`. The
date is the date that the blog post should appear to have been published on.
3. Add the following Jekyll "front matter" to the top of your new markdown file:
```
---
layout: post
title: This is the Title of Your Blog Post
tags: ready
---
```
4. On the next empty line, compose your post. You can use Markdown tags like `**bold**` or even raw HTML.
5. Follow the steps in the rest of this README for local previewing ("Local development") and deployment of your post.


## Local development

Install Ruby and then run:

```
gem install bundler
bundle
```

Note: the website integrates two other repos, which are integrated as submodules
and then need to be built individually.  If you want to make changes to those,
work directly in these separate repos

* [code of conduct](https://github.com/bridgefoundry/code-of-conduct)
* [workshop-map](https://github.com/bridgefoundry/workshop-map)

The full website can be built by triggering a build on Travis, which anyone
who is a member of the `bridgefoundry` organization on github should be able
to do.

To build locally:

```
git submodule update --init --recursive
(cd code-of-conduct-src; bundle; bundle exec jekyll build --destination ../code-of-conduct)
(cd workshop-map-src; bundle; bundle exec jekyll build --destination ../workshop-map)
```


To run the site:

```
bundle exec jekyll serve
```

point your browser at: http://localhost:4000/


## Deploying the site

[![Build Status](https://travis-ci.org/bridgefoundry/bridgefoundry.github.io.svg?branch=master)](https://travis-ci.org/bridgefoundry/bridgefoundry.github.io)

The site is deployed with Firebase hosting and should automatically deploy
whenever a change is checked into master.  If there are any issues, please
send email to admin@bridgefoundry.org

When we update the code-of-conduct or workshop-map, then we need to make some
kind of change to this repo (such as this README) in order to trigger a new
deploy.

To test out changes, any commits to `staging` branch will be automatically
deployed to https://bridgefoundry-staging.firebaseapp.com/
