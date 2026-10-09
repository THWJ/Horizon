---
layout: default
title: "Horizon Summary: 2026-10-09 (EN)"
date: 2026-10-09
lang: en
---

> From 41 items, 7 important content pieces were selected

---

**Technology News**
1. [ThinkingBox-Bench grades agent workflows on final database state over 20 runs](#item-tech-news-1) ⭐️ 7.0/10
2. [OpenAI Bans Two ChatGPT-Enabled Influence Operations, One Rated Category 5](#item-tech-news-2) ⭐️ 7.0/10
3. [Anthropic launches OSS Scanner, free AI vulnerability reports without human review](#item-tech-news-3) ⭐️ 7.0/10

**Financial News**
1. [S&amp;P: China&\#x27;s property slump may be nearing a bottom, though national prices may not bottom until 2028](#item-finance-news-1) ⭐️ 7.0/10
2. [OpenAI 年化收入比此前报道少 200 亿美元](#item-finance-news-2) ⭐️ 7.0/10
3. [美政府以欺诈为由暂停微软绿卡申请资格](#item-finance-news-3) ⭐️ 7.0/10
4. [SpaceX Announces Deal to Buy Nationwide Low-Band Spectrum Licenses](#item-finance-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [ThinkingBox-Bench grades agent workflows on final database state over 20 runs](https://www.reddit.com/r/MachineLearning/comments/1x17shf/thinkingbox_solving_an_agent_task_once_vs_solving/) ⭐️ 7.0/10

In an author-posted r/MachineLearning thread, Microsoft researchers introduced ThinkingBox-Bench, a benchmark of 507 policy-conditioned business workflows across five domains \(retail, travel/hospitality, auto insurance, neobank internal IT, consulting IT/HR\) that runs each task 20 times from an identical clean backend — 10,140 trials per model — and grades agents on the terminal backend/database state and side effects rather than on whether the run appeared to finish. Any trajectory producing the required end state passes, while wrong, missing, or extra effects fail; 477 of 507 tasks are graded on state alone and 30 also check a narrow property of the final response, with results reported as pass@1, pass@20 \(solved at least once in 20 attempts\), and all-20 \(solved every time\). The authors&\#x27; reported figures show discovery and repeatability ranking models differently: Kimi-K3 solved 93.89% of tasks at least once but only 13.41% on all 20, Claude Opus 5 solved 79.09% at least once but 47.53% on all 20, and Qwen3.8-27B 89.35% versus 7.50%. A retrospective ablation over 121,680 valid trials across 12 models found 79,853 failures on the executable checks, 67.24% of which still terminated cleanly after invoking a state-changing tool with no final error; the authors state the tasks are synthetic reconstructions of enterprise patterns, that 20/20 is an observed count on a fixed trial budget rather than a reliability guarantee, and that raw evaluation trajectories were not released. The paper, code, and dataset are public, and any of the 507 tasks can be run against another model through the Hugging Face OpenEnv environment.

reddit · r/MachineLearning · /u/tuhin\_k · Oct 9, 00:50

**「Background」** Agent benchmarks have conventionally reported a single success rate — whether a model completes a task once, or on average across attempts — which the paper&\#x27;s own framing, &quot;One Success Isn&\#x27;t Reliability,&quot; treats as the gap ThinkingBox is built to close. The work is presented as a reusable sandbox for verifiable tool–agent–user interaction paired with Thinkingbox-bench, its executable benchmark for stateful business workflows \(arXiv 2608.19741\).

**「What this means for agent evaluation」** The most actionable result is the failure ablation: across 121,680 valid trials, 67.24% of trajectories that failed the executable checks still terminated cleanly with a state-changing tool call and no final tool error, so teams treating a clean completion or successful tool invocation as task success would have counted roughly two-thirds of those observed failures as passes. Since the 507 workflows are published and runnable through the Hugging Face OpenEnv environment, developers can re-grade their own agents on terminal backend/database state instead of response plausibility — and should expect pass@20 and all-20 leaderboards to disagree sharply about which model is most reliable.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2608.19741">[2608.19741] One Success Isn&#x27;t Reliability: Thinkingbox, a ...</a></li>
<li><a href="https://arxiv.org/html/2608.19741">One Success Isn’t Reliability: Thinkingbox, a Sandbox and ...</a></li>
<li><a href="https://www.explainx.ai/blog/microsoft-thinkingbox-agent-benchmark-stateful-2026">ThinkingBox: Microsoft Agent Benchmark Explained (2026 ...</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#LLM evaluation`, `#benchmarks`, `#agent reliability`, `#stateful workflows`

---

<a id="item-tech-news-2"></a>
### [OpenAI Bans Two ChatGPT-Enabled Influence Operations, One Rated Category 5](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) ⭐️ 7.0/10

OpenAI banned two covert influence operations that used ChatGPT, according to a source summary of the company&\#x27;s disclosure. The Russian operation is said to have used fraudulent identities to control a Latin American &quot;research platform&quot; and spread content damaging Ukraine&\#x27;s reputation and influencing local politics; the Iranian operation ran seven &quot;journalist&quot; personas pitching articles to small and mid-sized outlets worldwide and also mass-generated social media comments. OpenAI rated the Russian operation Category 5 on its influence-operation breakthrough scale — the first time it has done so since it began reporting — and the Iranian operation Category 4, with nearly 100 signed articles produced. Both campaigns mixed conventional tactics with AI, and the source says some of the content reached mainstream media; the summary does not detail takedown timing, account counts, or which outlets carried the material.

telegram · zaihuapd · Oct 8, 15:52

**「Background」** OpenAI periodically publishes reports on covert influence campaigns that used its models, and earlier disclosures covered similar state-linked activity: one described banning Russia-origin accounts that used ChatGPT to promote a fictitious Israel-based think tank and a &quot;sovereignty&quot; index praising Russia and criticizing the West, and reporting on another round counted five operations traced to China, Iran, Israel, and two from Russia. The new report is notable within that series because the Russian campaign received a Category 5 rating on OpenAI&\#x27;s influence-operations scale, which the source says is the first time it has assigned that level.

**「Impact」** For newsrooms and smaller outlets, the reported reach of AI-assisted pitches into mainstream media makes verifying the identity and affiliations of unfamiliar contributors a direct operational concern, since the Iranian operation obtained publication under journalist personas; the source does not say whether any outlet has issued corrections, retractions, or new contributor-vetting rules.

<details><summary>References</summary>
<ul>
<li><a href="https://www.darkreading.com/threat-intelligence/openai-disrupts-5-ai-powered-state-backed-influence-ops">OpenAI Disrupts 5 AI -Powered, State-Backed Influence Ops</a></li>
<li><a href="https://openai.com/index/disrupting-malicious-uses-of-ai-influence-campaign-russia/">Disrupting a new covert influence campaign from Russia | OpenAI</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#AI misuse`, `#influence operations`, `#disinformation`, `#AI safety`

---

<a id="item-tech-news-3"></a>
### [Anthropic launches OSS Scanner, free AI vulnerability reports without human review](https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source) ⭐️ 7.0/10

Anthropic has launched OSS Scanner, a free, opt-in vulnerability scanning service for eligible open-source projects, with applications submitted by core maintainers via GitHub PR. Anthropic says reports are generated by models including Claude without human review and include vulnerability reproduction, an explanation, and patch suggestions where possible; the service may contain errors. Anthropic claims that over the past six months it found more than 29,000 candidate vulnerabilities and human-reviewed about 6,000. Of 97 high-severity or critical vulnerabilities in early testing, 85 met its disclosure-process requirements, according to the company; these figures are vendor claims from a brief secondary summary and have not been independently verified here.

telegram · zaihuapd · Oct 9, 02:00

**「Background」** Anthropic says OSS Scanner builds on Project Glasswing, its earlier effort using Claude to find vulnerabilities, and applies its strongest models to recurring scans of participating projects. Access is opt-in rather than automatic: core maintainers apply by submitting a pull request to Anthropic&\#x27;s OSS Scanner repository, and Anthropic said it reviews applicants case by case, prioritizing projects whose compromise would critically affect infrastructure or user security.

**「Maintainer triage burden」** Because OSS Scanner&\#x27;s reports are model-generated and explicitly not human-reviewed, maintainers of opted-in projects absorb the full triage cost of deciding which candidate findings are real before any suggested patch is trusted. That lands on a maintainer population already reporting a wave of low-quality, AI-generated vulnerability reports, according to an OpenSSF vulnerability-disclosures working group issue.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source">An opt-in vulnerability-finding service for open-source ...</a></li>
<li><a href="https://kju.ai/story/anthropic-announces-opt-in-oss-vulnerability-scanner">Anthropic announces opt-in OSS vulnerability scanner | Kju</a></li>
<li><a href="https://github.com/ossf/wg-vulnerability-disclosures/issues/178">AI -SLOP: Develop best current practises for Open Source ...</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#open-source security`, `#vulnerability scanning`, `#AI security`, `#LLM`

---

## Financial News

<a id="item-finance-news-1"></a>
### [S&amp;P: China&\#x27;s property slump may be nearing a bottom, though national prices may not bottom until 2028](https://www.cnbc.com/2026/10/08/chinas-real-estate-market-may-be-set-for-a-turnaround-sp-says.html) ⭐️ 7.0/10

S&amp;P Global Ratings analysts said China&\#x27;s yearslong residential property slump may be nearing a bottom, forecasting that national home prices will bottom in the third quarter of 2028 and that prices in the largest cities such as Beijing and Shanghai could recover as soon as next year.

rss · CNBC Finance · Oct 8, 09:27

**「Background」** In February, S&amp;P said high levels of unsold housing kept a recovery &quot;out of reach&quot;; the shift follows Beijing&\#x27;s August restrictions on developers selling unfinished homes and a September mortgage-rate subsidy for first-time buyers of units under 1.5 million yuan \($220,000\) and 120 square meters, after residential prices had already fallen 22% from a 2021 peak.

**「Impact」** If the forecast holds, developers would buy less land and build fewer projects — the report&\#x27;s main lever for stabilizing prices over the next one to two years — while the subsidy targets first-time buyers of smaller, cheaper homes.

**Tags**: `#China property market`, `#S&amp;P Global Ratings`, `#housing policy`, `#mortgage subsidies`, `#market outlook`

---

<a id="item-finance-news-2"></a>
### [OpenAI 年化收入比此前报道少 200 亿美元](https://www.ft.com/content/b66a9858-f8fb-46cb-b506-44bfe26fca2a?syn-25a6b1a6=1) ⭐️ 7.0/10

据《金融时报》看到的投资者文件，OpenAI 截至 9 月底的年化收入接近 500 亿美元，比此前广泛报道的 700 亿美元少约 200 亿美元；差异部分来自计算口径不同——Anthropic 计入通过 AWS、谷歌云等云伙伴实现的销售，OpenAI 未计入。OpenAI 拒绝置评，该数字尚未得到公司确认。

telegram · zaihuapd · Oct 8, 17:22

**「Background」** OpenAI had previously signaled annualized revenue—a run-rate based on recent sales—of about $70bn to investors, and that higher figure was widely reported. The lower figure partly reflects an accounting difference: Anthropic includes sales made through cloud partners such as AWS and Google Cloud, while OpenAI does not.

**「Impact」** Investors in AI-linked shares felt the immediate effect: after the report, the Nasdaq fell and AI-related stocks declined, as a figure below earlier expectations called into question the continued growth in computing demand that the market had priced in.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/business/openais-annualized-revenue-20-billion-less-than-previously-signaled-ft-reports-2026-10-08/">OpenAI&#x27;s September annualized revenue nears $50 billion, less ...</a></li>
<li><a href="https://techcrunch.com/2026/10/08/openais-revenue-is-reportedly-20-billion-less-than-previously-projected/">OpenAI’s revenue is reportedly $20 billion less than ...</a></li>
<li><a href="https://www.forbes.com/sites/josipamajic/2026/03/25/openai-and-anthropic-count-revenue-differently-and-investors-are-looking-into-it/">OpenAI And Anthropic Count Revenue Differently, And ... - Forbes</a></li>
<li><a href="https://www.zerohedge.com/markets/nasdaq-tumbles-after-ft-reports-openai-revenues-disappointing">Nasdaq Tumbles After FT Reports OpenAI Revenues ... | ZeroHedge</a></li>
<li><a href="https://verifiedinvesting.com/blogs/live-show-recap/trading-the-close-market-recap-10-08-2026-openai-revenue-shock-sparks-tech-volatility-10-year-yield-oil-silver-bitcoin-levels-to-watch">Trading The Close Market Recap - 10/08/ 2026 : OpenAI Revenue ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/07/stock-market-today-live-updates-.html">Stock market news for Oct. 8, 2026</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#AI industry`, `#annualized revenue`, `#financial disclosure`, `#market sentiment`

---

<a id="item-finance-news-3"></a>
### [美政府以欺诈为由暂停微软绿卡申请资格](https://apnews.com/article/h1b-visa-program-vance-microsoft-e7b3a407f822702b269ee277d21343ea) ⭐️ 7.0/10

特朗普政府宣布暂停微软参与外籍劳工绿卡申请项目，指控其存在欺诈行为。副总统万斯称，微软去年裁减6000名美国员工，同时获得6300份H-1B签证和近3000张绿卡，是“利用该系统最多的公司”；这些指控尚未得到证实，微软也尚未回应。

telegram · zaihuapd · Oct 9, 00:00

**「Background」** The suspension targets the PERM program, a federal certification that lets employers sponsor foreign workers for permanent U.S. residency, and reports say several other major technology companies were suspended from it as well.

**「Impact」** The suspension directly affects Microsoft&\#x27;s H-1B employees who rely on the company to sponsor a green card — the usual route to staying in the U.S. long term — and it constrains Microsoft&\#x27;s ability to recruit foreign skilled workers while the ban is in place.

<details><summary>References</summary>
<ul>
<li><a href="https://abcnews.com/Politics/vance-suspends-microsoft-green-card-program-crack-alleged/story?id=137100899">Vance suspends Microsoft from a green card program to crack ...</a></li>
<li><a href="https://finance.yahoo.com/economy/policy/articles/microsoft-suspended-green-card-program-153952894.html?fr=sycsrp_catchall">Microsoft Is Suspended From Green Card Program. Vance Accuses ...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/oct/08/jd-vance-microsoft-visa-workers-green-card-suspension">Microsoft suspended from applying for green cards for H-1B ...</a></li>

</ul>
</details>

**Tags**: `#Microsoft`, `#H-1B visa`, `#green card`, `#immigration policy`, `#tech labor`

---

<a id="item-finance-news-4"></a>
### [SpaceX Announces Deal to Buy Nationwide Low-Band Spectrum Licenses](https://x.com/SpaceX/status/2108291133025698301) ⭐️ 7.0/10

SpaceX said it has reached an agreement to acquire a nationwide portfolio of low-band spectrum licenses, which it says would let its Starlink Mobile service offer high-speed mobile broadband across the U.S. The announcement, made by the company, did not disclose the seller, the deal value, or a timeline, and it describes a planned transaction rather than a completed one.

telegram · zaihuapd · Oct 9, 01:04

**「Background」** Low-band spectrum — the airwaves that travel long distances and penetrate buildings — is licensed by U.S. regulators, and SpaceX reached a spectrum sale and commercial agreement with EchoStar in September 2025 that would also let Boost Mobile subscribers use Starlink&\#x27;s direct-to-cell service.

**「Impact」** If completed, the deal would put SpaceX in direct competition with U.S. wireless carriers AT&amp;T, Verizon and T-Mobile by offering Starlink Mobile service that bypasses conventional cell towers, according to Reuters, and CNBC reported those carriers&\#x27; shares fell after the announcement. The agreement remains subject to completion and no deal value, seller or regulatory timeline was disclosed.

<details><summary>References</summary>
<ul>
<li><a href="https://ir.echostar.com/news-releases/news-release-details/echostar-announces-spectrum-sale-and-commercial-agreement-spacex">EchoStar Announces Spectrum Sale and Commercial Agreement ...</a></li>
<li><a href="https://www.reuters.com/business/media-telecom/spacex-acquire-spectrum-that-enables-starlink-mobile-services-2026-10-08/">SpaceX takes aim at US wireless carriers with spectrum ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/08/spacex-spectrum-license-att-verizon-tmobile.html">SpaceX spectrum license hammers shares of AT&amp;T ... - CNBC</a></li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Starlink`, `#spectrum acquisition`, `#US telecom`, `#satellite broadband`

---