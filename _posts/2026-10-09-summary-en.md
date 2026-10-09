---
layout: default
title: "Horizon Summary: 2026-10-09 (EN)"
date: 2026-10-09
lang: en
---

> From 40 items, 8 important content pieces were selected

---

**Technology News**
1. [ThinkingBox benchmark repeats 507 stateful agent workflows 20x, grades final database state](#item-tech-news-1) ⭐️ 7.0/10
2. [OpenAI bans Russian, Iranian influence campaigns using ChatGPT](#item-tech-news-2) ⭐️ 7.0/10
3. [Anthropic updates Claude usage policy to ban abuse and high-risk uses](#item-tech-news-3) ⭐️ 7.0/10
4. [Anthropic launches OSS Scanner for open-source vulnerability scanning](#item-tech-news-4) ⭐️ 7.0/10

**Financial News**
1. [Premarket Movers: Broadcom AI-Chip Financing, Wolfspeed Defense Loan, TSMC Revenue](#item-finance-news-1) ⭐️ 7.0/10
2. [S&amp;P Sees China Property Prices Bottoming in 2028 as Big Cities Recover Sooner](#item-finance-news-2) ⭐️ 7.0/10
3. [US Government Suspends Microsoft From Green Card Sponsorship Program Over Fraud Allegation](#item-finance-news-3) ⭐️ 7.0/10
4. [SpaceX to Acquire Nationwide Low-Band Spectrum Licenses](#item-finance-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [ThinkingBox benchmark repeats 507 stateful agent workflows 20x, grades final database state](https://www.reddit.com/r/MachineLearning/comments/1x17shf/thinkingbox_solving_an_agent_task_once_vs_solving/) ⭐️ 7.0/10

Microsoft researchers released ThinkingBox-Bench, a benchmark of 507 policy-conditioned business workflows spanning retail, travel/hospitality, auto insurance, neobank internal IT, and consulting IT/HR that runs each task in 20 independent attempts from an identical clean backend \(10,140 trials per model\) and grades success by the terminal backend state and side effects rather than by whether the agent finished; the paper, code, and dataset are public and the environment is on Hugging Face OpenEnv, though raw evaluation trajectories are not released. 477 of the 507 tasks are graded on state alone and 30 additionally check a narrow property of the final response, and the benchmark reports pass@1, pass@20, and all-20, with the authors stressing that all-20 is an observed count on a fixed trial budget, not an estimator. Discovery and repeatability rank models differently: Kimi-K3 solved 93.89% of tasks at least once \(476/507\) but only 13.41% \(68/507\) on all 20 attempts, Claude Opus 5 discovered fewer \(79.09%\) yet repeated far more \(47.53%, 241 tasks\), and Qwen3.8-27B reached 89.35% at least once and 7.50% on every attempt. In a retrospective ablation over 121,680 valid trials across 12 models, 79,853 failed the executable checks, yet 67.24% of those failures terminated cleanly with a state-changing tool call and no final tool error — among them wrong field values in 77.61%, unintended extra effects in 43.30%, and missing required effects in 25.36% \(categories overlap\) — and the authors note the tasks are synthetic reconstructions rather than production traffic and that 20/20 is not a guarantee of future reliability.

reddit · r/MachineLearning · /u/tuhin\_k · Oct 9, 00:50

**「Background」** ThinkingBox&\#x27;s repository states that the framework began as a private project used by developers and scientists working on agentic reinforcement learning for Microsoft Copilot Studio before it became open source, and Microsoft&\#x27;s write-up describes the design as separating the execution harness from the benchmark package so each can be updated independently. The accompanying paper presents it as a sandbox for tool–agent–user interaction that provides isolated MCP-compatible tool sessions, complete execution traces, and outcome evaluation over terminal backend state, which is the machinery that makes repeated-attempt grading against a final backend state possible.

**「What this means for agent evaluation」** For teams that currently treat &quot;the agent finished the task&quot; as success, the paper&\#x27;s ablation is the actionable finding: across 121,680 valid trials, 79,853 failed the executable checks, yet 67.24% of those failures still terminated cleanly, invoked a state-changing tool, and ended without a final tool error — a completion-style proxy would have scored them as done, whereas grading on terminal backend state catches them. Because the 507 tasks, code, dataset, and an OpenEnv environment are published, developers can run the benchmark against their own models instead of relying on the reported numbers, though the authors stress that a 20/20 result is an observed count on a fixed trial budget, not a guarantee of future reliability.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/microsoft/thinkingbox">GitHub - microsoft/ thinkingbox : thinkingbox is a framework for...</a></li>
<li><a href="https://arxiv.org/abs/2608.19741">[2608.19741] One Success Isn&#x27;t Reliability: Thinkingbox , a...</a></li>
<li><a href="https://commandline.microsoft.com/thinkingbox-bench-agent-benchmarking/">ThinkingBox : Measuring whether agents finish the job</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#benchmarking`, `#LLM evaluation`, `#stateful workflows`, `#reproducibility`

---

<a id="item-tech-news-2"></a>
### [OpenAI bans Russian, Iranian influence campaigns using ChatGPT](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) ⭐️ 7.0/10

OpenAI said it banned two covert influence operations that used ChatGPT: a Russian campaign that allegedly took control of a Latin American &quot;research platform&quot; through impersonated identities and spread content damaging Ukraine&\#x27;s reputation and affecting local politics, and an Iranian operation that posed as seven &quot;journalist&quot; personas, pitched articles to small and mid-sized outlets worldwide, and mass-generated social media comments. OpenAI rated the Russian operation at Category 5 on its Breakout Scale — the first time it has reported an operation at that level — and the Iranian one at Category 4, noting it produced nearly 100 signed articles. The company said both campaigns combined conventional tradecraft with AI, and that some of the content reached mainstream media. These are OpenAI&\#x27;s own assessments of operations it disrupted, not independently verified findings.

telegram · zaihuapd · Oct 8, 15:52

**「Background」** OpenAI’s false-front report is part of its periodic disclosure of influence campaigns removed from ChatGPT, and the company rates such operations using a Breakout Scale category. According to the report and coverage of it, the Russian operation is the first Category 5 operation OpenAI says it has disrupted since it began reporting.

**「Impact」** For media outlets that received the Iranian network&\#x27;s unsolicited contributions, the ban on the underlying ChatGPT accounts does not undo the nearly 100 signed articles already produced, some of which reached mainstream outlets, leaving publishers to verify contributor identities and screen submissions themselves. The Russian campaign&\#x27;s rating as a Breakout Scale Category 5 operation also means OpenAI&\#x27;s own disclosure framework now treats such state-linked activity as having reached the scale where platform enforcement alone is insufficient.

<details><summary>References</summary>
<ul>
<li><a href="https://cellcog.ai/blog/openai-false-front-operations/">OpenAI &#x27;s False-Front Report: Its First Category 5 Takedown | CellCog</a></li>
<li><a href="https://openai.com/index/disrupting-ai-enabled-false-front-operations/">Disrupting AI-enabled “false front” operations | OpenAI</a></li>

</ul>
</details>

**Tags**: `#AI safety`, `#influence operations`, `#disinformation`, `#OpenAI`, `#geopolitics`

---

<a id="item-tech-news-3"></a>
### [Anthropic updates Claude usage policy to ban abuse and high-risk uses](https://www.theverge.com/ai-artificial-intelligence/1008100/anthropic-new-usage-policy-abuse-claude) ⭐️ 7.0/10

Anthropic updated its usage policy for Claude for the first time in more than a year, adding explicit bans on persistent and unnecessary abuse of the model along with high-risk uses including election interference, weapons development, surveillance, and certain health and financial applications. The new rules also prohibit deceptive political messaging, amplifying content through fake accounts, and deceiving voters. Anthropic says terminating a conversation remains its main enforcement mechanism, applied only in extreme cases of repeated abuse. The weapons prohibition now extends to software and hardware that operates weapons as well as armed drones.

telegram · zaihuapd · Oct 9, 01:34

**「Background」** Anthropic&\#x27;s previous usage policy refresh came more than a year before this update; the company said that in the intervening period Claude had taken on &quot;longer, more independent work.&quot; Anthropic also described most of the new rules as clarifications of existing policy, stating that the weapons and surveillance provisions reflect how it was already enforcing the policy, according to FourWeekMBA&\#x27;s account of the 2026 update.

**「What changes for developers」** Developers working on guidance or control software for weapons—including armed drones—now fall explicitly inside Claude&\#x27;s prohibited-use list, so such projects can no longer be routed through the API without risking enforcement. Anthropic&\#x27;s stated enforcement mechanism remains terminating conversations, which the source describes as reserved for extreme cases of repeated abuse, meaning the practical effect is a policy and account-level risk rather than a technical block.

<details><summary>References</summary>
<ul>
<li><a href="https://fourweekmba.com/ai-anthropic-rewrites-usage-policy-adds-physical-action-rules/">Anthropic Rewrites Usage Policy , Adds... - FourWeekMBA</a></li>
<li><a href="https://www.anthropic.com/news/2026-usage-policy-update">2026 Usage Policy update \ Anthropic</a></li>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/1008100/anthropic-new-usage-policy-abuse-claude">Anthropic bans ‘abusive or cruel behavior’ toward Claude | The Verge</a></li>

</ul>
</details>

**Tags**: `#AI policy`, `#Anthropic`, `#Claude`, `#AI safety`, `#content moderation`

---

<a id="item-tech-news-4"></a>
### [Anthropic launches OSS Scanner for open-source vulnerability scanning](https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source) ⭐️ 7.0/10

Anthropic launched OSS Scanner, a free, opt-in vulnerability scanning service for eligible open-source projects, with reports generated by models such as Claude. Anthropic says the reports are not reviewed by humans and include vulnerability reproduction steps, explanations of the issues, and suggested patches where possible, and that they may contain errors. The company claims that over the past six months it surfaced more than 29,000 candidate vulnerabilities, of which about 6,000 were manually reviewed; among 97 high- or critical-severity issues from early testing, 85 met its disclosure-process requirements. Core maintainers of eligible projects can apply by submitting a GitHub pull request.

telegram · zaihuapd · Oct 9, 02:00

**「Background」** Anthropic says OSS Scanner is an outgrowth of its earlier Project Glasswing work, in which it used Claude to search for vulnerabilities rather than only to assist with writing code \(tool-2-1\). The same launch material frames the service as the next step for that pipeline, extending AI-generated vulnerability reports beyond Anthropic&\#x27;s own triage effort to outside open-source maintainers who opt in.

**「What it means for maintainers」** For eligible open-source maintainers, the practical consequence of opting in is that they must triage unreviewed, model-generated reports themselves: Anthropic states the reports — reproduction steps, explanations, and possible patches — are produced by Claude and similar models without human review and may contain errors. Because opt-in is requested through a GitHub pull request from a project&\#x27;s core maintainers, validating each candidate vulnerability and any proposed fix falls on the project&\#x27;s own review process rather than on Anthropic.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source">An opt-in vulnerability - finding service for open - source software</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#vulnerability scanning`, `#open source`, `#Anthropic`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Premarket Movers: Broadcom AI-Chip Financing, Wolfspeed Defense Loan, TSMC Revenue](https://www.cnbc.com/2026/10/08/stocks-making-the-biggest-moves-premarket-hae-avgo-lulu-wolf.html) ⭐️ 7.0/10

Broadcom is working to arrange more than $50 billion in financing tied to the custom AI chips it is developing with OpenAI, according to a Wall Street Journal report, and Wolfspeed secured a conditional $1.5 billion loan from the Defense Department. Taiwan Semiconductor Manufacturing reported September revenue growth of 54.6% year over year, pushing its third-quarter revenue to $16.03 billion and above expectations, while Applied Digital&\#x27;s fiscal first-quarter revenue rose 322% year over year to nearly $342 million.

rss · CNBC Finance · Oct 8, 12:28

**「Background」** Demand for AI chips has been boosting revenue at semiconductor companies, including TSMC, the world&\#x27;s largest contract chipmaker, which manufactures chips designed by other firms.

**「Impact」** Wolfspeed&\#x27;s existing shareholders could face dilution of up to 7.5% if the Pentagon exercises the warrants included in the proposed loan terms.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/10/08/tsmc-september-sales-hit-another-record-as-ai-boom-rolls-on.html">TSMC ’s September sales surge year - over - year as AI drives chip...</a></li>

</ul>
</details>

**Tags**: `#premarket movers`, `#semiconductors`, `#AI financing`, `#earnings`, `#executive changes`

---

<a id="item-finance-news-2"></a>
### [S&amp;P Sees China Property Prices Bottoming in 2028 as Big Cities Recover Sooner](https://www.cnbc.com/2026/10/08/chinas-real-estate-market-may-be-set-for-a-turnaround-sp-says.html) ⭐️ 7.0/10

S&amp;P Global Ratings analysts said in a report distributed Thursday that China&\#x27;s residential property prices may hit a bottom in the third quarter of 2028, with prices in large cities such as Beijing and Shanghai possibly recovering as soon as next year — a shift from February, when the agency said high levels of unsold housing kept a recovery &quot;out of reach.&quot; The forecast comes after residential prices have already fallen 22% from their 2021 peak, and Guotai Junan International chief economist Hao Zhou separately predicted tier-one existing-home prices could post their first growth in the fourth quarter of this year.

rss · CNBC Finance · Oct 8, 09:27

**「Background」** China&\#x27;s housing market has been sliding since prices peaked in 2021, after developers like Evergrande fueled rapid growth by selling apartments before they were built — a model Beijing moved to restrict in August by limiting sales of unfinished homes. S&amp;P now expects national residential prices to bottom in the third quarter of 2028, after a 22% fall from that 2021 peak; by comparison, it says U.S. residential prices fell 26% around the financial crisis.

**「Impact」** Developers are expected to buy less land and start fewer new projects, which S&amp;P says would help ease China&\#x27;s housing oversupply but weigh on developer revenue.

**Tags**: `#China real estate`, `#S&amp;P Global Ratings`, `#property market outlook`, `#housing policy`, `#mortgage subsidies`

---

<a id="item-finance-news-3"></a>
### [US Government Suspends Microsoft From Green Card Sponsorship Program Over Fraud Allegation](https://apnews.com/article/h1b-visa-program-vance-microsoft-e7b3a407f822702b269ee277d21343ea) ⭐️ 7.0/10

The Trump administration said it is suspending Microsoft from a program that sponsors foreign workers for green cards, alleging fraud. Vice President JD Vance said Microsoft cut 6,000 US employees last year while obtaining 6,300 H-1B visas and nearly 3,000 green cards, and named nine universities as suspected abusers of the J-1 visa program; Microsoft has not responded.

telegram · zaihuapd · Oct 9, 00:00

**「Background」** The H-1B visa lets U.S. employers hire foreign workers for specialty jobs, and employers can then sponsor those workers for green cards, which grant permanent residency; the administration is suspending Microsoft from that sponsorship program as part of a broader visa-fraud enforcement push that also accuses universities of misusing the J-1 exchange-visa program \(tool-1-2, tool-1-3\).

**「Impact」** Microsoft employees who depend on the company to sponsor their green cards, and its ability to hire foreign workers needing visa sponsorship, face delays while the company is barred from the program; the allegations remain unanswered by Microsoft.

<details><summary>References</summary>
<ul>
<li><a href="https://www.nytimes.com/2026/10/08/us/politics/microsoft-visas-green-cards.html">Trump Administration Suspends Microsoft From Green Card ...</a></li>
<li><a href="https://www.youtube.com/watch?v=OZJiZPNCPYA">Trump administration is suspending Microsoft from the H - 1 B green ...</a></li>

</ul>
</details>

**Tags**: `#美国移民政策`, `#H-1B签证`, `#微软`, `#科技行业用工`, `#政府执法`

---

<a id="item-finance-news-4"></a>
### [SpaceX to Acquire Nationwide Low-Band Spectrum Licenses](https://x.com/SpaceX/status/2108291133025698301) ⭐️ 7.0/10

SpaceX said it has agreed to acquire a nationwide portfolio of low-band spectrum licenses, aimed at letting its Starlink Mobile service operate as a U.S. mobile broadband provider. SpaceX said pairing the licenses with its Gen2 satellite constellation would give people across the U.S. high-speed mobile broadband; the price, seller, regulatory approval status and timeline were not disclosed in the announcement as reported by a Telegram aggregator.

telegram · zaihuapd · Oct 9, 01:04

**「Background」** SpaceX, founded in 2002 by Elon Musk and best known for designing and launching rockets and spacecraft, is moving into consumer mobile service. Low-band spectrum means lower-frequency radio airwaves, which travel farther and pass through buildings more easily than higher-frequency bands, making them suited to wide-area coverage.

**「Impact」** The move would let SpaceX sell mobile service directly to U.S. consumers, putting it in competition with existing carriers; shares in incumbent cell providers fell as much as 8% after the announcement, Bloomberg reported.

<details><summary>References</summary>
<ul>
<li><a href="https://en.m.wikipedia.org/wiki/SpaceX">SpaceX - Wikipedia</a></li>
<li><a href="https://www.spacex.com/">SpaceX</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-10-08/spacex-to-acquire-low-band-spectrum-for-mobile-phone-service">SpaceX Acquires Nationwide Spectrum License to Boost Starlink ...</a></li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Starlink`, `#spectrum acquisition`, `#telecom`, `#M&amp;A`

---