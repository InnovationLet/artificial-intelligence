---
title: "How Chinese AI Labs Use Distillation Attacks on US LLMs"
seo_title: "Chinese AI Distillation Attacks | InnovationLet"
date: 2026-11-02 09:00:00 +0000
updated: 2026-11-03 16:17:31 +0000
author: "InnovationLet Editorial"
tags: [Cybersecurity, Policy]
categories: [Artificial Intelligence, Cybersecurity]
description: "Anthropic, OpenAI and US agencies say Chinese labs copy frontier AI via distillation. Here is how it works, what is alleged and what China says."
permalink: "/chinese-labs-distillation-attacks-ai/"
subtitle: "A standard training technique, a global fight over permission, and a paper trail that now runs to the FBI."
keywords: "AI distillation, Chinese AI labs, DeepSeek, Anthropic, Claude, model extraction, AI policy"
key_points:
  - "Anthropic's February report named DeepSeek, Moonshot AI and MiniMax, and counted more than 16 million Claude exchanges through about 24,000 fraudulent accounts."
  - "Its September update added Alibaba-affiliated operators, Zhipu, Xiaomi and SenseTime, with nearly 200 million exchanges across the campaigns it described."
  - "The NSA, CISA and the FBI released a joint advisory on September 8 describing industrial-scale extraction. Beijing rejected it the next day."
  - "The alleged playbook uses proxy accounts, stolen API keys, chain-of-thought extraction and rerouted customer traffic."
  - "US labs are summarizing reasoning traces and tightening identity checks. Businesses should guard API keys and avoid cheap resellers."
image:
  path: "/assets/images/chinese-ai-distillation.jpg"
  width: 1600
  height: 900
  alt: "Illustration of a central AI model sending data through proxy account nodes to smaller student models."
---

Anthropic, OpenAI and three US security agencies now say several China-based AI labs have been pulling capabilities out of American frontier models and using the answers to train their own. The practice is called AI distillation. The fight is over who gave permission.

The named labs have not publicly detailed their side in the coverage reviewed for this article. Beijing has, through the Commerce Ministry and the foreign ministry. And the argument has moved from company blogs to Congress, the White House and a joint advisory from the NSA, CISA and the FBI.

One transparency note before the details: most of the technical reporting comes from the US companies whose models were targeted, plus US government bodies. Those are interested parties, and every claim below should be read as an allegation unless stated otherwise. Our [editorial standards]({{ '/editorial-standards/' | relative_url }}) explain how we attribute claims like these.

<figure class="post-figure">
  <img src="{{ '/assets/images/chinese-ai-distillation.jpg' | relative_url }}" width="1600" height="900" alt="Illustration of a central AI model sending data through proxy account nodes to smaller student models." decoding="async">
  <figcaption>An illustration of the alleged flow: a frontier model, proxy accounts, and smaller student models. Image: InnovationLet / F9XR.</figcaption>
</figure>

## What distillation is

Knowledge distillation is a standard machine-learning method. A large, expensive teacher model produces answers, and a smaller student model learns to imitate them. The student ends up faster and cheaper, with much of the teacher's skill. AI companies do this internally all the time, and explainers from the UK government and IBM describe it as routine.

An attack, in the current usage, means doing that to a model you don't own. The alleged conduct includes fake accounts, stolen API keys and relay services, all to harvest outputs at scale in violation of access terms. Anthropic says the targets are the abilities that separate a frontier model from a commodity one: agentic reasoning, tool use and coding.

The technique is the same, but permission is what changed.

## The alleged playbook

The reports from Anthropic, OpenAI, Google's threat intelligence group and US agencies describe a fairly consistent set of tactics.

### Proxy accounts and relay services

Claude, GPT and Gemini are not sold in China, so access has to be routed around geography. According to the September advisory from the NSA, CISA and the FBI, Chinese labs use native APIs, cloud providers, aggregators and gray-market "transfer stations" to get in. Some of those services have been advertised on Chinese marketplaces such as Taobao and Xianyu.

Anthropic's February report described "hydra cluster" networks: thousands of accounts spreading traffic so no single login looks unusual. One proxy network ran more than 20,000 fraudulent accounts at once, mixing distillation traffic with ordinary customer requests.

### Chain-of-thought extraction

The most useful target is the model's working, because chain-of-thought traces show the steps a model takes before it answers. Train a student on those traces and you teach it how to work through a problem, which is harder to copy from public web text.

Anthropic says several campaigns aimed directly at reasoning transcripts. Its September report described one operation tied to Alibaba-affiliated accounts that used a fixed prompt to pull chain-of-thought data from Claude Opus 4.6 and 4.7.

### Rerouted customer traffic

Some labs took a more direct route. Anthropic says DeepSeek and Moonshot sent customer requests to Claude, showed Claude's answer as if their own model had produced it, and kept some of the exchanges for training. Moonshot routed nearly 300,000 requests through 5,380 accounts in 10 days, mostly from Singapore and Japan, according to the report.

Anthropic said some of that traffic included sensitive information from individuals, multinational companies and state-affiliated actors.

### A market for harvested transcripts

Not every lab needs to run its own extraction, since proxy operators can log conversations and sell them. Anthropic says SenseTime bought Claude transcripts from third-party vendors. That creates a secondary market for model output that never touches the original API.

### Fast pivots and quality checks

When Anthropic released a new Claude model during MiniMax's campaign, MiniMax moved nearly half its traffic to the new system within 24 hours. The US advisory describes automated failover between access paths when one gets blocked, plus quality checks designed to spot defensive changes.

## The paper trail

The dispute escalated in a hurry. This is the sequence of public events.

| Date (2026) | What happened |
|---|---|
| February 12 | OpenAI sends a memo to the House Select Committee on China accusing DeepSeek of distillation through obfuscated routers and programmatic access. |
| February 23 | Anthropic names DeepSeek, Moonshot AI and MiniMax, citing more than 16 million exchanges through about 24,000 fraudulent accounts. |
| April 15 | The Deterring American AI Model Theft Act is introduced in the House. |
| April 16 | The House Select Committee on China holds a hearing titled "China's Campaign to Steal America's AI Edge." |
| April 22 | The House Foreign Affairs Committee advances the model-theft bill 43-0. |
| April 23 | The White House Office of Science and Technology Policy, led by Michael Kratsios, issues a memo on industrial-scale distillation. |
| September 8 | The NSA, CISA and the FBI publish a joint advisory. Google's threat intelligence group publishes its own findings the same day. |
| September 9 | China's Commerce Ministry rejects the US advisory and warns of countermeasures. |
| September 10 | Anthropic publishes a threat intelligence report naming seven China-based labs and describing campaigns totaling nearly 200 million exchanges. |

## Who is accused, and of what

The table below summarizes what each source has alleged. None of these are court findings, and the named companies have not had a chance to cross-examine the evidence.

| Lab | What the reporting alleges | Source |
|---|---|---|
| DeepSeek | OpenAI says staff used obfuscated routers and custom code to pull outputs from US models. Anthropic says a July campaign moved more than 12.1 million exchanges over 14 days by relaying customer requests and extracting reasoning traces. | OpenAI memo; Anthropic |
| Moonshot AI | More than 3.4 million exchanges in the February report. A later campaign of about 23 million exchanges from May to July, including nearly 300,000 customer requests routed through 5,380 fraudulent accounts over 10 days. | Anthropic |
| MiniMax | More than 13 million exchanges aimed at agentic coding and tool use. Later, a proxy service built through a shell company. | Anthropic |
| Alibaba-affiliated operators | 151 million exchanges between May and July, peaking near 3 million a day from more than 3,500 accounts and targeting reasoning transcripts. Anthropic called it the largest campaign it has measured. | Anthropic |
| Zhipu (Z.ai) | More than 3.4 million exchanges over 17 days in June and July, using 273 accounts to extract reasoning traces. | Anthropic |
| Xiaomi | More than 400,000 exchanges over 20 days in March and April, replaying conversations from its own models through Claude. | Anthropic |
| SenseTime | Purchasing Claude user transcripts from third-party data vendors. | Anthropic |
| StepFun | Distilling Claude and GPT models between late 2025 and early 2026. | NSA, CISA and FBI advisory |

The US advisory names DeepSeek, Moonshot AI, Alibaba, MiniMax, StepFun and Z.AI. It says the campaigns have targeted models from Anthropic, OpenAI, Google and xAI since at least late 2024, and that the activity likely happened with Chinese government awareness. That attribution is the agencies' assessment, and Beijing rejects it.

## Why labs would do it

US officials and companies frame this as an economics problem. The September advisory says labs that distill at industrial scale see shorter development timelines and lower spending when training frontier models. Anthropic uses the same argument to back export controls: if extraction at this scale needs advanced chips, then limiting chip access limits both direct training and the size of a distillation run.

Critics of that framing, including Beijing, say it discounts Chinese research and engineering.

## What China says

Beijing has answered through the Commerce Ministry and the foreign ministry, not through the named companies. On September 9, the Commerce Ministry called the US allegations groundless and legally unsound. It said distillation is a neutral technique used by companies worldwide, including American ones, and accused Washington of double standards and "technological hegemony."

The ministry also warned of "resolute countermeasures" if the US acts against Chinese AI firms. It said the two governments had agreed to an intergovernmental AI dialogue.

No detailed public rebuttal from DeepSeek, Moonshot AI, MiniMax or the other named labs appeared in the coverage reviewed for this article. Reuters, CNBC and CNN reported at the time of the February and September disclosures that the companies did not respond to requests for comment.

## The hard questions

### Is this hypocritical?

Some critics say frontier labs trained their own models on huge amounts of public internet data and have no standing to complain when someone learns from their outputs. The labs answer that scraping public pages is different from running a paid API through fraudulent accounts to copy safety-restricted reasoning. The law has not settled that distinction.

### Is it illegal?

Most of the conduct described is a terms-of-service and access-control dispute. Whether it is illegal is a separate question.

The Deterring American AI Model Theft Act would create a process to identify foreign entities that extract key features of closed-source US models and allow sanctions. It passed the House Foreign Affairs Committee 43-0 in April and has not become law.

US agencies call the activity a national security threat. That is a policy judgment from an agency, and no court has ruled on it.

### How strong is the evidence?

Anthropic says it attributes campaigns through IP addresses, request metadata, infrastructure and, in some cases, corroboration from other companies. It shared indicators with other labs and authorities. Outsiders cannot audit those indicators, which is why the government advisory matters and why Beijing disputes it.

Google's threat intelligence group separately said it had found distillation campaigns exceeding 100 million prompts against its models, including attempts on visual, audio and video capabilities. Google did not name the operators in its public post.

## How the labs are fighting back

Anthropic's countermeasures include banning reseller accounts and accounts from unsupported regions when identity checks fail. It now summarizes its internal reasoning before responding, so a stolen transcript is less useful. It also restricts new API accounts from editing the context before encrypted reasoning in multi-turn conversations, a trick attackers use to coax reasoning out of the model.

The US advisory recommends three things: detect anomalous prompts and account behavior, subtly alter responses to suspected extraction, and share indicators across model providers, cloud platforms and aggregators.

Google says it has deployed real-time defenses that degrade the performance of unauthorized student models and tools that identify Gemini-distilled models.

## What this means for developers and businesses

Even if you never train a frontier model, the alleged tactics touch ordinary customers.

- Guard API keys. Anthropic says stolen keys from legitimate companies and individuals were used in these campaigns. A leaked key can fund someone else's training run, and you may get the bill.
- Treat cheap resellers as a data risk. Proxy services that sell discounted or restricted-region access may log and resell conversations. Anything sensitive you paste into them can end up in a training set.
- Watch usage spikes. Sudden jumps in tokens, odd geographies or overnight traffic can signal that your credentials are being used.
- Expect more identity checks. Providers are tightening verification and regional rules, which may slow onboarding for legitimate developers.
- Ask about provenance. If you adopt a model, ask how it was trained. Treat unresolved allegations as a procurement risk and ask your supplier for answers.

## What to watch

Four things: whether the Deterring American AI Model Theft Act becomes law, whether more labs publish findings, whether Beijing follows through on countermeasures, and whether summarized reasoning slows extraction without hurting legitimate users. The last one is testable: if customers see reasoning quality drop, the defense will be hard to keep.

More coverage sits in the [InnovationLet AI archive]({{ '/archive.html' | relative_url }}), including our reporting on [how the EU AI Act's enforcement powers went live]({{ '/eu-ai-act-enforcement-goes-live/' | relative_url }}).

## Key takeaways

<ul class="key-takeaways">
  <li><strong>The method is routine.</strong> Knowledge distillation is a standard way to build smaller models. The alleged abuse is doing it to a competitor's model without permission.</li>
  <li><strong>The scale is the allegation.</strong> Anthropic counted more than 16 million exchanges in February and nearly 200 million across the campaigns in its September report.</li>
  <li><strong>Washington has joined the fight.</strong> A House bill, a White House memo and a joint NSA, CISA and FBI advisory have turned a corporate complaint into national policy.</li>
  <li><strong>Beijing rejects the premise.</strong> China calls distillation normal, the US accusations groundless and has warned of countermeasures.</li>
  <li><strong>The defenses have a cost.</strong> Summarized reasoning, identity checks and regional bans may frustrate attackers and legitimate customers at the same time.</li>
</ul>

## Frequently asked questions

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">What is a distillation attack in AI?</h3></summary>
  <div class="faq__a"><p>A distillation attack is the unauthorized use of a rival model's outputs to train another model. The attacker sends large volumes of prompts to a leading model, often through fake accounts or relay services, then trains its own model on the answers.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">Is AI distillation illegal?</h3></summary>
  <div class="faq__a"><p>Distillation is a standard, legitimate technique used inside AI companies. The accusations concern doing it to someone else's model in violation of terms of service and access restrictions. Whether specific conduct is illegal is a matter for courts and lawmakers, and the allegations reported so far have not been adjudicated.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">Which Chinese AI labs have been accused of distillation attacks?</h3></summary>
  <div class="faq__a"><p>Anthropic has named DeepSeek, Moonshot AI, MiniMax, Alibaba-affiliated operators, Zhipu (Z.ai), Xiaomi and SenseTime. OpenAI has accused DeepSeek, and a joint US advisory also names StepFun. These are allegations, and the Chinese government rejects them.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">How many exchanges did Anthropic say were involved in the distillation attacks?</h3></summary>
  <div class="faq__a"><p>In February 2026, Anthropic reported more than 16 million exchanges through about 24,000 fraudulent accounts across three labs. Its September 2026 update described one campaign of 151 million exchanges attributed to Alibaba-affiliated operators and nearly 200 million exchanges across the campaigns it described.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">What has China said about the distillation accusations?</h3></summary>
  <div class="faq__a"><p>Chinese officials call the accusations groundless, say distillation is a widely used practice, and accuse the United States of double standards. They have warned of resolute countermeasures if Washington suppresses Chinese AI companies on this basis.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">How can AI companies stop distillation attacks?</h3></summary>
  <div class="faq__a"><p>Reported measures include identity verification, banning resellers and unsupported regions, summarizing reasoning instead of exposing full traces, altering responses to suspected extraction, and sharing indicators across AI providers and cloud platforms.</p></div>
</details>

<details class="faq">
  <summary class="faq__summary"><h3 class="faq__q">Can distillation attacks affect regular businesses and AI users?</h3></summary>
  <div class="faq__a"><p>Yes. Stolen API keys and unofficial reseller services can expose private prompts and data. Businesses should secure credentials, monitor usage for unusual spikes and avoid untrusted access providers.</p></div>
</details>

## Sources and notes

Primary sources:

- Anthropic, ["Detecting and preventing distillation attacks"](https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks), February 23, 2026.
- Anthropic, ["Detecting and countering misuse of AI: September 2026"](https://www.anthropic.com/threat-intelligence-report-september-2026), September 10, 2026.
- NSA, CISA and FBI, ["China-Based Artificial Intelligence Companies Conducting Industrial-Scale Distillation Campaigns Against U.S. AI Companies"](https://www.cisa.gov/news-events/cybersecurity-advisories/aa26-251a), September 8, 2026.
- OpenAI, [memo to the House Select Committee on China](https://cdn.openai.com/pdf/045aa967-ee96-4a09-94ee-3098ddf6db2c/OpenAI-US-House-Select-Cmte-Update-%5B021226%5D.pdf), February 12, 2026.
- White House OSTP, NSTM-4, ["Adversarial Distillation of American AI Models"](https://whitehouse.gov/wp-content/uploads/2026/04/NSTM-4.pdf), April 23, 2026.
- China Ministry of Commerce, [spokesperson remarks](https://english.mofcom.gov.cn/News/SpokesmansRemarks/art/2026/art_9b97b0c7213742c9946830e5aa6c923d.html), September 9, 2026.
- Google Cloud Threat Intelligence, ["From Prompting to Autonomy"](https://cloud.google.com/blog/topics/threat-intelligence/from-prompting-to-autonomy-the-evolution-of-adversarial-ai), September 8, 2026.
- Congress.gov, [H.R. 8283, the Deterring American AI Model Theft Act of 2026](https://www.congress.gov/bill/119th-congress/house-bill/8283/all-info).
- House Select Committee on China, [hearing on "China's Campaign to Steal America's AI Edge"](https://docs.house.gov/Committee/Calendar/ByEvent.aspx?EventID=119165), April 16, 2026.

Secondary reporting:

- Reuters, ["Anthropic disrupts Russian, Chinese AI campaigns targeting its Claude models"](https://www.reuters.com/legal/litigation/anthropic-disrupts-russian-chinese-ai-campaigns-targeting-its-claude-models-2026-09-10/), September 10, 2026.
- CNBC, ["Chinese AI labs secretly used millions of Claude exchanges to train their models"](https://www.cnbc.com/2026/09/11/chinese-ai-labs-moonshot-deepseek-alibaba-anthropic.html), September 11, 2026.
- TechCrunch, ["Anthropic details distillation campaigns from Alibaba, Moonshot AI, and DeepSeek"](https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/), September 10, 2026.
- The Hacker News, ["Anthropic Says Seven China-Based AI Labs Ran Industrial-Scale Claude Distillation Attacks"](https://thehackernews.com/2026/09/anthropic-says-seven-china-based-ai.html), September 11, 2026.
- AP, ["China rejects US accusations that its AI developers rely on American AI models"](https://apnews.com/article/us-china-ai-models-anthropic-trump-0f6ca61301630134607551b1dab0d632), September 9, 2026.
- Reuters, ["Chinese AI companies 'distilled' Claude to improve own models, Anthropic says"](https://www.reuters.com/world/china/chinese-companies-used-claude-improve-own-models-anthropic-says-2026-02-23/), February 23, 2026.
- CNBC, ["Anthropic accuses DeepSeek, Moonshot and MiniMax of distillation attacks on Claude"](https://www.cnbc.com/2026/02/24/anthropic-openai-china-firms-distillation-deepseek.html), February 24, 2026.
- BBC, ["White House memo claims mass AI theft by Chinese firms"](https://www.bbc.com/news/articles/cpqxgxx9nrqo), April 23, 2026.

*Disclosure: this article is based on public reporting and company or government statements available as of November 2, 2026. Allegations are attributed to their sources and have not been adjudicated.*

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is a distillation attack in AI?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "A distillation attack is the unauthorized use of a rival model's outputs to train another model. The attacker sends large volumes of prompts to a leading model, often through fake accounts or relay services, then trains its own model on the answers."
      }
    },
    {
      "@type": "Question",
      "name": "Is AI distillation illegal?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Distillation is a standard, legitimate technique used inside AI companies. The accusations concern doing it to someone else's model in violation of terms of service and access restrictions. Whether specific conduct is illegal is a matter for courts and lawmakers, and the allegations reported so far have not been adjudicated."
      }
    },
    {
      "@type": "Question",
      "name": "Which Chinese AI labs have been accused of distillation attacks?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Anthropic has named DeepSeek, Moonshot AI, MiniMax, Alibaba-affiliated operators, Zhipu (Z.ai), Xiaomi and SenseTime. OpenAI has accused DeepSeek, and a joint US advisory also names StepFun. These are allegations, and the Chinese government rejects them."
      }
    },
    {
      "@type": "Question",
      "name": "How many exchanges did Anthropic say were involved in the distillation attacks?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "In February 2026, Anthropic reported more than 16 million exchanges through about 24,000 fraudulent accounts across three labs. Its September 2026 update described one campaign of 151 million exchanges attributed to Alibaba-affiliated operators and nearly 200 million exchanges across the campaigns it described."
      }
    },
    {
      "@type": "Question",
      "name": "What has China said about the distillation accusations?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Chinese officials call the accusations groundless, say distillation is a widely used practice, and accuse the United States of double standards. They have warned of resolute countermeasures if Washington suppresses Chinese AI companies on this basis."
      }
    },
    {
      "@type": "Question",
      "name": "How can AI companies stop distillation attacks?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Reported measures include identity verification, banning resellers and unsupported regions, summarizing reasoning instead of exposing full traces, altering responses to suspected extraction, and sharing indicators across AI providers and cloud platforms."
      }
    },
    {
      "@type": "Question",
      "name": "Can distillation attacks affect regular businesses and AI users?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. Stolen API keys and unofficial reseller services can expose private prompts and data. Businesses should secure credentials, monitor usage for unusual spikes and avoid untrusted access providers."
      }
    }
  ]
}
</script>
