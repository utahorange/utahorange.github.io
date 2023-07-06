---
layout: post
title: Review of TCP/IP for Dummies
date: 2021-8-9 14:19:00
description: archive of a post I wrote in 2021, edited for grammar-ish
tags: networking
categories: 
thumbnail: 
---

# Preface
I’d like to first apologize for my writing style; I’m trying to make it less formal and hopefully more expressive. When I talk about “cisco curriculum”, I’m referring to material that cisco instructors at my high school teach to students.

## Overall Thoughts
**First Impression**: For a beginner book, it's quite detailed. However, it's also quite outdated.

**Content**: Again, it's somewhat outdated, especially in terms of security practices. It goes over **extremely** general security practices (secure password, no admin, phishing, spearphishing, DDOS) and especially their theory. Overall, it goes over networking theory as well as set-up quite well. They have nice screenshots of configurations and labeled steps in how you would accomplish most things. However, this isn’t as helpful as it seems since the book refers to older distributions such as Leopard and Windows Vista. The way protocols interact with each other (TCP handshakes, VPN setup, etc) still holds up today but that's kind of the point of internet protocols anyway. I liked the section about IPv6, but I might be biased since this was my first real dive into IPv6.

**Overall**: Expect a lot of theory knowledge that is good fundamentals for more complicated stuff. The authors understand that learning networking is not exactly what people do on summer break, so they make up for it with jokes, easy-to-understand analogies, and an over-encompassing theme of the TCP/IP cake. Some of the parts seem kind of like common sense but knowing the vocab in those chapters will help you a lot in the future. You’ll get an idea of what a network admin does and how to set things up; this information will transfer somewhat indirectly to modern-day devices.

## Tips for reading this Book and Understanding Network Info in general

Okay, listen carefully kids:
* Please take breaks when reading. This stuff is painful to read sometimes (and I don’t mean painful as in *Looking for Alaska* emotionally painful but as in *arduous* painful). To me, it was actually interesting but that’s because I knew most of it. This goes for networking in general. Take breaks, think about what the network is actually doing in the diagram, go for quality not quantity...
* **Analyze the diagrams** Oftentimes, I find myself reading through text and think “wow I am such a fast reader”. Then, I try to understand the diagram on that page and don’t understand a single thing. Understand the diagrams so you get something out of this book.
* If you know it, lightly speed-read the chapter or section but try not to skip the entire thing. If you’re really pressed for time, read the harder parts. Be glad this book has some troubleshooting chapters but they're definitely nowhere near comprehensive.

## Ok time for some (very little) knowledge
I don’t want to bore you guys; the book will be more interesting than hearing me ramble. Here goes nothing…

### Very generally speaking
Networking is the transfer of packets between hosts/nodes/devices/PCs (essentially most of these names represent the same thing). Packets have layers (just like onions), which are in reality, headers. We can say there is an IPv6 header on this packet, or maybe an IPv4 header if it’s going through an IPv6 over IPv4 tunnel. A packet has information, most fundamentally it should have:
host address (IPv4 or IPv6 or mac address of sender)
destination address (IPv4 or IPv6 or mac address of receiver)
payload
Of course, a packet varies A LOT. You might have timeouts (TTL), different headers for different protocols, and whatnot. And these different protocols represent part of the TCP/IP cake.

### Part I: TCP/IP from names to addresses
Protocols are rules for how people should communicate. These protocols are defined by a bunch of different organizations, sometimes even corporate/proprietary ones, like from cisco. RFCs are how we keep track of these TCP/IP rules. It talks about intranets and extranets, but in my mind, they’re basically synonymous with LANs (local area networks) and WANs (wide area networks). Essentially a LAN or an intranet is a private network like maybe a university network or the high school computer network. The internet or other large networks can be considered as WANs.

### Part II: Getting connected
Some DHCP, IPv6, BGP, etc. In cisco class, you learn about RIP and OSPF. The overall idea is the same, but BGP is extra special since it works on larger routers/networks. BGP stands for Border Gateway Protocol and works between autonomous systems (which are like big networks), while OSPF and RIP work inside autonomous systems.

### Part III: Configuring Clients and Servers: Web, E-Mail, and Chat
This is pretty relevant for web challenges in CTFs in terms of theory, but it won’t help you with how to actually solve challenges.

### Part IV: Even More TCP/IP Applications and Services
This goes over a bunch of stuff not in the cisco curriculum (but possibly in Netacad), such as Mobile IP, VoIP, File Sharing/FTP, telnet and remote sessions. 

### Part V: Networking Troubleshooting and Security
Again, kind of general in my opinion (e.g. it says “use firewalls”, but not necessarily firewall rules, etc). Network troubleshooting is pretty important and it gives the major commands of netstat, ps, traceroute, and ping which should sound somewhat familiar. However, some common problems when setting up a network is not discussed unfortunately, probably because it requires yet more theory knowledge.

### Part VI: The part of tens
Honestly not much to know here. Some random (maybe?) interesting links and some places to look for more information. Basically skipped this part.

TLDR: Good book, not exactly hard to read, but quite long. I would say it’s definitely worthwhile for a good summary or introduction, but don’t rely on it too much.