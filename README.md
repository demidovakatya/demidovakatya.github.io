# My Awesome Blog

## How-To

Otherwise I'll forget. 

### Create post

To create a new post, you can run the following command:

`$ hexo new [layout] <title>`

Post is the default layout, but you can supply your own. Change the default layout by editing the `default_layout` setting in `_config.yml`.

```
title: page title
tags:
  - aTag
  - anotherTag
id: 418
categories:
  - aCategory
  - anotherCategory
date: 2013-11-06 06:40:12
---

Some text i'd like to have in the body of this post
```

### Generate static files

`$ hexo generate`

### Deploy

`$ hexo deploy`
