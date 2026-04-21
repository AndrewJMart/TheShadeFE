---
layout: post
title: "Why Learn Computer Networking"
date: 2026-4-18
gif: /assets/gifs/LearningNetworking.gif
excerpt: Continuing My Journey For Knowledge.
featured: true
---

# Why Learn Computer Networking?

Coming from a mathematics background, Computer Networking was a topic often glossed over in the classes I took. In introductory classes this did not matter, however as you progress in your journey as a developer this quickly causes problems. Specifically, I remember looking at the CORS set up for my API in distributed computing as if it were hieroglyphics.

Computer Networking is quite the rabbit hole, there really is no end to how much you can learn, but even learning the basics I argue will grealy increase your literacy as a programmer and developer. The chances that all of your programs have zero meaningful interactions with the internet are quite low, so it is a topic that you will eventually have to confront.

# Where You Should Start

There are many acclaimed resources to learn networking topics, however the one I stumbled upon is [High Performance Browser Networking](https://hpbn.co/). The first section of the book is a networking 101 refresher, which provides solid depth with great visuals and explanations.

Furthermore, I think learning about the performance side of how networking is great. When you are developing any type of web application, reading through this resource, even just skimming, will provide you a newfound checklist to boost your web app's performance.

# A Quick Primer

As previously mentioned Computer Networking is quite the rabbit hole. There are definitely diminishing returns to the learning you put in and I believe a quick primer could teach you a great deal. Below I will cover topics in some depth.

## The Classic Question - What Happens When You Enter Google.com Into Your URL

### DNS Search

First, when you enter a URL into your browser, your browser needs to parse that URL to a destination. The way this works is with a DNS search. Your browser will first check local caches, and if a destination IP is not available it will initiate a DNS query with your ISP. The result from a DNS search or query is a destination IP.

### TCP Connection

Your destination IP provides your network connection with routing, however there are no guarantees baked into IP protocol. Meaning, if you send packets, there are no guarantees they will reach the destination, be in order, or not be corrupted. Because of this, TCP is a protocol built on top of IP. TCP's main guarantees/perks are the following. Your packets will reach the destination (eventually), they will be read in order, and they will not be corrupted. With your destination IP, your browser will start a TCP handshake, which goes as follows. Your browsers send a SYN (to sync with your server), your server will then ACK (acknowledge the SYN) and send it's own SYN. Lastly, your browser will ACK the server's SYN. Once this roundtrip is completed, your TCP connection has been established.

### TLS Connection

At this point your browser and server can use application protocols like HTTP and HTML to communicate back and forth, however if someone intercepts your traffic it will be unencrypted. This is where the TLS layer comes in. Your browser performs another round trip handshake as follows. Your browser first sends over it's supported cipher suites and TLS versions. The server will then select a matching cipher suite and TLS version, along with sending back it's respective certificate. Your browser will verify this ceritifcate using chain of trust from an approved Root CA and will then set up the EDHKE. At this point, your content is now encrypted!

### Application Data At Last! (At Least The Happy Path Version)

At long last you have application data. You can now freely use HTTPS to communicate back and forth. However, this doesn't take into consideration a whole host of other things. Concepts like CDNs, Websockets, HTTP 3 with UDP, what different versions of HTTP entail, IFrames, Dynamic Trackers (like google analytics), how a browser actually works, etc. This blog post is just a scratch on the surface, however I encourage you to take a stab!

## Command Line Utility

Understanding this basic process does provide you with utility. Understanding this initial set up, along with HTTP makes debugging your web apps much more intuitive. Prior to learning this, I felt like I had to memorize what to do in what case, however when you build an understanding the solution falls out.

For DNS issues, use dig. So if you cannot connect to your website, a first initial test would be to see if the DNS search resolves to the correct IP, this would be with dig.

If your website is resolving to the right IP but you cannot connect, you can use a verbose curl to suss out why that is.

Lastly, if you are testing endpoints understanding curl and HTTP allows you to better understand how to format payloads etc.

Furthermore, understanding this process enables you to utilize the dev tools available in Chrome, Safari, etc. Like the network waterfall tab, JS console, and element tab for DOM inspection.

# Summary

Even for non webdevs like me, webdev is unavoidable and should be utilized to showcase your projects. Because of this, having a baseline understanding of what is going on underneath the hood helps you have essential critical thinking skills when debugging or interacting with projects or prod sites. Computer Networking may not be the most glamorous area to study, but a simple day's worth of studying will yield critical knowledge!