---
layout: post
title:  'why this blog'
date:    2018-10-29 14:51:10
categories: 
---

This is not my first time blogging.

My first blog was setup on RedHat on one of their free instances on rhcloud.com during my sophomore year of high school. It was a Ghost Instance that served me well until RedHat sunlighted their free tier :(. The blog failed because I had trouble keeping up with a 2 week post output schedule which wasn't ideal given my schedule and emotional turbulence at the time.

I intend for this blog to mainly focus on what interests me, that is, at the moment, a combination of CS, philosophy, and literature. If I do find interest in other things, those have the potential to come up. The only exception to that is politics, which despite my large interest, I'll try to keep down (_marks politics posts under philosophy instead_).

This blog also serves as a sort of emotional venting place for me too (why I decided to pick up blogging again lol), so there's a potential for rants (although I'll really try to keep it clean).

There's a couple key differences between my last blog and this one. My last one directly ran under [ghost's CMS](https://ghost.org) with an admin panel and everything. There was also an [electron](https://electron.atom.io) desktop app wrapper that I could use.

Even though the blogs look visually the same, the underlying code is different. This site is powered by Jekyll, a static site generator. Unlike a CMS like wordpress, jekyll doesn't have a login page or any endpoints; there's no server involved. It just serves raw HTML, CSS, and Javascript. All of the preprocessing and generation instead happens beforehand, on my computer, where it'll turn markdown files into the files that are rendered before your very eyes.

This presents some huge advantages over using a CMS. For one, for the most part, I don't have to worry about security. Since the site is all static, there is no server or endpoint for the client to manipulate. The most an attacker could do would be some request forgery or cross site scripting (XSS). Secondly, static sites load much faster in general compared to dynamic sites due to lower overhead.

### But why a blog?

I chose a blog over something like Twitter or Mastodon due to the need to make lengthier content. In this day and age, where people can be easily be quoted out of context, where an entire idea gets reduced to a single witticism to fit lowered attention spans, I prefer longform. 

Hopefully (lol hopefully), I'll be able to get this blog setup and up and running within the next couple weeks or so. I still need to integrate the Medium API to cross-post and want to create some sort of desktop jekyll live editor thingamajingy (I'm writing this in emacs right now).

