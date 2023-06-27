---
layout: project
type: project
image: img/tcpserver/logo.png
title: "Simple Client-Server | TCP & UDP"
date: "Jun 2023"
published: true
position: 7
labels:
  - TCP
  - UDP
  - Socket Programming
  - C++
summary: "Developed two basic servers using TCP and UDP protocols that offer identical functionality and possess the ability to handle multiple clients concurrently. Additionally, built separate clients for each server, where every client transmits a substantial (larger than the buffer size) message to its server. Upon receiving the data, the server displays it on the screen."
---

## Objective

The aim of this project is to learn basics of socket programming utilizing **TCP** and **UDP**. For this, I developed two basic servers using TCP and UDP protocols that offer identical functionality and possess the ability to handle multiple clients concurrently. Additionally, built separate clients for each server, where every client transmits a substantial (larger than the buffer size) message to its server. Upon receiving the data, the server displays it on the screen.

(This is work in progress project!)

## TCP

* After establishing the connection, the client sends messages using fixed-length byte streams.
* On the server side, for now the process is forked into a child process. The child process maintains an open connection with the client until it receives all the data. Once all the data is received, the connection is closed, and the child process terminates.
* To handle multiple clients, multiple child processes are created, with a limit of 8 clients. Each child process is responsible for handling the communication with a specific client. This allows the server to handle concurrent connections from multiple clients, up to the specified limit of 8.
* I am currently working on trying out `select()` calls and multithreading to handle multiple clients instead of forking the process.

## UDP

* Since UDP is not connection-oriented, for each message received on the server, a separate child process is created. This child process is responsible for handling the specific message received on that particular socket. 
* The child process displays the last message received on the corresponding socket, as there is no inherent connection or sequencing of messages in UDP. This approach allows the server to handle multiple messages concurrently and display the most recent message received on the socket.

#### Source Code

This project is WIP. Source Code is present [here](https://github.com/pallavi-garg/filetransfer).