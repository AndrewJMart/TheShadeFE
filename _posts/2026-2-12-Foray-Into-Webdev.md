---
layout: post
title: "Foray Into WebDev - CompDoku.com"
date: 2025-12-30
gif: /assets/gifs/Sudoku.gif
excerpt: Creating an MVP Competitive Sudoku App.
featured: false
---

# Why WebDev?

As someone who comes from primarily a math background, there are computer science classes I was never able to take. Thus, there are many unturned stones within the computer science world I haven't quite explored yet. Among the most prominent was Web Development. To gather some knowledge in this area, I decided to create a simple website that allows people to both practice and compete amongst one another in sudoku.

# How was this site built?

## The Frontend

The frontend of this site was built with vite, tailwind, and TS. I am not a superfan of frontend, however I do believe it is an important skill to at least have a baseline understanding of.

## The Backend

Because I want to up my technical chops in C++, I opted to use Crow to develop the backend. The backend comprises of two major parts. One is a RESTful API setup for Practice. Meaning, the user sends a one way connection to my backend requesting a practice board, and receives both a playing board and a solution board for the client to check if the user is right. Secondly, I have a websocket connection for when users wish to compete against one another. A websocket connection allows for bidirectional communication between the server and client. This helps enforce wins and losses when a client closes their tab or loses connection, for once the websocket connection drops the other player is awarded a win. I did not have experience with websocket connections prior to this project and enjoyed implementing one.

## Wrapping It All Together

As always, the unsung hero of my projects is Oracle. Their always free tier for projects is enough to get something basic hosted and accessible for people online. I used a NGINX configuration to route traffic to my built frontend and a proxy pass to route appropriate requests to my backend. 

# Next Steps?

For now, I will put this project on the backburner, however I am sure I will come back to it. I really enjoyed implementing the Sudoku algorithms in C++, all of which can be seen here. Logins, leaderboards, and varying board difficulties are all things that can be implemented, which over time I am sure I will get around to. 

# Want to see the website or code for yourself?

Here Is The [Website](https://compdoku.com)

Here Is The [Website Code](https://github.com/AndrewJMart/CompDoku)
