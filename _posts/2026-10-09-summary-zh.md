---
layout: default
title: "Horizon Summary: 2026-10-09 (ZH)"
date: 2026-10-09
lang: zh
---

> 从 41 条内容中筛选出 7 条重要资讯。

---

**科技新闻**
1. [ThinkingBox-Bench：用 507 个有状态工作流评估智能体可靠性](#item-tech-news-1) ⭐️ 7.0/10
2. [OpenAI 封禁俄伊两起 ChatGPT 影响行动](#item-tech-news-2) ⭐️ 7.0/10
3. [Anthropic 推出 OSS Scanner 开源漏洞扫描服务](#item-tech-news-3) ⭐️ 7.0/10

**财经新闻**
1. [标普：中国楼市低迷或近尾声，全国房价预计 2028 年三季度见底](#item-finance-news-1) ⭐️ 7.0/10
2. [文件显示 OpenAI 年化收入约 500 亿美元，低于此前报道的 700 亿](#item-finance-news-2) ⭐️ 7.0/10
3. [美政府以欺诈为由暂停微软绿卡申请资格](#item-finance-news-3) ⭐️ 7.0/10
4. [SpaceX 宣布协议拟收购全美低频段频谱许可证](#item-finance-news-4) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [ThinkingBox-Bench：用 507 个有状态工作流评估智能体可靠性](https://www.reddit.com/r/MachineLearning/comments/1x17shf/thinkingbox_solving_an_agent_task_once_vs_solving/) ⭐️ 7.0/10

微软作者在 r/MachineLearning 发布 ThinkingBox-Bench，用 507 个策略条件业务工作流（覆盖零售、旅行/酒店、汽车保险、数字银行内部 IT、咨询 IT/HR 五个领域）评估 AI 智能体；每个任务从相同的干净后端独立运行 20 次，每个模型共 10,140 次试验，477 个任务仅按最终数据库状态评分，30 个还检查最终回答的一个狭窄属性，错误、缺失或多余的效果均判失败。该基准同时报告 pass@1、pass@20（20 次中至少成功一次）和 all-20（20 次全部成功）；论文图 1b 的 9 个模型中，Kimi-K3 的 pass@20 为 93.89%（476/507）、all-20 仅 13.41%（68/507），Claude Opus 5 分别为 79.09% 和 47.53%（241 个任务），Qwen3.8-27B 为 89.35% 和 7.50%，按 pass@20 与 all-20 排出的榜单几乎相反。在 12 个模型、121,680 次有效试验的回顾性消融中，79,853 次未通过可执行检查的失败有 67.24% 仍干净终止；失败类别中错误字段值占 77.61%、多余副作用占 43.30%、缺失必需效果占 25.36%（类别可重叠）。作者指出任务为合成重建而非生产流量，all-20 是固定试验预算下的观测计数而非未来可靠性的保证，模拟用户为固定 LLM，原始评估轨迹未发布；论文、代码与数据集公开，并可通过 Hugging Face OpenEnv 运行。

reddit · r/MachineLearning · /u/tuhin\_k · 10月9日 00:50

**「背景」** 这项基准出自 2026 年 8 月发布在 arXiv 的论文《One Success Isn&\#x27;t Reliability: Thinkingbox, a Sandbox and Benchmark for Agents in Stateful Business Workflows》（编号 2608.19741），论文把 Thinkingbox 描述为可复用的沙箱，用于可验证的工具—智能体—用户交互，Thinkingbox-bench 则是其针对有状态业务流程的可执行基准（tool-2-1、tool-2-2）。这篇 Reddit 帖子是作者对该论文与配套环境的介绍，而非独立第三方的评测报告。之所以需要这样的设计，是因为此前智能体评测通常只报告单次尝试的成功率（pass@1），把“跑通一次”当作可靠性，而本文要检验的是这种成功率在重复执行、且以后端数据库终态和副作用为判据时会剩下多少。

**「影响」** 对把 agent 接入真实后台系统的团队来说,这套基准的直接后果是:单次成功率不足以作为上线验收指标——论文的消融显示,在 79,853 次失败尝试中有 67.24% 是在没有最终工具错误、还调用了状态变更工具的情况下“干净”结束的,只监控会话是否正常收尾的做法会把它们记作完成。该基准已通过 Hugging Face OpenEnv 公开,团队可用自己的模型跑这 507 个任务,用终态数据库校验替代完成式代理指标;arXiv 摘要同样强调,多轮补全信息、遵守领域策略并协调相互依赖的工具才是这类工作的难点,而非给出看似合理的回复或合法工具调用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2608.19741">[2608.19741] One Success Isn&#x27;t Reliability: Thinkingbox, a ...</a></li>
<li><a href="https://arxiv.org/html/2608.19741">One Success Isn’t Reliability: Thinkingbox, a Sandbox and ...</a></li>
<li><a href="https://www.explainx.ai/blog/microsoft-thinkingbox-agent-benchmark-stateful-2026">ThinkingBox: Microsoft Agent Benchmark Explained (2026 ...</a></li>
<li><a href="https://arxiv.org/abs/2608.19741">[2608.19741] One Success Isn&#x27;t Reliability: Thinkingbox, a ...</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#LLM evaluation`, `#benchmarks`, `#agent reliability`, `#stateful workflows`

---

<a id="item-tech-news-2"></a>
### [OpenAI 封禁俄伊两起 ChatGPT 影响行动](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) ⭐️ 7.0/10

OpenAI 表示已封禁两起利用 ChatGPT 的隐蔽影响行动。俄罗斯行动被指冒用身份控制拉美一个“研究平台”，传播损害乌克兰声誉并影响当地政治的内容，被 OpenAI 评为影响行动突破量表第 5 类，这是其开始报告以来首次。伊朗行动使用 7 个“记者”人设向全球中小网络媒体投稿，并批量生成社交媒体评论，被评为第 4 类，产出近 100 篇署名文章。OpenAI 称两起行动都结合传统手段与 AI，且部分内容已进入主流媒体。

telegram · zaihuapd · 10月8日 15:52

**「背景」** OpenAI 此前已多次披露并处置利用其模型的国家背景隐蔽影响行动。其官方页面曾说明封禁俄罗斯来源账号，这些账号用 AI 推广一个冒充以色列智库的机构和一份称赞俄罗斯、批评西方的“主权指数”；Dark Reading 的汇总则称 OpenAI 已识别并干扰来自中国、伊朗、以色列和俄罗斯的五个此类行动。

**「影响」** 对接收投稿和转载的媒体机构而言，来源称伊朗行动以 7 个“记者”人设向中小网络媒体投稿，且部分内容进入主流媒体；这意味着审核作者身份、核查原始来源比只看文本质量更关键。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.darkreading.com/threat-intelligence/openai-disrupts-5-ai-powered-state-backed-influence-ops">OpenAI Disrupts 5 AI -Powered, State-Backed Influence Ops</a></li>
<li><a href="https://openai.com/index/disrupting-malicious-uses-of-ai-influence-campaign-russia/">Disrupting a new covert influence campaign from Russia | OpenAI</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#AI misuse`, `#influence operations`, `#disinformation`, `#AI safety`

---

<a id="item-tech-news-3"></a>
### [Anthropic 推出 OSS Scanner 开源漏洞扫描服务](https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source) ⭐️ 7.0/10

Anthropic 推出 OSS Scanner，为符合条件的开源项目提供免费、自愿接入的漏洞扫描服务，报告由 Claude 等模型生成、不经人工审核，包含漏洞复现与说明，并在可能时给出补丁建议，因此可能存在错误。Anthropic 称过去半年发现逾 2.9 万个候选漏洞，其中人工审查约 6000 个；早期测试的 97 个高危或严重漏洞中有 85 个符合其披露流程要求。符合条件项目的核心维护者可通过提交 GitHub PR 申请接入。

telegram · zaihuapd · 10月9日 02:00

**「背景」** OSS Scanner 的推出建立在 Anthropic 此前“Project Glasswing”的经验之上：该项目用 Claude 寻找漏洞，而新服务把这一方法产品化为面向开源生态的定期扫描（tool-2-1）。据 Anthropic 的申请说明，服务采取自愿接入，项目核心维护者需向 Anthropic 的 OSS Scanner GitHub 仓库提交 PR，Anthropic 会逐案评估项目对基础设施和用户安全的关键影响，并人工核实申请人是否为项目核心维护者（tool-2-3）。

**「对维护者的实际负担」** 对获准接入的开源项目维护者而言，OSS Scanner 的报告由模型生成、不经人工审核，且官方已提示可能存在错误，因此漏洞复现、说明与补丁建议仍需维护者自行验证和分类，误报与补丁质量的风险由接收方承担。开源社区此前已出现大量低质量 AI 生成漏洞报告（所谓“AI slop”）加重维护负担的情况，接入方宜提前为筛查和验证留出人力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/research/launching-opt-in-vuln-finding-service-for-open-source">An opt-in vulnerability-finding service for open-source ...</a></li>
<li><a href="https://kju.ai/story/anthropic-announces-opt-in-oss-vulnerability-scanner">Anthropic announces opt-in OSS vulnerability scanner | Kju</a></li>
<li><a href="https://github.com/ossf/wg-vulnerability-disclosures/issues/178">AI -SLOP: Develop best current practises for Open Source ...</a></li>
<li><a href="https://analyticsindiamag.com/ai-features/ai-slop-is-choking-open-source-and-frustrating-developers">AI Slop is Choking Open Source , and Frustrating Developers | AIM</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#open-source security`, `#vulnerability scanning`, `#AI security`, `#LLM`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [标普：中国楼市低迷或近尾声，全国房价预计 2028 年三季度见底](https://www.cnbc.com/2026/10/08/chinas-real-estate-market-may-be-set-for-a-turnaround-sp-says.html) ⭐️ 7.0/10

标普全球评级 10 月 8 日发布的报告称，中国持续多年的房地产低迷可能已接近尾声，全国住宅价格预计在 2028 年第三季度见底，而北京、上海等一线城市房价最早可能在明年回暖。

rss · CNBC Finance · 10月8日 09:27

**「背景」** 今年 2 月标普还认为，高企的未售住房让中国楼市复苏“遥不可及”；此后中国在 8 月限制开发商销售未完工住房，9 月又推出面向首套房购房者的房贷利率补贴（房款不超过 150 万元人民币、面积不超过 120 平方米），标普认为这是判断转变的主因，而中国住宅价格自 2021 年峰值已下跌 22%。

**「影响」** 标普分析师 Edward Chan 指出，限制预售将使开发商更谨慎拿地、减少新项目开发，这虽会压低其收入，但有助于消化供应过剩的楼市；摩根士丹利分析师 Stephen Cheung 则提醒，房贷补贴更多是把原计划的购房提前，而非带来大量新增需求。

**标签**: `#China property market`, `#S&amp;P Global Ratings`, `#housing policy`, `#mortgage subsidies`, `#market outlook`

---

<a id="item-finance-news-2"></a>
### [文件显示 OpenAI 年化收入约 500 亿美元，低于此前报道的 700 亿](https://www.ft.com/content/b66a9858-f8fb-46cb-b506-44bfe26fca2a?syn-25a6b1a6=1) ⭐️ 7.0/10

据《金融时报》报道，投资者获得的财务文件显示，OpenAI 截至 9 月底的年化收入接近 500 亿美元，比此前广泛报道的约 700 亿美元少约 200 亿美元。报道称差异部分源于会计口径不同：Anthropic 计入通过 AWS、谷歌云等云伙伴销售的收入，OpenAI 未计入；OpenAI 拒绝置评。

telegram · zaihuapd · 10月8日 17:22

**「背景」** 此前有报道称 OpenAI 的年化收入约为 700 亿美元，而该公司更早向投资者释放的信号也高于此次披露的数字。这一差距部分源于计算口径不同：Anthropic 会把通过 AWS、谷歌云等云伙伴销售的收入计入自身营收，OpenAI 则不计入。

**「市场影响」** 消息公布后，纳斯达克指数下跌，人工智能相关股票走低，原因是市场此前已将算力需求持续增长的预期计入股价，收入预期被高估的迹象可能引发对相关投资链条的抛售。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/business/openais-annualized-revenue-20-billion-less-than-previously-signaled-ft-reports-2026-10-08/">OpenAI&#x27;s September annualized revenue nears $50 billion, less ...</a></li>
<li><a href="https://techcrunch.com/2026/10/08/openais-revenue-is-reportedly-20-billion-less-than-previously-projected/">OpenAI’s revenue is reportedly $20 billion less than ...</a></li>
<li><a href="https://www.forbes.com/sites/josipamajic/2026/03/25/openai-and-anthropic-count-revenue-differently-and-investors-are-looking-into-it/">OpenAI And Anthropic Count Revenue Differently, And ... - Forbes</a></li>
<li><a href="https://www.zerohedge.com/markets/nasdaq-tumbles-after-ft-reports-openai-revenues-disappointing">Nasdaq Tumbles After FT Reports OpenAI Revenues ... | ZeroHedge</a></li>
<li><a href="https://verifiedinvesting.com/blogs/live-show-recap/trading-the-close-market-recap-10-08-2026-openai-revenue-shock-sparks-tech-volatility-10-year-yield-oil-silver-bitcoin-levels-to-watch">Trading The Close Market Recap - 10/08/ 2026 : OpenAI Revenue ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/07/stock-market-today-live-updates-.html">Stock market news for Oct. 8, 2026</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#AI industry`, `#annualized revenue`, `#financial disclosure`, `#market sentiment`

---

<a id="item-finance-news-3"></a>
### [美政府以欺诈为由暂停微软绿卡申请资格](https://apnews.com/article/h1b-visa-program-vance-microsoft-e7b3a407f822702b269ee277d21343ea) ⭐️ 7.0/10

特朗普政府以涉嫌欺诈为由，暂停微软参与外籍劳工绿卡申请项目。副总统万斯称，微软去年裁减 6000 名美国员工，却获得 6300 份 H-1B 签证和近 3000 张绿卡；这些指控目前尚未得到微软回应。

telegram · zaihuapd · 10月9日 00:00

**「背景」** 此次被暂停的是 PERM 劳工认证项目——雇主为外籍员工申请永久居留（绿卡）所需的认证；这是联邦政府针对 H-1B 签证项目欺诈与滥用问题调查的一部分，微软等多家大型科技公司均被暂停参与该项目。

**「影响」** 绿卡申请由雇主担保提交，微软被暂停资格意味着其持 H-1B 签证的员工暂时无法由公司推进永久居留申请，只能等待或另寻途径。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://abcnews.com/Politics/vance-suspends-microsoft-green-card-program-crack-alleged/story?id=137100899">Vance suspends Microsoft from a green card program to crack ...</a></li>
<li><a href="https://finance.yahoo.com/economy/policy/articles/microsoft-suspended-green-card-program-153952894.html?fr=sycsrp_catchall">Microsoft Is Suspended From Green Card Program. Vance Accuses ...</a></li>
<li><a href="https://www.nbcnews.com/politics/trump-administration/microsoft-suspended-green-cards-h-1b-visa-j-1-visa-vance-rcna602314">Microsoft Facing Fraud Claims, Green Card Program ...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/oct/08/jd-vance-microsoft-visa-workers-green-card-suspension">Microsoft suspended from applying for green cards for H-1B ...</a></li>

</ul>
</details>

**标签**: `#Microsoft`, `#H-1B visa`, `#green card`, `#immigration policy`, `#tech labor`

---

<a id="item-finance-news-4"></a>
### [SpaceX 宣布协议拟收购全美低频段频谱许可证](https://x.com/SpaceX/status/2108291133025698301) ⭐️ 7.0/10

SpaceX 宣布一项协议，拟收购覆盖全美的低频段频谱许可证组合。公司称，将该频谱与 Gen2 星座结合后，Starlink Mobile 可为美国民众在任何地点提供高速移动宽带；公告未披露交易金额、卖方身份、时间表及监管审批细节，交易尚未完成。

telegram · zaihuapd · 10月9日 01:04

**「背景」** Starlink 此前主要依靠与运营商的合作来提供卫星直连手机（Direct to Cell）服务，并已与 EchoStar 旗下 Boost Mobile 达成长期商业协议，让后者用户接入其下一代直连服务。低频段频谱传播距离远、穿墙能力强，是广覆盖移动网络的基础资源，因此收购全国性频谱意味着 SpaceX 从依赖合作转向自建美国移动网络。

**「影响」** 若 Starlink Mobile 按公司设想绕过传统地面基站提供移动宽带，美国现有无线运营商 AT&amp;T、Verizon 和 T-Mobile 将面对一个新的全国性竞争者；CNBC 报道称，消息公布后这三家公司的股价下跌。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/business/media-telecom/spacex-acquire-spectrum-that-enables-starlink-mobile-services-2026-10-08/">ReutersSpaceX to acquire spectrum that enables Starlink ...</a></li>
<li><a href="https://ir.echostar.com/news-releases/news-release-details/echostar-announces-spectrum-sale-and-commercial-agreement-spacex">EchoStar Announces Spectrum Sale and Commercial Agreement ...</a></li>
<li><a href="https://www.reuters.com/business/media-telecom/spacex-acquire-spectrum-that-enables-starlink-mobile-services-2026-10-08/">SpaceX takes aim at US wireless carriers with spectrum ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/08/spacex-spectrum-license-att-verizon-tmobile.html">SpaceX spectrum license hammers shares of AT&amp;T ... - CNBC</a></li>

</ul>
</details>

**标签**: `#SpaceX`, `#Starlink`, `#spectrum acquisition`, `#US telecom`, `#satellite broadband`

---