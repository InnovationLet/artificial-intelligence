---
title: "Agents Need Boring Tools: Why Constrained Tool Use Beats Open Autonomy"
date: 2026-04-08 09:00:00 +0000
author: "InnovationLet Editorial"
tags: [Agents]
description: "Agent demos succeed because someone reruns them until they work. Production doesn't get free retries, and the fix is fewer tools, hard step limits, and boring paths."
---

An agent in a demo booked a flight in 40 seconds. In staging, the same agent failed one run in six, and half the failures came from it reaching for a tool that shouldn't have been on the table.

Demos are curated. The prompt is tuned, the network is fast, the target sites don't change their markup mid-run, and a person is ready to restart the loop. Production has none of that.

## Demos hide the retry loop

Most agent demos get run until they succeed, and only the successful run is recorded. The retries never make the cut. That's how a 40% success rate becomes a convincing video.

Most teams also demo on the happy path. They pick inputs close to ones the agent has seen before, run on a clean network, and skip the step where an API returns a slightly different JSON shape than last week. Production throws those variations at you hourly.

Real traffic punishes sloppiness harder. An agent with twelve tools spends its budget deciding among them, and each extra option is another way to choose wrong. Errors compound, since one bad call feeds a bad result into the next step.

## Fewer tools, better behavior

Give the agent three tools with narrow, typed inputs instead of fifteen with free-form arguments. It'll pick the right one more often, and when it doesn't, the failure is obvious in the logs.

Typed arguments also make retries cheaper. When the model gets a validation error instead of a silent wrong action, it can correct itself in one step instead of wandering for five.

Cap the loop too. Five steps, one retry, then hand it to a person. A bounded failure costs an afternoon; an unbounded one costs a customer.

Keep deterministic paths for the steps that don't need judgment. Filling a known form from known fields doesn't require the model deciding its own sequence. Save the reasoning for the parts with real ambiguity.

## Ship the boring version first

Start with one task, a fixed tool set, and a clear escalation rule. Measure unassisted success on real inputs for a week before you touch anything. Add a tool only when the current set demonstrably can't finish the job.

Cut your agent's tool list to the three it actually needs, cap the loop at five steps, and track unassisted success rate on real traffic for a week. Only then add anything new.
