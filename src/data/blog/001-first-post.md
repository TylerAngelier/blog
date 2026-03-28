---
title: First Post
author: Tyler Angelier
pubDatetime: 2025-07-26T21:59:39Z
slug: first-post
featured: true
draft: false
tags:
  - astro
  - cloudflare
description: My first blog post using Astro & Cloudflare Workers.
---

Welcome to my blog! This is my first post with the new blog setup. This time, I’m using [Astro](https://astro.build) and [Cloudflare Workers](https://workers.cloudflare.com/).

## Table of Contents

I haven't blogged in a long time. My [last blog article](https://medium.com/@tylerangelier/oracle-pipelined-table-functions-part-one-99696c95e60b) was way back in August of 2019! Honestly, I’ve been wanting to get back into the habit of documenting the things I work on and sharing that knowledge through a blog again.

With the rise of AI tools (which I’ve been spending my "extra" time playing with), I finally got the motivation to rebuild my blog—ironically, with a little help from AI itself.

The tech stack here is pretty straightforward. The blog is built using [Astro](https://astro.build). I’d heard about it through work at Oracle and figured I’d give it a shot. I initially considered [Hugo](https://gohugo.io/) since I’d used it before and was planning to host with GitHub Pages. But during a chat with ChatGPT about building this blog, it suggested [Cloudflare Pages](https://pages.cloudflare.com/) as an alternative host.

I started researching and decided to go with Cloudflare for hosting. I've used GitHub Pages before, and while it worked fine, I’ve been using Cloudflare for DNS for _years_. They consistently deliver top-notch tooling, and switching things up felt like a good way to stay engaged in the project.

Now here’s where the first curveball came in: after deciding to go with Astro, I found out Cloudflare is [shifting focus away from Pages](https://developers.cloudflare.com/workers/static-assets/migration-guides/migrate-from-pages/) and encouraging new projects to use Cloudflare Workers instead.

So, I pivoted to Workers. Naturally.

Okay okay, getting ahead of myself. Like any dev-blogger, the theme was pretty important to me. After _intense hours of research_ (courtesy of ChatGPT o3), I landed on [AstroPaper](https://github.com/satnaing/astro-paper). It’s well-supported and highly customizable—two things I really wanted. Plus, it looks drop-dead gorgeous and nails the little UI details. The way the color bar grows as you scroll? Chef’s kiss.

## Setup

### Astro

Run the install command for Astro using the AstroPaper template:

```bash
npm create astro@latest -- --template satnaing/astro-paper
```

That’s basically it. The README includes a great table of common commands, but I was mainly looking for `pnpm run dev` to preview the default blog layout. The starter content is robust and gets you up and running fast.

Some tweaks I made:

- Customized constants in `config.ts` and `constants.ts`
- Removed sample blog content and images
- Cleaned up the README

### GitHub

The usual workflow:

- Created a new repository
- Pushed everything up

### Cloudflare

I already had an account and domains with Cloudflare, so this part was quick.

- Logged in
- Navigated to the Workers section
- Started a new project from the GitHub repo
- Plugged in the build and deployment commands (from the AstroPaper README)

Then, I added a `wrangler.jsonc` file in my local repo—this tells Cloudflare Workers how to run the project. Here's the simple config I started with:

```jsonc
{
  "name": "blog",
  // Update to today's date
  "compatibility_date": "2025-07-26",
  "assets": {
    "directory": "./dist",
  },
  "observability": {
    "logs": {
      "enabled": true,
    },
  },
}
```

I committed this file and kicked off my first build! Naturally, it failed at first because `npx wrangler deploy` couldn't find `wrangler`—I hadn’t installed it. A quick `npm i wrangler` fixed that.

And now, the blog is live at: https://blog.trangelier.dev/ 🎉
