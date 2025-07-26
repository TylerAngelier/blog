---
title: First Post
author: Tyler Angelier
pubDatetime: 2022-09-21T05:17:19Z
slug: first-post
featured: true
draft: false
tags:
description: My first blog post using Astro & Cloudflare Workers.
---

Welcome to my blog! This is my first post with the new blog software. This time I am using [Astro](https://astro.build)
and [Cloudflare Workers](https://workers.cloudflare.com/).

## Table of Contents

I haven't blogged in a log time. My [last blog article](https://medium.com/@tylerangelier/oracle-pipelined-table-functions-part-one-99696c95e60b)
was in August of 2019! Honestly, I've been wanting to get into the habit of documenting things I work and sharing that information
via a blog again. With the rise of AI tools (what I've been spending my "extra" time playing with) I got motivated to build
out my blog again, with the help of AI.

The technolgy stack here is quite simple. The blog is built on [Astro](https://astro.build) - I've heard about it from my job
at Oracle and figured I'd give it a try. I was going to go with [Hugo](https://gohugo.io/) as I've played around with that software
before and was going to use GitHub Pages to host it. In my chat with ChatGPT on building this blog, it called out [Cloudflare Pages](https://pages.cloudflare.com/)
as an alternative hosting provider. I started to research that and decided I'd try using Cloudflare for hosting. I've used GitHub Pages before
and while it was fine, I've Cloudflare for DNS for _years_. They always seem to deliver top-notch software and the changeup of things should help
keep me interested in the project.

This was the first curveball after deciding to go for Astro. Cloudflare is pretty clear they are [leaving Cloudflare Pages to the wayside](https://developers.cloudflare.com/workers/static-assets/migration-guides/migrate-from-pages/)
and anyone starting a new project should start with Cloudflare Workers. Well, that's obviously me so off to using Cloudflare Workers now!

Okay okay, getting slightly ahead of myself. As any developer who blogs, the theme was pretty important to me. After _intense hours of research_ (being performed by ChatGPT o3)
I found [AstroPaper](https://github.com/satnaing/astro-paper). It's well supported and customizable, which were two things I was looking for. Oh and of course,
it looks drop dead gorgeous with attention to the small details. The way the color bar increases as you scroll through the article is :cheff-kiss:

## Setup

### Astro

Run the install method for astro and use the AstroPaper template.

```bash
npm create astro@latest -- --template satnaing/astro-paper
```

This is really it. The readme includes an awesome table of commands to run, but of course what I was looking for is `pnpm run dev` so I can
see the default blog configuration. It comes with plenty of sample material to get you started. Some items I did was

- Configure some constants in `config.ts` and `constants.ts`.
- Remove sample blog content and images.
- Cleanup readme.

### Github

Normal stuff. Create a new repository and push the changes up.

### Cloudflare

I already had an account and domains with Cloudflare, so this was super simple.

- I signed in
- Went the workers section
- Started a new project from an existing repository
- Plugged in the build and run commands per the readme

After that, I came back to the local repository and made a `wrangler.jsonc` file - this tells Cloudflare Workers how the project works.
A very simple configuration to start with.

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

Committed this file and ran my first build! Of course, the first build failed because my deploy command was `npx wrangler deploy` and `wrangler` wasn't installed.
This was easily fixed by running `npm i wrangler`.

Now the blog is live at https://blog.trangelier.dev/about/!
