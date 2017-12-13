title: Travis automation
author: Emil Hein
tags:
  - Travis
  - Build
  - automation
categories: []
date: 2017-11-29 23:51:00
---
Since i just setup automatic deployment of this project, whenever i commit to the master branch, i want to display it here:


```yaml

language: node_js
node_js:
- stable
branches:
  only:
  - master # Only build on master
install:  # What i need to install on Travis in order to build
 - npm install
 - npm run generate # This refers to a script in package.json
before_script:
- sed -i "s/GH_TOKEN/${GH_TOKEN}/" _config.yml # This is to take my github token from travis settings
script:
- npm run deploy # my package.json deploy script
```