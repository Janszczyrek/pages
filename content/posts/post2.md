+++
title = "CI/CD pipeline for updating this site"
date = "2025-10-09"
author = "Janszczyrek"
+++


## Intro
Manually logging into remote server and copying over changed files can be tedious. As they say, if you're doing something often and it cost you lot of time - automate it! In this post I want to show you how this blog is being updated after changes are made. 
## Tech stack
Im using Hugo - a [go](https://gohugo.io/) open-source framework for creating static websites. It's really fast and easy to setup. All pages are represented as Markdown files and are translated to HTML. For this site I'm using [Terminal](https://themes.gohugo.io/themes/hugo-theme-terminal/) theme, it's cool isn't it?
All relevant files are sotred as git repository on GitHub. It enables me to use Github Actions for defining pipeline to copy site over SSH to my VPS.
## How it works?
Every time when `main` branch is pushed workflow `deploy-to-vps.yml` is called. It creates temporary Ubuntu environment used for generating hugo's `/public` directory that stores ready to serve html files. Then it calls script which purpose is to copy these files to VPS using scp. Variables like hostname, port, username, key are stored as repository secrets.
