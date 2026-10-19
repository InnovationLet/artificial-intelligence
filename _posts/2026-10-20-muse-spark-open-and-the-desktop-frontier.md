---
title: "Muse Spark Open Puts a Frontier Model on Two Desktops"
date: 2026-10-20 09:00:00 +0000
author: "InnovationLet Editorial"
tags: [Models]
description: "Meta's 816B-parameter Muse Spark Open runs on two M5 Ultra Mac Studios, and October's open-weight wave makes local frontier inference a deployment choice, not a demo."
permalink: "/muse-spark-open-and-the-desktop-frontier/"
subtitle: "An 816B open-weight model on two workstations is a packaging win, but the ops bill still follows you home."
keywords: "Muse Spark Open, open weights, local inference, Meta, mixture of experts, Nemotron 3.5"
key_points:
  - "Meta released Muse Spark Open, an 816B-parameter model with 42B active, under a limited-commercial license."
  - "It runs locally on two Apple M5 Ultra Mac Studios with a combined terabyte of unified memory."
  - "NVIDIA's Nemotron 3.5 and Mistral's Large 4 shipped in the same two-week window, widening the open field."
  - "Fast local tokens still don't remove the eval, guardrail and on-call work that hosted APIs absorb."
---

Meta published the weights for Muse Spark Open on October 15, an 816B-parameter mixture-of-experts model with 42B parameters active per token and a one-million-token context window. The headline isn't the size. It's that Meta demonstrated it doing real agent work on two Apple M5 Ultra Mac Studios sitting on a desk.

That is a shift in what "open weights" means. A year ago a model in this class was a data-center asset. Now the sales pitch is a workstation.

## The desktop claim, unpacked

The local claim leans on Apple's unified memory. Each M5 Ultra Mac Studio carries up to 512 GB, so two machines hold the whole model across a combined terabyte, and the chip's 1.2 TB/s of memory bandwidth is fast enough to feed each token the small slice it needs. Two desktops behave like one box.

Meta ran the demo on-device through Muse Code, shipping iOS changes to an open-source Mastodon client and driving DaVinci Resolve end to end. Those are agent workflows, not chat transcripts, which is the part worth watching.

The license is a caveat. Muse Spark Open ships under Meta's Muse Model License with limited commercial terms, not an OSI-approved one, so read the terms before you build a product on it.

## October's open-weight wave is the real story

Muse Spark Open landed in the middle of a dense release window. NVIDIA shipped Nemotron 3.5 Super VL, a 120B-parameter open multimodal model with 12B active, pitched at customized agents that need vision. Mistral released Large 4, a trillion-parameter model with 49B active. Reflection AI published Beam 1.0. Liquid AI, JetBrains, Cloudflare and others filled in the smaller end.

That density matters more than any single release. When a competently sized open model shows up every few days, the hosted-API default weakens. Teams can now pick a local model for latency-sensitive or data-resident work and keep a hosted frontier model for the hard tail.

## What local doesn't buy you

Fast local tokens are not a free lunch. The infrastructure costs we wrote about earlier this year don't disappear when the hardware moves under your desk — they change shape. You still own the eval suite, the guardrails, the versioning, and the person who gets paged when throughput drops.

The honest test is narrow. Pick one task you currently send to a hosted API, run it locally on Muse Spark Open or an October open model for a week, and measure unassisted success and dollars per task. If the local model clears your bar, move that task. If it doesn't, the weights were never the point.
