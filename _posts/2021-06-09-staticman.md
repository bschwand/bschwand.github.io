---
layout: single
title:  "Staticman comments"
date:   2021-06-09 21:01:00 +0200
categories: web
tags: staticman

---

Well, when I started with [Jekyll](https://jekyllrb.com/) to create my blog, one of the contributing factors in so choosing was the comment system. [Staticman](https://staticman.net/), notably, allows comments to be made which are actually PR merge requests in the blog site repo. The whole blog is still static and integrated in github as backend.

I thought enabling staticman would be really easy... unfortunately, not so. As starter, it actually needs a service which handles the http GET and POST requests which then are turned into a PR request. Since the public service is saturated, I had to deplox an instance for my blog. Which means, forking the staticman repo, opening an [heroku](http://www.heroku.com) account to run that service which, incidentally is a... node.js daemon. Grr. Gotta hate this web JS shit. I will never understand why an untyped language with like 3 different equality operators and none of the good stuff promoting solid and bug-free engineering got so popular. Oh, yeah, because of "Web developers".

Anyway, it was quite a journey to get staticman working between RSA certificates, multiple accounts, extra git repositories, and layer after layer of configuration all over the place. Seems that anyone who creates a blog with Jekyll goes over the same crap and puts a gigantic blog post about it, so I am not going to repeat this, however I will give the link to all the posts and web pages which helped me get this working. Although there is still one piece that is not working: the github webhook. Whenever the webhook is invoked by github when a PR is created, the staticman service croaks with an error. Too bad, I just disabled this in the end as everything else is working ok. I still get the email notifications so I really do not care about the webhook.

In the end, I got everything I wanted working: comments on my blog posts, akismet for anti-spam

As reference:

- <https://www.mrumpler.at/comments-with-staticman/>
- <https://knightcodes.com/miscellaneous/2016/09/13/fix-github-metadata-error.html>
- <https://github.com/mmistakes/minimal-mistakes/issues/1544>
- <https://www.mrumpler.at/comments-with-staticman/>
- <https://hajekj.net/2020/04/15/staticman-setup-in-app-service/>
- <https://spinningnumbers.org/a/staticman-heroku.html#webhook>
- <https://github.com/eduardoboucas/staticman/issues/389>
- <https://github.com/eduardoboucas/staticman/issues/83>
