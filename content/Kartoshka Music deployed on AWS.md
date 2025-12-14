---
title: Kartoshka Music deployed on AWS
description: Kartoshka Music, a Django web app that connects to Spotify to aestheically display album art, is now deployed on AWS.
date: 2025-01-06 17:36:00 +0000
categories: [Software, Projects]
tags: [aws, projects]
author: daniel
image:
  path: /assets/img/KMusic/kmusic-bb.jpeg
  alt: Screenshot of Kartoshka Music
---
# Kartoshka Music

[Kartoshka Music](https://kmusic.danielspyros.com) was the second Django site I built, created in 2021 to address a personal annoyance with Spotify's desktop app: the nanoscopic album art. By connecting to the Spotify API, my web app showcases large album art, recent plays, and artist backgrounds for a more aesthetic experience.

Here is a screenshot of **Spotify**'s desktop full screen player:

![Screenshot of Spotify Desktop](/assets/img/KMusic/spotify-bb.png)

I think you will agree that it is not the most beautiful. It is quite dim and you cannot properly appreciate the album art without a magnifying glass.

Now have a look at **Kartoshka Music**'s UI:

![Dcreenshot of Kartoshka Music](/assets/img/KMusic/kmusic-bb.jpeg)

Much better, right? It is bright, the album art is big, you can even see the album art of the last songs you were listening to.

## Deploying Kartoshka Music

Initially, I deployed the site using PythonAnywhere, which was free and easy to use due to its integration with Django. However, this simplicity meant I learned little about the deployment process.

I open-sourced the [code](https://github.com/DanielJMWilliams/KartoshkaMusic) and left the project untouched until last month when my ex-colleague, Ish, showed interest in it and helped me explore a new deployment approach. Ish containerised the code and together, we redeployed it using AWS and Terraform. Over a few calls, Ish guided me through:

- Setting up a **Virtual Private Cloud (VPC)** with security groups.
- Using **GitHub Actions** to automate updates to the Elastic Container Registry (ECR) and running containers in **Elastic Container Service (ECS)**.
- Configuring **Route 53** and **Certificate Manager** to connect the site to **[kmusic.danielspyros.com](https://kmusic.danielspyros.com)**.

One of the significant advantages of using Terraform is that it enables me to destroy and recreate the AWS configuration at will. This makes the setup both flexible and reusable for future projects.

This experience gave me valuable insights into containerization, cloud deployment, and automation pipelines. You can check it out live at **[kmusic.danielspyros.com](https://kmusic.danielspyros.com)**!

Expect blog posts in the future detailing how to deploy sites on AWS.
