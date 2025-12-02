---
layout: post
title: "Beginning Unix Networking"
date: 2025-12-01
gif: assets/gifs/Networking.gif
excerpt: Cobbling Together My Beginner's Understanding Of Unix Networking.
featured: false
---

To force myself to review the content I've been learning lately, I am writing this post to give a beginner's recap of computer networking in Unix.

## What Is A Socket?

A socket serves as an endpoint for sending or receiving data across a computer network. It is an API within your OS that allows you to send and receive data over a network. In order to instantiate a socket in C, one must call `socket()` and a file descriptor for the socket will be returned.

### What Makes Up A Socket?

By looking at the man page for `socket()`, we can see that sockets are comprised of three parts:

1. **Domain** - You pass in what kind of socket you are interested in. For common sockets this will be either `PF_INET` (IPv4) or `PF_INET6` (IPv6)
2. **Type** - This parameter allows you to determine the communication type of the socket. Meaning, this parameter dictates how data will be delivered.
3. **Protocol** - For most cases, put 0 and the OS will figure out the appropriate choice.

## So Then What Do I Do With A Socket?

Once you create a socket the fun begins! You can now use other networking system calls to send and receive data across networks.

### Disclaimer

While it is definitely possible to use socket networks across wireless networks, this requires port forwarding or other techniques and this is not covered in this explanation. However, with my upcoming projects this will eventually be covered.

## Client-Server Relationship

The best place to understand the aforementioned system calls is a classic, simple client/server connection. These descriptions are mostly conceptual; there are VERY common tools within Unix networking not covered in this guide. For a more practical, code-oriented example please see the GitHub repo linked at the bottom.

### Client Side Setup

#### 1 - Socket Setup

The first step in creating a client is to create a socket on one computer with a `socket()` system call. This system call will give you a file descriptor you can use `send()` with.

#### 2 - Let's Connect!

Once you have your socket created (be sure to error check the system call), you can then establish a connection with `connect()`.

#### 3 - Receiving Data

Now that you are connected, there are a variety of receive system calls depending on your connection type. For TCP connections use `recv()` and for UDP connections use `recvfrom()`.

#### Client Review

The general pipeline for a client is to set up their respective socket, connect to the host machine, and receive data. Again, this simplistic, generalized overview of the client side is supplemented with a code example in the GitHub repo at the bottom.

### Server Side Setup

#### 1 - Socket Setup

Similar to the client, the server must also designate a socket and receive a file descriptor back. The server also performs this with `socket()`.

#### 2 - Binding To A Port

Unlike the client, the server must bind its socket to a specified port. When a client attempts to connect to the host, it needs the IP address and the port number. The `bind()` function binds the IP address and specified port.

#### 3 - Listening

Once your socket is connected to a specified port, you can designate it to start looking for incoming connections with `listen()`.

#### 4 - Accepting Connections

When an incoming request arrives, the server uses `accept()` to accept the connection. This creates a new socket specifically for communicating with that client.

#### 5 - Sending Data

Once a connection is established, the server can use `send()` for TCP connections and `sendto()` for UDP datagram sockets.

## Code Example

As promised above, here is a link to my GitHub repo that includes .c files that create server and client executables:

[GitHub - WebServer](https://github.com/AndrewJMart/WebServer)

---