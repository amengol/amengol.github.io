---
title: Hello World!
subtitle: It is a Hello World, but you may find it interesting!
layout: post
---
How do we start anything in the software developer world? Ok, you already saw the tittle, so here it is. But instead of just make a meaningless Hello World post, I want to talk more about how easy it can be to get a site like this up and running in a short period of time.

You may or may not have notice it, but this site is a Gitgub Page. Yep, besides being this wonderful collaboration tool, you can also host your page on Github, and the better is that it is free.

As a software developer you might know that having a website to propagate and concentrate your work is one of the most important key features for success is this demanding industry. However, if you like me are not a web designer, things can become really complicated pretty soon and if you want to use your "free" time wisely, you don't want to spend too much time just trying to get a simple blog/portfolio page running.

### How about WordPress?

This is usually the first suggestion you will hear from bloggers all over: WordPress. It is heavily popular among blog and similar sites. There are tons of services (and a lot of good ones) for it and you will encounter plenty of good material on the Internet to help you run your website based on it. The problem is that, for most of a blog/portfolio site needs a WordPress is like killing a fly with a cannon bullet. Besides that, you will need to spare a good amount of time just to know "wordpresseology" as I might say. First, you will need a reasonable service to host your WP site and this is not free, most of the time. Second, you will have to maintain it thought its Administration Panel and take care of all its configurations, pages, posts, media files, plugins tools, users... As I said, there is lots of good material to help you with the task of maintaining a WP site, but the question should be: Do you really need all of this stuff for your site?

### What makes GitHub pages a better option?

You might answer what would be the scope of your site in the first place. If you thinking on having some serious services on it, probably GitHub Pages is not for you, but if you are in the majority group of software developers in the market that just want a simple page to refer to when asking for a portfolio or blog, GitHub Pages can be your place to go. 

If you are already sharing some work on GitHub you probably have wrote some READEME.MD files. They are plain text files using a very simple markup language: Markdown. Believe me, it is extremely simple and useful, and with just some special characters you can format your text pretty well and GitHub will read it like an HTML file. If you want to see how it works, take a look <a href="https://guides.github.com/features/mastering-markdown/" target="_blank">here</a>.

But if you still want to use HTML language you can use it in a markdown file, or better, you can use your html file directly. Neat, right?

### How GitHub Pages work?

GitHub pages are static pages that are automatically generated for you from your post markdown or html files. All you have to do is create a repository with your usarname and GitHub will do the rest for you. This repository will be the place where your files are stored and you can treat it like any other repo that you have been working with. The difference is that if you type yoursername.github.io it will render your `index.md` or `index.html` file.

### Is there a theme or something?

Yes. You can choose between a bunch of official <a href="https://pages.github.com/themes/" target="_blank">supportted themes</a> and personalize it the way you want. If you go to your repo settings, there is also a GitHub Pages tab where you can choose one of them. But this is really just a matter of putting the name of the theme into the `_config.yml` file in your repo.

### \_config.yml?

This is the place where you configure some parameters for your site. When you just start your GitHub Page with a theme, it will only contain the name of the theme, but if you want to go wild, you can personalize it and your repo to have a lot of useful information for things in your site.

### I have heard about Jekyll themes too and it is becoming complicated now

If you started to look around for themes you may have heard about Jekyll. To make things easy, Jekyll is a kind of automatic factory that will build your static site pages from your plain text files (like markdown files). If you are running Linux you can have it building your site locally, so you can test it before going public. It will generate all your html files in a folder in your computer and they will be ready to be published at your website. Jekyll (and GitHub Pages) are all about static web pages generated "locally" and then published, by the way.

The good thing is that you don't need to touch Jekyll with GitHub Pages because it is already a kind of Jekyll, generating the static pages for you. However, if you want to use a different Jekyll theme, you may find it useful to have it running locally and then push your files to your GitHub repo page. This is not difficult too and it was what I did actually, as I wanted to use a different theme.

### I still finding Jekyll complicated and it does not run on Windows

You can run it on Windows too by installing the Ruby stack or Ubuntu on Windows bash. This might be a topic for a future post, but my advice is if you are just beginning to build your site, you can pretty much do most of it using just plain GitHub Pages with the already available resources.

### Ok then, show me the way
Creating your first GitHub Page is easy, just follow the steps here: 
<a href="https://pages.github.com/" target="_blank">https://pages.github.com/</a>

---
Well, this should be enough for a Hello Word post, don't you think? Please feel free to contact me if you have any question on this via one of the methods at the end of this page.

Thanks for reading,

Jorge Amengol