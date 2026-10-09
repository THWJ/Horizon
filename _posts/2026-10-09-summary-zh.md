---
layout: default
title: "Horizon Summary: 2026-10-09 (ZH)"
date: 2026-10-09
lang: zh
---

> 从 41 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [ThinkingBox-Bench：507 个业务流程各跑 20 次，按数据库终态评分](#item-tech-news-1) ⭐️ 7.0/10
2. [OpenAI 封禁俄伊两起利用 ChatGPT 的影响行动](#item-tech-news-2) ⭐️ 7.0/10
3. [Anthropic 推出 OSS Scanner 免费开源漏洞扫描服务](#item-tech-news-3) ⭐️ 7.0/10

**财经新闻**
1. [标普：中国住宅价格或于 2028 年三季度见底](#item-finance-news-1) ⭐️ 8.0/10
2. [人社部就新就业形态劳动者权益保障办法征求意见](#item-finance-news-2) ⭐️ 8.0/10
3. [Stocks making the biggest moves premarket: Haemonetics, Broadcom, Lululemon, Palantir, Wolfspeed &amp; more](#item-finance-news-3) ⭐️ 7.0/10
4. [FT：OpenAI 9 月底年化收入接近 500 亿美元，比此前报道少约 200 亿](#item-finance-news-4) ⭐️ 7.0/10
5. [美政府以欺诈为由暂停微软绿卡申请资格](#item-finance-news-5) ⭐️ 7.0/10
6. [SpaceX 宣布拟收购全美低频段频谱许可证](#item-finance-news-6) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [ThinkingBox-Bench：507 个业务流程各跑 20 次，按数据库终态评分](https://www.reddit.com/r/MachineLearning/comments/1x17shf/thinkingbox_solving_an_agent_task_once_vs_solving/) ⭐️ 7.0/10

微软相关作者发布了 ThinkingBox-Bench：一个涵盖 5 个领域（零售、旅行/酒店、汽车保险、数字银行内部 IT、咨询 IT/HR）共 507 个策略约束型业务流程的智能体基准，每个任务都从相同的干净后端独立执行 20 次，因此每个模型有 10,140 次试验。评分不依赖“任务已完成”信号，而是比对后端终态与副作用：507 个任务中 477 个仅按状态评分，30 个还额外检查最终响应的一项狭窄属性。论文、代码、数据集均已公开，基准也已上线 Hugging Face OpenEnv，但原始评测轨迹未发布。作者给出 pass@1、pass@20 与 all-20（20 次全对）三项指标，并强调这些是固定 20 次试验预算下的观测计数，而非对未来可靠性的估计。

reddit · r/MachineLearning · /u/tuhin\_k · 10月9日 00:50

**「背景」** 在智能体评测中，常见做法是用「任务完成」这类代理信号判分：轨迹只要正常收尾、或最终回答看似正确，就记为成功。ThinkingBox 的作者认为这种代理会把实际改坏后端状态的运行误判为通过，因此该基准改为在每次执行结束后直接比对后端数据库终态与副作用，外部报道也以「智能体说完成了，数据库不同意」概括这一取向（tool-2-2）。该基准此前已在微软 Command Line 的报道中公开介绍为覆盖五个业务领域的 507 项可执行任务（tool-2-1）。

**「影响」** 对依赖这类指标做选型的团队来说，发现能力与可重复性的排名差异很大：作者报告 Kimi-K3 的 pass@20 最高，为 93.89%（476/507），但 all-20 仅 13.41%（68/507）；Claude Opus 5 的 pass@20 较低（79.09%），all-20 却达 47.53%（241 个任务）；Qwen3.8-27B 为 89.35% 与 7.50%——按 pass@20 和按 all-20 得出的排行榜几乎相反。作者在 12 个模型、121,680 次有效试验的回溯性消融中发现，79,853 次未通过可执行检查，其中 67.24% 仍干净终止、调用过改状态工具且无最终工具错误，仅凭“完成”代理信号会把它们计为成功，因此评测者需要按终态与副作用验证，或通过 HF OpenEnv 用自有的 507 个任务复跑。作者同时提示，这些是合成重构的企业流程模式而非生产流量，模拟用户是固定 LLM，且失败类别是确定性诊断标签而非因果解释。

<details><summary>参考链接</summary>
<ul>
<li>ThinkingBox: Measuring whether agents finish the job - Command Line</li>
<li>The Agent Said It Was Done. The Database Disagreed. - Hugging Face</li>

</ul>
</details>

**标签**: `#LLM agents`, `#benchmarks and evaluation`, `#agent reliability`, `#stateful workflows`, `#AI research`

---

<a id="item-tech-news-2"></a>
### [OpenAI 封禁俄伊两起利用 ChatGPT 的影响行动](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) ⭐️ 7.0/10

OpenAI 封禁了两个利用 ChatGPT 的隐蔽影响行动。俄罗斯行动疑似通过冒用身份控制拉美一个“研究平台”，传播损害乌克兰声誉及影响当地政治的虚假内容；伊朗行动以 7 个“记者”人设向全球中小网络媒体投稿，并批量生成社交媒体评论。OpenAI 将俄罗斯行动评为影响行动突破量表第 5 类，这是其开始报告以来首次；伊朗行动为第 4 类，产出近 100 篇署名文章。两起行动均结合传统手段与 AI，部分内容进入主流媒体。

telegram · zaihuapd · 10月8日 15:52

**「背景」** OpenAI 此前已发布过针对滥用其模型的隐蔽影响力行动的处置报告，并用“影响行动突破量表”对这类行动按 AI 参与程度分级。据本条来源，俄罗斯行动的评级为第 5 类，是 OpenAI 开始此类报告以来的首次，伊朗行动则为第 4 类。

**「影响」** 对接纳外部投稿的中小型网络媒体来说，这起以 7 个“记者”人设投递、且部分内容已进入主流媒体的行动意味着需要回头核验署名作者的真实身份，并判断已刊发稿件是否要更正或下架。工具结果显示，OpenAI 的影响行动突破量表为 1 至 6 级，过去两年半约 30 起被处置行动几乎都停留在第 1、2 级，即仅在各平台间活动、未真正打入真实社群；此次俄罗斯行动首次被评为第 5 级，说明 AI 辅助的虚假账号内容已有进入真实传播渠道的实例。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://beyondtmrw.org/article/disrupting-ai-enabled-false-front-operations">OpenAI Dark Clark Category 5: Russia, Iran ops | Beyond Tomorrow</a></li>
<li><a href="https://www.ainvest.com/news/openai-category-5-influence-op-reading-banned-io-headline-2610/">OpenAI&#x27;s First Category 5 Influence Op: Reading Past the &quot;Banned IO ...</a></li>

</ul>
</details>

**标签**: `#AI安全`, `#影响力行动`, `#OpenAI`, `#虚假信息`, `#平台治理`

---

<a id="item-tech-news-3"></a>
### [Anthropic 推出 OSS Scanner 免费开源漏洞扫描服务](https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source) ⭐️ 7.0/10

Anthropic 推出 OSS Scanner，面向符合条件的开源项目提供免费、自愿接入的漏洞扫描服务。报告由 Claude 等模型生成，不经人工审核，包含漏洞复现、漏洞说明，并在可能时给出补丁建议，因此可能存在错误。Anthropic 称过去半年发现逾 2.9 万个候选漏洞，人工审查约 6000 个；早期测试的 97 个高危或严重漏洞中，有 85 个符合其披露流程要求。符合条件的项目核心维护者可提交 GitHub PR 申请接入。

telegram · zaihuapd · 10月9日 02:00

**「背景」** OSS Scanner 的做法源自 Anthropic 此前在 Project Glasswing 中使用 Claude 寻找漏洞的经验，这一项目构成了该服务的技术与流程基础。据 Anthropic 介绍，OSS Scanner 会定期用其前沿模型检查已接入的开源代码库，再把结果提供给维护者。

**「影响」** 对符合条件的开源项目，核心维护者可提交 GitHub PR 申请免费接入，获得漏洞复现、说明和补丁建议；但由于报告未经人工审核且可能出错，维护者在采纳补丁或公开披露前需要自行验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source">An opt - in vulnerability - finding service for open - source software</a></li>
<li><a href="https://dev.to/alifar/anthropic-oss-scanner-uses-ai-to-find-vulnerabilities-in-opted-in-open-source-projects-p29">Anthropic OSS Scanner Uses AI to Find Vulnerabilities in Opted - In ...</a></li>

</ul>
</details>

**标签**: `#AI security`, `#open source`, `#vulnerability scanning`, `#Anthropic`, `#Claude`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [标普：中国住宅价格或于 2028 年三季度见底](https://www.cnbc.com/2026/10/08/chinas-real-estate-market-may-be-set-for-a-turnaround-sp-says.html) ⭐️ 8.0/10

标普全球评级在 10 月 8 日发布的报告中称，中国住宅价格可能在 2028 年第三季度见底，而北京、上海等大城市房价最早明年回升；报告将 8 月限制开发商销售未完工房产，以及随后针对总价不超过 150 万元、面积小于 120 平方米的首套房贷款补贴，视为推动市场回稳的关键政策变化。

rss · CNBC Finance · 10月8日 09:27

**「背景」** 此前中国住宅价格自 2021 年峰值已下跌 22%，开发商长期依赖预售模式导致库存高企，标普今年 2 月还认为“房地产复苏遥不可及”。

**「影响」** 摩根士丹利股票分析师 Stephen Cheung 则指出，10 月 1 日至 6 日 25 城二手房销量同比增长 50%，但对首次购房者而言，贷款补贴可能只是把原有购房计划提前，而非创造大量新增需求。

**标签**: `#China real estate`, `#S&amp;P Global Ratings`, `#housing policy`, `#mortgage subsidies`, `#property market forecast`

---

<a id="item-finance-news-2"></a>
### [人社部就新就业形态劳动者权益保障办法征求意见](https://mp.weixin.qq.com/s/saqkOXlhe0wX7qD83vdkRw) ⭐️ 8.0/10

10 月 8 日，人力资源社会保障部发布《新就业形态劳动者权益保障办法（征求意见稿）》，公开征求意见至 11 月 8 日，适用范围包括网约车司机、外卖骑手、网络主播等群体。征求意见稿提出正常劳动报酬不得低于当地最低工资标准、连续工作 4 小时应保障适当休息，并要求停止派单、封禁账号等重大决定不得由算法自动作出，须经人工审核，同时禁止滥用罚款等惩罚性措施；该文件尚处征求意见阶段，未正式生效。

telegram · zaihuapd · 10月8日 09:23

**「背景」** 中国此前对网约车司机、外卖骑手等由平台管理、但不完全符合确立劳动关系情形的劳动者，缺乏专门的劳动法律保障；据新华社报道，这次是首次以规章形式将这类劳动者纳入劳动法律制度保障。该文件目前仍为征求意见稿，公开征求意见至 11 月 8 日。

**「影响」** 据 Sinocism 报道，这是中国首次以部门规章形式规范新就业形态劳动者权益；若该办法最终生效，网约车、外卖配送和直播平台将须调整派单与考核算法、执行报酬下限，并把封号等处置交由人工审核。

<details><summary>参考链接</summary>
<ul>
<li><a href="http://www3.xinhuanet.com/politics/20261008/6e01730616fc4900b2892af1e904914e/c.html">新华社权威快报丨新就业形态劳动者权益保障办法公开征求意见</a></li>
<li>EU-China talks; PBoC on RMB; Measures for protecting the rights ...</li>

</ul>
</details>

**标签**: `#gig economy`, `#labor rights`, `#China regulation`, `#platform algorithms`, `#minimum wage`

---

<a id="item-finance-news-3"></a>
### [Stocks making the biggest moves premarket: Haemonetics, Broadcom, Lululemon, Palantir, Wolfspeed &amp; more](https://www.cnbc.com/2026/10/08/stocks-making-the-biggest-moves-premarket-hae-avgo-lulu-wolf.html) ⭐️ 7.0/10

A premarket movers roundup highlighting several material semiconductor, AI-infrastructure, financing, and earnings developments alongside routine stock moves.

rss · CNBC Finance · 10月8日 12:28

**标签**: `#premarket stock movers`, `#semiconductor financing`, `#AI infrastructure`, `#corporate earnings`, `#Defense Department loan`

---

<a id="item-finance-news-4"></a>
### [FT：OpenAI 9 月底年化收入接近 500 亿美元，比此前报道少约 200 亿](https://www.ft.com/content/b66a9858-f8fb-46cb-b506-44bfe26fca2a?syn-25a6b1a6=1) ⭐️ 7.0/10

据《金融时报》援引投资者获得的财务文件，OpenAI 在 9 月底的年化收入接近 500 亿美元，比此前广泛报道的约 700 亿美元少约 200 亿美元。报道称，差异部分源于计算口径不同——Anthropic 会计入通过 AWS、谷歌云等云伙伴销售的收入，OpenAI 则未计入；OpenAI 拒绝置评。

telegram · zaihuapd · 10月8日 17:22

**「背景」** 此前的广泛报道称 OpenAI 年化收入（把当期收入折算成全年的口径）约 700 亿美元，与投资者文件中接近 500 亿美元的数字存在差距，部分原因在于是否把通过 AWS、谷歌云等云伙伴销售的收入计入口径不同。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.yahoo.com/technology/ai/articles/openai-annualized-revenue-20-billion-195013069.html">OpenAI annualized revenue $20 billion less than previously reported</a></li>
<li><a href="https://digg.com/tech/bi8cxrn1">OpenAI &#x27;s annualized revenue reportedly neared $50 billion at the...</a></li>
<li><a href="https://qz.com/openai-annualized-revenue-50-billion-correction-ai-stocks-100826">OpenAI corrects annualized revenue figure to $50 billion</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#AI revenue`, `#Financial Times`, `#AI market sentiment`, `#private company financials`

---

<a id="item-finance-news-5"></a>
### [美政府以欺诈为由暂停微软绿卡申请资格](https://apnews.com/article/h1b-visa-program-vance-microsoft-e7b3a407f822702b269ee277d21343ea) ⭐️ 7.0/10

特朗普政府宣布暂停微软参与外籍劳工绿卡申请项目，指控其存在欺诈行为；副总统万斯称，微软去年裁员 6000 名美国员工，同时获得 6300 份 H-1B 签证和近 3000 张绿卡。万斯还点名哈佛、耶鲁、MIT 等九所大学涉嫌滥用 J-1 签证项目，微软尚未回应。

telegram · zaihuapd · 10月9日 00:00

**「背景」** 美国雇主为外籍员工申请绿卡时，通常需先通过劳工部的永久劳工证程序，证明招不到合格的美国工人；H-1B 则是临时技术工作签证。特朗普政府此次以欺诈为由暂停微软参与该绿卡项目，副总统万斯称微软去年裁减 6000 名美国员工，却持有 6300 份 H-1B 签证和近 3000 张绿卡；微软随后对相关说法提出异议。

**「影响」** 据路透和《华盛顿邮报》报道，此次暂停同时覆盖新提交和待审的 PERM 申请（即雇主为外籍员工申请永久居留的劳工认证），并涉及 Adobe 及多家 IT 外包公司，还可能影响微软、Adobe 为持其他签证的外籍员工担保永久居留的能力，因此正等待雇主担保绿卡的这些公司在职外籍员工会直接受波及。

<details><summary>参考链接</summary>
<ul>
<li>Microsoft pushes back on Vance&#x27;s H-1B visa claims | The Seattle Times</li>
<li>Microsoft Suspended From Green Card Program as Trump Officials ...</li>
<li>Trump administration freezes green cards for Microsoft, IT firms, probes ...</li>
<li>The Trump administration is suspending Microsoft from a green ...</li>
<li>Trump officials block Microsoft&#x27;s access to program for employee ...</li>

</ul>
</details>

**标签**: `#immigration policy`, `#H-1B visas`, `#Microsoft`, `#labor market`, `#fraud allegations`

---

<a id="item-finance-news-6"></a>
### [SpaceX 宣布拟收购全美低频段频谱许可证](https://x.com/SpaceX/status/2108291133025698301) ⭐️ 7.0/10

SpaceX 宣布已达成协议，拟收购一套覆盖全美的低频段频谱许可证组合；公司未披露交易金额、卖方身份或监管审批时间表。SpaceX 称，将这批频谱与其 Gen2 星座结合后，Starlink Mobile 可为美国民众提供高速移动宽带。

telegram · zaihuapd · 10月9日 01:04

**「背景」** 频谱许可证是移动运营商合法使用无线电波提供手机服务的前提，美国市场目前主要由 AT&amp;T、Verizon 和 T-Mobile 三家占据；路透社和 CNBC 均把 SpaceX 此次收购描述为对这三家运营商的挑战。这并非 SpaceX 首次购入频谱：据 startupfortune 报道，2025 年 9 月 EchoStar 已同意以 170 亿美元（含 85 亿美元现金）向其出售 AWS-4 与 H 频段许可证。

**「影响」** 若交易获批，AT&amp;T、Verizon 和 T-Mobile 等美国传统移动运营商将直面 Starlink Mobile 的竞争——报道称消息公布后三家运营商股价下跌；该交易尚需美国联邦通信委员会（FCC）批准，价格未披露。

<details><summary>参考链接</summary>
<ul>
<li>SpaceX takes aim at US wireless carriers with spectrum acquisition</li>
<li>SpaceX spectrum license hammers shares of AT&amp;T, Verizon and T-Mobile</li>
<li>SpaceX moves to buy nationwide low-band spectrum to rival US carriers</li>
<li>SpaceX takes aim at US wireless carriers with spectrum acquisition</li>
<li>SpaceX spectrum license hammers shares of AT&amp;T, Verizon and T-Mobile</li>
<li>SpaceX announced a deal on Thursday, Oct. 8, to buy ... - Facebook</li>

</ul>
</details>

**标签**: `#SpaceX`, `#Starlink`, `#spectrum acquisition`, `#telecom`, `#satellite broadband`

---