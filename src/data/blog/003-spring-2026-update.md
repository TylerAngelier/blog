---
title: Spring 2026 update
author: Tyler Angelier
pubDatetime: 2026-03-28T14:01:26Z
slug: spring-2026-update
featured: true
draft: false
tags:
  - ai
  - personal
description: Update since last post
---

It has been months since my last post, and, well, things have changed a lot.

Around the time of my last post, AI tools had evolved to the capability where they could make
edits to code and get them about 50-70% correct. You, the human, still had to get it to the finish line. Opus 4.5
broke the pattern by making broad changes across a codebase with great confidence and correctness. This was a turning
point in late 2025. It felt like the shift from "help me write this patch" to "go handle this part of the project."
GPT-5.2 was great, 5.3-codex was fantastic and 5.4 has been a stellar all-around model.

Then OpenClaw, which made a lot of people look at AI again. Codex started to feel like a real competitor to Claude Code.
[pi](https://pi.dev) got popular and it is just an amazing harness. Extremely customizable and flexible to anything
_you_ want to build in it.

I'm lucky enough to have near unlimited usage of the OpenAI GPT family at my job at Oracle. I also have been put
on an AI-specific project, so I'm able to invest a lot of time into this space lately. Personally, I have the
$20 OpenAI plan and the yearly ZAI Coding Plan subscription. I burn through the codex quota for the actual
hard work and planning. With the ZAI plan, I subscribed early and am a legacy plan member. This means I have
five-hour limits, but no weekly or monthly limits. The models are not SOTA by any means, and after using GPT 5.4
all day it can feel "dumb" at times, but for a lot of the things I do at home it is more than capable.
That split has worked really well for me. I use the best models where the extra capability matters and cheaper,
good-enough models where it doesn't.

Not to mention `glm-5.1` just launched and `glm-5-turbo` launched not long ago. I primarily use `glm-5-turbo` on
the openclaw instance I have running in my homelab. It's been a great project and having an AI agent with access
to my homelab has enabled some really cool things, like standing up new internal services without me manually
clicking around five different dashboards first.

## My Coding Setup

OpenAI seems to have a really good team behind Codex. The Codex App is really useful for quick chats, making edits to
tools I don't really care that much about and having an AI-enabled chat window in my knowledge base project. I've lived
in the terminal with a tmux + neovim setup, so the CLI agent tools have been a welcome addition to my workflow. Several
other engineers on my team have liked my setup, so I've given them my tmux and neovim configs. It's so cool to see a
screenshare of a team member and see my terminal configuration on their machine!

We are trying to build tooling for our entire organization, so features like [Plugins](https://developers.openai.com/codex/plugins)
have been really nice to get.

At home though, I mainly use pi. It's such a great agent and I've customized it the way I like it. I can easily
swap between my Codex or ZAI subscription, even mid-session, and it is _so much faster_ than any other harness I've used.
Being able to swap models, load skills and extensions dynamically, and shape the workflow around how _I_ want to work has made a huge difference.

## Changes to my homelab

I have created a repository, named `homelab`, that I allowed my agent to have some `ssh` access to my machines to build.
It documents all of my homelab: the hardware, the Proxmox servers, all the VMs and all the services running on them.
Then I started building [skills](https://agentskills.io/) into the project to have easy workflows and capabilities
documented.

For example, I have an [ubuntu vm template](https://community-scripts.org/scripts/ubuntu2504-vm) installed with my
default settings. I have a skill that instructs an agent how to quiz me and use this template to create a new VM. I've
built several skills like this and along with access to the Proxmox API, `ssh` access to the server and all of the
documentation in the repo itself, I almost never have to add missing context when interacting with the agent.

I also have, what I think is, a badass self-hosted service setup. The major components:

- [Docker Registry](https://hub.docker.com/_/registry) with [Docker Registry UI](https://github.com/joxit/docker-registry-ui)
- [Drone CI](https://www.drone.io/) server for CI
- [Coolify](https://coolify.io/) as my application runtime. Think homelab version of Heroku. It has a Cloudflare integration so I can publicly expose services if I want.
- [Nginx Proxy Manager](https://nginxproxymanager.com/) with a Cloudflare integration so I have SSL to internal domains. This has been amazing to have real SSL internally with no effort.
- [Plane](https://plane.so/self-hosted) for project management. Again, think homelab version of Jira.

With skills for each of these, agents can interact with them very easily. I can put information into a Plane work item
(Jira story) and have an agent work on it. I have built [agent-worker](https://github.com/TylerAngelier/agent-worker) so
agents can pick up tasks autonomously.

I can have an agent set up a new project with a pretty solid starting point:

- GitHub repository
- CI with Drone
- Containers in Docker Registry
- Deployment to Coolify
- Internal SSL through Nginx Proxy Manager or Coolify + Cloudflare for external sites

all dynamically loaded from skills as I talk with an agent.

The part that still feels wild to me is that this is actually useful, not just novel. It saves time, reduces the amount
of setup work I have to keep in my head and makes the homelab feel like a system I can operate instead of a pile of tools
I have to remember how to drive.
