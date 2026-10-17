---
title: "Open Weights Aren't Free: The Real Cost Is Operations"
date: 2026-02-25 09:00:00 +0000
author: "InnovationLet Editorial"
tags: [Models]
description: "Downloading the weights costs nothing. Running them well costs GPUs, on-call time, and a pile of infrastructure nobody quotes you. Here's the real math."
permalink: "/open-weights-arent-free/"
subtitle: "The weights are free. GPUs, on-call time and infrastructure are not."
keywords: "open weights, self-hosting, LLM inference, GPU costs, MLOps"
key_points:
  - "Serving a 70B model means multiple GPUs sized for peak, paid for around the clock."
  - "Inference infrastructure can consume a full-time role before any feature ships."
  - "Open weights usually win on price only at high, sustained, predictable volume."
  - "Price three months of real traffic fully loaded before committing to self-hosting."
---

A 70B open-weight model looks like free money the day you download it. Then you rent two H100s at about $3 an hour each, and the meter runs through the night while traffic sits at zero.

Licensing isn't the expense. Nobody is invoicing you for the weights. The expense is everything you have to build and operate around them.

## What self-hosting actually costs

First, hardware. Serving a 70B model at usable latency means multiple GPUs, a host machine, storage, and enough cooling to keep it happy. Idle time doesn't discount. You pay for capacity sized to your peak, not your average.

Then the people. Someone has to serve the model, upgrade drivers, patch vulnerabilities, and wake up when throughput drops. A small team can burn a full-time role on inference infrastructure alone.

Add the pieces that were invisible when you only used a hosted API:

- Quantization experiments and batching logic
- Autoscaling, rate limits, and a fallback path when a node dies
- Monitoring and tracing for every request
- A person on call, because the queue doesn't drain itself
- Eval and guardrail maintenance after each model change

Each item is a week of work on its own, and none of them ship features.

## The comparison teams get wrong

Open weights beat hosted APIs on price only at sustained, high-volume usage with a predictable shape. If your traffic is spiky, or you're still rewriting the prompt every two days, you'll pay for idle GPUs and redeploys either way.

There's also a quality cost. Hosted models ship with updates and safety filtering you don't maintain. With open weights, you own the eval suite, the guardrails, and every regression that slips past them.

## Do the math with your numbers

Take last month's request count. Multiply by tokens per request. Price that volume at the hosted rate you'd actually get. Then price the alternative: hardware or cloud instances, fully loaded with engineering time, divided across the same requests.

The break-even usually lands higher than teams expect. Plenty of people assume open weights will halve the bill, then find the crossover point at eight times their current volume, maybe more once idle capacity and on-call hours are counted.

Before you commit to self-hosting, price three months of your real traffic against your fully loaded ops cost, including the person who gets paged at 3 a.m. If the hosted API still wins at that volume, keep it and spend the engineering time on your product.
