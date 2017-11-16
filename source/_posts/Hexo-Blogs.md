title: Hexo Blogs
author: Emil Hein
tags: []
categories: []
date: 2017-02-24 22:29:00
---
## This blog

Is written in hexo. Hexo is simply a node project that presents markdown files in a pretty way (as a blog). As its markdown its pretty convinient for a blog about development, as you will find a lot of documentation in this format. 

With the admin plugin it almost fells like wordpress, but with all the code completly customizable. The plugin makes it way easier to manage your blog.


``` bash
// This command will generate all the static files that you need for your blog
$ hexo generate
```


``` bash
//This command simply starts the server, so you can see you blog before you deploy it.
$ hexo server
```

###### Deploy/host
How to host and deploy your blog is up to you. Every hexo blog comes with a _config.yml file, for all the settings of your project. One of the things you can specify is, what and where you want to deploy your static files. 
In depth you can read more about it here: [Hexo documentation](https://hexo.io/docs/deployment.html)

I have set this up to github pages, as this blog only consists of static files.
My deploy configuration looks like the following.

``` yml
deploy:
  type: git
  repository: https://github.com/emilhein/emilhein.github.com.git
  branch: master

```

Then when i run the floowing command my files will be deployed and saved in sourcecontrol
``` bash
// This command will generate all the static files that you need for your blog
$ hexo deploy [commit message]
```

