---
layout: post
title: Playing with Threads for Matmults Part II
date: 2025-4-1 15:00:00
description:
tags: concurrency
categories: 
thumbnail: 
---

Previously, I tried to parallelize matmults with my very beginner-level of C++ knowledge. What I learned from that I chronicled here. Lo and behold, my introduction to computer organization class taught me about OpenMP, which is like the one major C++ concurrency API. This was quite awesome.

So I was obligated to come back and implement matmult, but better this time, and hopefully not as naively. This is how it went down.