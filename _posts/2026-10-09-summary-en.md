---
layout: default
title: "Horizon Summary: 2026-10-09 (EN)"
date: 2026-10-09
lang: en
---

> From 41 items, 9 important content pieces were selected

---

**Technology News**
1. [ThinkingBox-Bench grades 507 agent workflows on database state across 20 runs](#item-tech-news-1) ⭐️ 7.0/10
2. [OpenAI Bans Russian and Iranian ChatGPT Influence Operations](#item-tech-news-2) ⭐️ 7.0/10
3. [Anthropic launches free opt-in OSS vulnerability scanner](#item-tech-news-3) ⭐️ 7.0/10

**Financial News**
1. [S&amp;P forecasts China housing bottom in third quarter 2028](#item-finance-news-1) ⭐️ 8.0/10
2. [China&\#x27;s HR ministry opens comment on draft gig-worker protection rules](#item-finance-news-2) ⭐️ 8.0/10
3. [Stocks making the biggest moves premarket: Haemonetics, Broadcom, Lululemon, Palantir, Wolfspeed &amp; more](#item-finance-news-3) ⭐️ 7.0/10
4. [FT: OpenAI 年化收入约为 500 亿美元，比此前报道少约 200 亿美元](#item-finance-news-4) ⭐️ 7.0/10
5. [US suspends Microsoft from green card program over fraud allegations](#item-finance-news-5) ⭐️ 7.0/10
6. [SpaceX agrees to buy nationwide low-band spectrum licenses for Starlink Mobile](#item-finance-news-6) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [ThinkingBox-Bench grades 507 agent workflows on database state across 20 runs](https://www.reddit.com/r/MachineLearning/comments/1x17shf/thinkingbox_solving_an_agent_task_once_vs_solving/) ⭐️ 7.0/10

Microsoft-affiliated authors released ThinkingBox-Bench, a public benchmark of 507 policy-conditioned business workflows across five domains \(retail, travel/hospitality, auto insurance, neobank internal IT, and consulting IT/HR\). Each task is executed in 20 independent attempts from an identical clean backend — 10,140 trials per model — and grading compares the terminal backend state and side effects against the required end state rather than accepting a &quot;task finished&quot; signal; 477 of 507 tasks are graded on state alone, and 30 also check a narrow property of the final response. The authors report that discovery and repeatability rank models differently: Kimi-K3 solved 93.89% of tasks at least once \(476/507\) but only 13.41% \(68/507\) on all 20 attempts, while Claude Opus 5 solved 79.09% at least once and 47.53% \(241 tasks\) on all 20. The paper, code, and dataset are public and the environment is on Hugging Face OpenEnv, but raw evaluation trajectories are not released.

reddit · r/MachineLearning · /u/tuhin\_k · Oct 9, 00:50

**「Background」** Agent evaluations have typically judged a run by whether the agent declares the task finished or returns the right final answer, rather than by the state the backend is left in. Microsoft&\#x27;s ThinkingBox-Bench is framed directly against that gap — &quot;The Agent Said It Was Done. The Database Disagreed.&quot; — and is distributed as executable tasks so the same workflows can be run against other models \(tool-2-2, tool-2-1\).

**「Impact」** Practitioners can run any of the 507 tasks against their own model through the Hugging Face OpenEnv environment, and the authors argue reliability reporting should show pass@1, pass@20, and the all-20 count separately, since ranking by pass@20 and by all-20 produced nearly reversed leaderboards across the nine models plotted. In a retrospective ablation over 121,680 valid trials across 12 models, 79,853 failed the executable checks, and 67.24% of those failures still terminated cleanly after invoking a state-changing tool with no final tool error — so completion-style proxies would have scored them as done. The authors caution that 20/20 is an observed count on a fixed trial budget, not a guarantee of future reliability, and that the simulated user is a fixed LLM.

<details><summary>References</summary>
<ul>
<li>ThinkingBox: Measuring whether agents finish the job - Command Line</li>
<li>The Agent Said It Was Done. The Database Disagreed. - Hugging Face</li>

</ul>
</details>

**Tags**: `#LLM agents`, `#benchmarks and evaluation`, `#agent reliability`, `#stateful workflows`, `#AI research`

---

<a id="item-tech-news-2"></a>
### [OpenAI Bans Russian and Iranian ChatGPT Influence Operations](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) ⭐️ 7.0/10

OpenAI said it banned two covert influence operations that used ChatGPT. The Russian operation allegedly used impersonated identities to control a Latin American &quot;research platform&quot; and spread content damaging Ukraine&\#x27;s reputation and affecting local politics; the Iranian operation ran seven fake &quot;journalist&quot; personas that pitched articles to small and mid-sized news outlets worldwide and mass-generated social media comments. OpenAI rated the Russian operation as category 5 on its influence-operation breakthrough scale — the first time it has done so since it began reporting — and the Iranian operation as category 4, with nearly 100 bylined articles produced. Both campaigns mixed traditional methods with AI, and some of the content reached mainstream media, according to the account.

telegram · zaihuapd · Oct 8, 15:52

**「Background」** OpenAI has an established practice of investigating and publicly disclosing covert influence operations that misuse its models, and grades them on an &quot;influence operations breakthrough scale&quot; that measures how far a campaign combines conventional tactics with AI-generated content. According to the source, the Russian operation is the first to be rated Category 5 since OpenAI began publishing these reports, while the Iranian one was rated Category 4.

**「Impact」** OpenAI&\#x27;s first Category 5 rating for the Russian operation — versus mostly Category 1–2 activity among roughly 30 earlier disrupted operations — indicates the campaign crossed into authentic communities, so newsrooms and platforms that carried its content face a higher burden to verify contributor identities and review or label published material. Because OpenAI&\#x27;s ban closes ChatGPT accounts rather than external articles or comments, the Iranian operation&\#x27;s fake-journalist placements and any mainstream pickups would need to be addressed by the receiving outlets themselves.

<details><summary>References</summary>
<ul>
<li><a href="https://beyondtmrw.org/article/disrupting-ai-enabled-false-front-operations">OpenAI Dark Clark Category 5: Russia, Iran ops | Beyond Tomorrow</a></li>
<li><a href="https://www.ainvest.com/news/openai-category-5-influence-op-reading-banned-io-headline-2610/">OpenAI&#x27;s First Category 5 Influence Op: Reading Past the &quot;Banned IO ...</a></li>

</ul>
</details>

**Tags**: `#AI安全`, `#影响力行动`, `#OpenAI`, `#虚假信息`, `#平台治理`

---

<a id="item-tech-news-3"></a>
### [Anthropic launches free opt-in OSS vulnerability scanner](https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source) ⭐️ 7.0/10

Anthropic announced OSS Scanner, a free, opt-in vulnerability scanning service for eligible open-source projects. Reports are generated by Claude and other models without human review, include vulnerability reproduction steps and explanations, and offer patch suggestions where possible; Anthropic states they may contain errors. Anthropic says that over the past six months it found more than 29,000 candidate vulnerabilities and human-reviewed about 6,000, and that 85 of 97 high-severity or critical findings from early testing met its disclosure process requirements. Core maintainers of qualifying projects can apply by submitting a GitHub pull request.

telegram · zaihuapd · Oct 9, 02:00

**「Background」** Anthropic says OSS Scanner is informed by its experience using Claude to find vulnerabilities during an earlier effort it calls Project Glasswing, described in the company&\#x27;s own launch post. Rather than a one-off research exercise, the service periodically scans enrolled codebases with Anthropic&\#x27;s frontier models and returns the resulting reports to the projects&\#x27; maintainers.

**「Impact」** Maintainers of qualifying projects can obtain scan reports at no cost, but because the findings are unreviewed model output that may be wrong, they should verify each reported vulnerability before acting on it or publishing a patch. Access is gated by an application: a core maintainer must submit a GitHub pull request to enroll a project.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source">An opt - in vulnerability - finding service for open - source software</a></li>
<li><a href="https://dev.to/alifar/anthropic-oss-scanner-uses-ai-to-find-vulnerabilities-in-opted-in-open-source-projects-p29">Anthropic OSS Scanner Uses AI to Find Vulnerabilities in Opted - In ...</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#open source`, `#vulnerability scanning`, `#Anthropic`, `#Claude`

---

## Financial News

<a id="item-finance-news-1"></a>
### [S&amp;P forecasts China housing bottom in third quarter 2028](https://www.cnbc.com/2026/10/08/chinas-real-estate-market-may-be-set-for-a-turnaround-sp-says.html) ⭐️ 8.0/10

S&amp;P Global Ratings analysts said China&\#x27;s residential property prices may bottom in the third quarter of 2028, with prices in large cities such as Beijing and Shanghai possibly recovering as soon as next year, helped by August restrictions on selling unfinished homes and a mortgage-rate subsidy for first-time buyers of units under 1.5 million yuan \($220,000\).

rss · CNBC Finance · Oct 8, 09:27

**「Background」** The forecast is a shift from February, when S&amp;P said high levels of unsold housing kept a recovery out of reach; Chinese developers had long relied on pre-selling unfinished apartments, and S&amp;P says residential prices have already fallen 22% from a 2021 peak, compared with a 67% drop in Japan and 26% in the U.S.

**「Impact」** A sustained recovery would ease pressure on Chinese homeowners and developers, but Morgan Stanley analyst Stephen Cheung said the mortgage subsidy may mostly pull forward planned purchases rather than create substantial new demand.

**Tags**: `#China real estate`, `#S&amp;P Global Ratings`, `#housing policy`, `#mortgage subsidies`, `#property market forecast`

---

<a id="item-finance-news-2"></a>
### [China&\#x27;s HR ministry opens comment on draft gig-worker protection rules](https://mp.weixin.qq.com/s/saqkOXlhe0wX7qD83vdkRw) ⭐️ 8.0/10

China&\#x27;s Ministry of Human Resources and Social Security released a draft regulation on October 8 for public comment through November 8 that would require pay for platform-based gig workers — including ride-hailing drivers, delivery riders and livestreamers — to be no lower than the local minimum wage, guarantee proper rest after four consecutive hours of work, and bar automatic algorithmic decisions such as stopping dispatch or banning accounts without human review, according to the draft as reported by Jiupai News. The draft also prohibits abuse of punitive measures such as fines; it is a consultation document, not yet a final rule.

telegram · zaihuapd · Oct 8, 09:23

**「Background」** China has previously lacked a formal regulation covering platform workers who are subject to company labor management but do not fully meet the legal test for an employment relationship; this draft is the first rule to bring them into labor-law protection, according to Xinhua.

**「Who would be affected」** If the draft becomes final, platform operators in ride-hailing, food delivery and livestreaming would have to change how they set pay and how they use algorithms — including requiring human review before suspending dispatches or banning accounts — while their workers would gain minimum-wage and rest protections; the measure is described as China&\#x27;s first such rule issued in the form of a ministry regulation.

<details><summary>References</summary>
<ul>
<li><a href="http://www3.xinhuanet.com/politics/20261008/6e01730616fc4900b2892af1e904914e/c.html">新华社权威快报丨新就业形态劳动者权益保障办法公开征求意见</a></li>
<li>EU-China talks; PBoC on RMB; Measures for protecting the rights ...</li>

</ul>
</details>

**Tags**: `#gig economy`, `#labor rights`, `#China regulation`, `#platform algorithms`, `#minimum wage`

---

<a id="item-finance-news-3"></a>
### [Stocks making the biggest moves premarket: Haemonetics, Broadcom, Lululemon, Palantir, Wolfspeed &amp; more](https://www.cnbc.com/2026/10/08/stocks-making-the-biggest-moves-premarket-hae-avgo-lulu-wolf.html) ⭐️ 7.0/10

A premarket movers roundup highlighting several material semiconductor, AI-infrastructure, financing, and earnings developments alongside routine stock moves.

rss · CNBC Finance · Oct 8, 12:28

**Tags**: `#premarket stock movers`, `#semiconductor financing`, `#AI infrastructure`, `#corporate earnings`, `#Defense Department loan`

---

<a id="item-finance-news-4"></a>
### [FT: OpenAI 年化收入约为 500 亿美元，比此前报道少约 200 亿美元](https://www.ft.com/content/b66a9858-f8fb-46cb-b506-44bfe26fca2a?syn-25a6b1a6=1) ⭐️ 7.0/10

据《金融时报》援引投资者获得的财务文件，OpenAI 9 月底的年化收入接近 500 亿美元，比此前广泛报道的 700 亿美元少约 200 亿美元。报道称，这一差距部分来自口径不同：Anthropic 计入通过 AWS、谷歌云等云伙伴销售的收入，OpenAI 则不计入；OpenAI 拒绝置评。

telegram · zaihuapd · Oct 8, 17:22

**「Background」** OpenAI is privately held and does not publish financial statements, so its revenue figures come from documents shown to investors. Earlier reports had put annualized revenue near $70 billion, while rival Anthropic counts sales made through cloud partners such as AWS and Google Cloud and OpenAI does not, which helps explain the differing totals.

**「影响」** 若这一较低数字被投资者接受，可能削弱市场对 AI 需求增长的乐观预期；但由于统计口径不同，这两个数字并不能直接比较。

<details><summary>References</summary>
<ul>
<li><a href="https://finance.yahoo.com/technology/ai/articles/openai-annualized-revenue-20-billion-195013069.html">OpenAI annualized revenue $20 billion less than previously reported</a></li>
<li><a href="https://digg.com/tech/bi8cxrn1">OpenAI &#x27;s annualized revenue reportedly neared $50 billion at the...</a></li>
<li><a href="https://qz.com/openai-annualized-revenue-50-billion-correction-ai-stocks-100826">OpenAI corrects annualized revenue figure to $50 billion</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#AI revenue`, `#Financial Times`, `#AI market sentiment`, `#private company financials`

---

<a id="item-finance-news-5"></a>
### [US suspends Microsoft from green card program over fraud allegations](https://apnews.com/article/h1b-visa-program-vance-microsoft-e7b3a407f822702b269ee277d21343ea) ⭐️ 7.0/10

The Trump administration suspended Microsoft from a foreign-worker green card program over fraud allegations, with Vice President JD Vance saying the company laid off 6,000 US employees while obtaining 6,300 H-1B visas and nearly 3,000 green cards last year. Vance also accused nine universities, including Harvard, Yale and MIT, of abusing the J-1 visa program; Microsoft has not responded.

telegram · zaihuapd · Oct 9, 00:00

**「Background」** The program at issue is the Labor Department&\#x27;s permanent labor certification, known as PERM, which requires an employer to show it tried and failed to find qualified US workers before sponsoring a foreign employee for a green card; Vice President JD Vance said companies like Microsoft had been exploiting that process \(tool-1-2\). Microsoft has disputed his account of its hiring \(tool-1-1\), and the administration&\#x27;s action also covered other IT firms \(tool-1-3\).

**「Impact」** The suspension also covers Adobe and several IT outsourcing firms and applies to new and pending green-card sponsorship applications, so foreign workers at those companies who are pursuing permanent residency could have their applications blocked.

<details><summary>References</summary>
<ul>
<li>Microsoft pushes back on Vance&#x27;s H-1B visa claims | The Seattle Times</li>
<li>Microsoft Suspended From Green Card Program as Trump Officials ...</li>
<li>Trump administration freezes green cards for Microsoft, IT firms, probes ...</li>
<li>Trump administration freezes green cards for Microsoft, IT firms, probes ...</li>
<li>The Trump administration is suspending Microsoft from a green ...</li>
<li>Trump officials block Microsoft&#x27;s access to program for employee ...</li>

</ul>
</details>

**Tags**: `#immigration policy`, `#H-1B visas`, `#Microsoft`, `#labor market`, `#fraud allegations`

---

<a id="item-finance-news-6"></a>
### [SpaceX agrees to buy nationwide low-band spectrum licenses for Starlink Mobile](https://x.com/SpaceX/status/2108291133025698301) ⭐️ 7.0/10

SpaceX announced an agreement to acquire a portfolio of low-band spectrum licenses covering the entire United States, which the company says would support high-speed Starlink Mobile broadband nationwide by combining the spectrum with its Gen2 satellite constellation. SpaceX did not disclose the purchase price, the seller, the number of licenses, or a regulatory approval timeline.

telegram · zaihuapd · Oct 9, 01:04

**「Background」** Starlink is SpaceX’s satellite-internet service, which had more than 12 million subscribers as of June 2026, and SpaceX previously agreed in September 2025 to buy EchoStar’s AWS-4 and H-block spectrum licenses for $17 billion.

**「Impact」** The deal would put SpaceX in competition with established U.S. carriers such as AT&amp;T, Verizon and T-Mobile for everyday mobile service, rather than leaving satellite links as a backup safety feature — and the acquisition still needs Federal Communications Commission approval.

<details><summary>References</summary>
<ul>
<li>SpaceX moves to buy nationwide low-band spectrum to rival US carriers</li>
<li><a href="https://en.wikipedia.org/wiki/Starlink">Starlink - Wikipedia</a></li>
<li><a href="https://starlink.com/">Starlink</a></li>
<li>SpaceX takes aim at US wireless carriers with spectrum acquisition</li>
<li>SpaceX announced a deal on Thursday, Oct. 8, to buy ... - Facebook</li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Starlink`, `#spectrum acquisition`, `#telecom`, `#satellite broadband`

---