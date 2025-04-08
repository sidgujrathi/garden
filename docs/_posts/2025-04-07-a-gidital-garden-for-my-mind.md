---
layout: post
title: A garden for my mind and thoughts
date: 2025-04-07
categories:
  - Today I Learned
---
# April 07, 2025

I have always been fond of technical writing and learning. I often thought about having my own blog or some public space where I could share my learnings.  
In the past, I made several attempts — on Medium, Dev.to, and Tumblr — but for one reason or another, I couldn't keep up with writing or posting consistently.

Over time, I realized a plausible reason behind my infrequent posting:  

I was always trying to write for an audience, aiming to make posts educational or informational. This mindset often stopped me from simply posting my learnings, because I felt I had to structure everything carefully, keeping in mind the reader’s background and how they would perceive the content.

Fast forward to 2023–2024, I discovered the concept of PKMS (Personal Knowledge Management System).

> **PKMS** is a method for individuals to collect, organize, and manage information effectively to support their learning and growth.  
> It helps users filter relevant information, retain knowledge, and apply insights in their daily activities.

I started building my PKMS using Obsidian and other tools to manage my notes, learnings, and other relevant information.  
My goal was (and still is) to build a "second brain" to support all aspects of my daily life, including scaling up my skills and continuous learning.

While doing so, I also wanted to pursue writing — in a way that would fulfill my interest without stressing too much about structure or domain-specific content.

During this journey, I came across the concept of a **digital garden**.

> A **digital garden** is a personal online space where individuals can collect, curate, and share their thoughts and ideas in a less formal, evolving manner — similar to a notebook or personal wiki.  
> It emphasizes the process of learning and creativity over polished, finished content, allowing for exploration and growth over time.

I started looking for a way to build this without disrupting my ongoing PKMS and second brain workflow.

## Github Pages with Jekyll

While searching for ways to maintain a subset of my second brain/PKMS as a digital garden, I found a method that gives complete control: **GitHub Pages with Jekyll**.

- **GitHub Pages** — A free service to host static websites directly from a GitHub repository.
- **Jekyll** — A static site generator that converts plain text (written in formats like Markdown) into a website.

Since I already use Markdown for most of my notes, GitHub Pages was a perfect fit — it natively supports Markdown.

Jekyll, combined with GitHub Pages, helps generate static content automatically from Markdown files, making it an ideal lightweight solution.

## What I Learned

Today, I learned how to:

- Set up GitHub Pages for a specific repository.
- Configure Jekyll to build and serve notes as a website.

I created a repository called [`garden`](https://github.com/sidgujrathi/garden) and configured GitHub Pages to serve content from the `docs` folder, which holds all the Jekyll configurations and posts.

Now, my digital garden is live and accessible at:  

👉 [https://sidgujrathi.github.io/garden/](https://sidgujrathi.github.io/garden/)

## Workflow

- Everything — Jekyll setup, configurations, posts — is part of the `garden` repo.
- The only prerequisites are having **Ruby**, **Bundler**, and **Obsidian** installed on the machine.
- **Obsidian** helps me quickly write posts and generate templates in the format Jekyll expects.
- I have written a complete "Getting Started" guide in the repo’s `README.md` to make future onboarding easier.
- Workflow steps:
  - I use a template stored in Obsidian (`templates/_posts`) to create new posts.
  - Each daily note or post is generated with the required boilerplate inside `docs/_posts/`.
  - I write my content and commit it.
  - Once pushed to GitHub, the site automatically rebuilds and updates via GitHub Pages.

## What's Next

- I will practice keeping this **evergreen garden** updated as part of my learning habit.
- At the same time, I will also cross-publish the same content to [Dev.to](https://dev.to/siddharth_g).
- I'll observe how this setup supports my growth and adjust as needed.
