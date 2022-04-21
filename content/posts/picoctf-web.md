---
title: "picoCTF web exploitation writeups"
date: 2022-03-23T23:42:04+01:00
showDate: true
draft: false
tags: ["writeup"]
---

Hey, this is a simple writeup on the challenges provided by [picoCTF](https://picoctf.org/)

Hope you find it useful ;)

&nbsp;

## Get aHEAD
For this challenge you should think about the HTTP request methods (GET, POST, PUT, DELETE, HEAD,...)

See the HEAD there? Does it look like something you have on the title of the challenge? xP

The HEAD gives you the website's metadata. It should do the same thing as a GET but without all the body, although sometimes they are different.

You can use Burp Suite to check the responses but I think there's a simpler way to get it! Open up a terminal and type:

```
curl -I http://mercury.picoctf.net:28916/
```

If you go to the curl options, the -I is how youll get the HEAD.

&nbsp;

## Cookie
This challenge puts your dev tools knowledge to the test eheh

In Google Chrome press F12 and go to the "Application" tab.

You'll see the cookies there, mess around with the value and find the right one to give you the challenge flag.

It's funny that you can think about several ways of using this in a pentest or vulnerability assessment.

One of the most common examples is an e-commerce website where normally the checkout carts could have a cookie session ID that you could change and see the cart of another person. Now imagine this on a bank application where you could have access to other people's accounts and mess with it... Nasty!

&nbsp;

## Insp3ct0r
Knowing the previous one, this will be a walk in the park!

Just go to the "Sources" tab this time and see all the files there.

Normally, when developing websites with HTML, CSS and JavaScript, either using all of them or just a few, developers often leave notes from previous tasks that are not supposed to be there. And they could be admin credentials, hidden pages, undeleted login info or other high security risk information that can be exploited.

&nbsp;

## Scavenger Hunt
This is a little bit trickier than the last one.

Yes you start exactly like the last one but you'll have to master some other web shenanigans :)

So lets take a look at the steps required:

1. Go to the "Sources" tab
2. Check the (index) file --> 1st flag part
3. Check mycss.css file --> 2nd flag part
4. Get clue on myjs.js file. Do you know which file are they talking about?
5. Add "/robots.txt" to the URL --> 3rd flag part. There's a clue in it about an access configuration file.
6. Remove previous one and add "/.htaccess" --> 4th flag part. There's yet another clue in it about the macOS storage system
7. Remove previous one and add "/.DS_Store" --> 5th flag part


All files in a website may contain valuable information for possible exploitation! Specially if those are configuration files that could be tempered with.


&nbsp;
&nbsp;

---

will add more, just don't really know when :P

---
