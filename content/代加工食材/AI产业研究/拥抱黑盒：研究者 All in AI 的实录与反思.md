
# 拥抱黑盒：研究者 All in AI 的实录与反思

## 核心观点
AI 正在以不可逆的速度重写人类的工作方式。
要真正用好 AI，必须放弃对确定性的执念，接受黑盒的本质——
潘多拉的盒子已经打开，一切都回不去了。

---

## Agent 的本质：黑盒外的操作系统

LLM 本质是**概率推断机器**（next-token predictor），没有真正的逻辑或记忆，
这也是它产生幻觉（hallucination）的根本原因。

Agent = LLM（推理核心）+ Harness（控制外壳）。
Harness 负责调用工具、追加上下文、循环执行，直到任务完成。

整个系统和操作系统高度相似：

| Agent 概念 | OS 类比 |
|---|---|
| LLM | CPU（概率处理器）|
| 上下文窗口（Context Window）| RAM |
| MCP（模型上下文协议）| 驱动协议（USB/POSIX）|
| Skills（技能包）| 已安装的 App |
| Subagents（子代理）| 多任务进程调度 |

> 关键结论：决定上限的往往不是 Harness 挂了多少花活，
> 而是底层内核（模型本身）够不够强。
>
> 佐证：[Pi Coding Agent](https://mariozechner.at/posts/2025-11-30-pi-coding-agent/)
> 仅用 <1000 tokens 的系统提示词、4个工具，
> 在 Terminal-Bench 上与复杂系统表现相当。

---

## Coding Agent：变化最剧烈的战场

**为什么 Coding 最先被 AI 攻克？**
- 反馈闭环强：编译器、运行时、测试套件能快速暴露错误
- 可复用 patterns 多：LLM 容易学习并拼接常见解法
- 文档丰富且可机器消化：给 Agent "读文档"的工具效果立竿见影

**转折点**：2025 年 12 月 Claude Opus 4.5 发布，
手搓代码及 AI autocomplete 彻底成为"古法"。

**开发者与 AI 的角色演化路径：**
1. 初级程序员：自己写码，AI 辅助
2. 资深程序员：审查 AI 产出，负责 review
3. **产品经理（当前可达目标）**：不看代码，只和 AI 资深程序员沟通需求
4. 用户（终极形态）：随口说需求，和 AI PM 沟通

> 注意：没有任何编程背景直接跳到"用户阶段"，
> 等于把 AI 当许愿机，无法判断结果对错。
> 合理目标是先达到"稍微懂实现的 PM 状态"。
> （参考：[Steve Yegge 的 Developer Agent Evolution Model](https://justin.abrah.ms/blog/2026-01-08-yegge-s-developer-agent-evolution-model.html)）

---

## Agent 控制流：Thin Agent 模式

**核心问题**：在系统中，到底谁掌握控制流（Control Flow）？

| 范式 | 思路 | 优势 | 劣势 |
|---|---|---|---|
| Code-driven（代码驱动）| 状态机写死，Agent 只是工具 | 稳定不跑偏 | 不够灵活 |
| Agent-driven（胖代理）| 规划和调用都交给 Agent | 灵活易扩展 | 容易幻觉、跳步骤 |
| **Thin Agent（瘦代理）**| 代码管状态与验收，LLM 管局部推理 | 兼顾灵活与确定性 | 架构设计更复杂 |

> 业界共识正在收束到 **Thin Agent 模式**：
> 代码是不可违背的 Contract，LLM 是契约内部的推理引擎。
> 编译器 / linter / test runner 过了，状态才更新；没过就打回继续改。
>
> 参考案例：
> [Stripe Minions - Blueprints](https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents-part-2)
> [Ramp Background Agent](https://builders.ramp.com/post/why-we-built-our-background-agent)

---

## 数学：最后的堡垒（但也在动摇）

**为什么数学还没被攻克？**
- 没有现成的"裁判"：不像代码有编译器，数学证明的对错需要人来判断
- 状态空间搜索巨大：即使推理速度快 10 倍，依然需要搜索正确证明路径
- 验证错误成本高：理解 AI 给出的错误证明，往往比自己从头推导更费时

**突破口：形式化数学（Lean 4）作为数学的"编译器"**

一旦 Lean 能给出对错反馈，AI 就获得了和写代码一样的闭环。

近期里程碑：
- DeepSeek-Prover-V2（2025）：MiniF2F 基准通过率 88.9%
- [Harmonic Aristotle](https://github.com/harmonic-ai/IMO2025)：2025 年 IMO 金牌，全部经 Lean 形式化验证
- [AxiomProver](https://axiommath.ai/territory/from-seeing-why-to-checking-everything)：Lean 4 解决 2025 年 Putnam 竞赛全部 12 题
- GPT-5.2 Pro（2026.1）：生成 3 个 Erdős 开放问题证明，Terence Tao 验证接受

> 结论：由于缺乏完整的形式化证明 AI 框架，
> 数学研究者暂时安全——但也安全不了多久了。

---

## 成为 AI Native：重构工作方式

### 信息输入：语音优先
- 人说话速度 >> 打字速度，阅读速度 >> 听语音速度
- 目标：**语音输入 + 视觉输出**
- 工具推荐：[Typeless](https://www.typeless.com/)（跨平台）、豆包输入法（手机）
- 传统 ASR 只转写文字；新一代工具能理解意图、剥离口语废话

### 外脑与知识库
- 用 AI 监视 feeds、过滤噪音、生成每日摘要
- 个人知识库：Obsidian（纯 MD 文件）+ RAG
- 决策面板：[Neat](https://github.com/ndbroadbent/neat)（Nathan Broadbent 的方案）
- 最终目标：AI 越了解你，你越少需要主动沟通

### 学习方式：AI Native
- 不需要先读完文档再动手——直接让 Agent 在真实项目中用起来
- 让 AI 读文档后再教你：解释开源项目架构、翻译论文为可理解语言
- 学习瓶颈从"信息获取"转变为"能提出多好的问题"

---

## 效率悖论：越高效，越疲惫

Agentic Coding 压缩了所有等待间隙（编译/测试/部署），
大脑持续处于高决策状态，反而比以前更累。

执行成本趋近于零 → 大脑不断产生新 idea → 停不下来 →
结果：一晚上交付比以前一周更多的量，但身心俱疲。

> 这是 AI 时代被严重低估的问题："效率内卷"。

---

## 安全：与黑盒共处的代价

**核心风险**：Prompt Injection（提示词注入）
— 让 AI 读外部内容时，内容本身可能包含恶意指令，AI 可能照单全收。

**基本防线：**
- **最小权限原则**：分阶段开放，只给当前任务所需权限
- **沙盒与审计**：敏感操作（发邮件、删文件、推代码）需人工确认或留日志
- **分离信任域**：处理外部输入的 Agent ≠ 拥有系统权限的 Agent

> 这些措施会降低效率——这就是与黑盒共处的代价。
> 风险永远不可能降到零。

---

## 宏观判断：智力商品化与世界重构

- **智力溢价崩溃**：AI 以趋近于零的边际成本输出认知决策，
  专业技能将像自来水一样成为廉价基础设施
- **幽灵 GDP**：未来大量生产力由机器生产、在机器间流转，
  红利流向算力所有者和资本
- **中间商瓦解**：SaaS、平台本质是"将摩擦货币化"，
  Agent 跨越系统壁垒后，这些中间商将被摧毁
  > "Every app is just a very slow API now"
  > —— Peter Steinberger，[Lex Fridman 播客](https://lexfridman.com/peter-steinberger/)

> 参考：[Citrini Research - 2028 全球智力危机推演](https://www.citriniresearch.com/p/2028gic)
>
> 核心结论：即便 AI 不再取得任何进展，
> 只要算力成本持续下降，现有技术已具备替代多数白领认知工作的能力。
> **现在阻止多数人被替代的理由仅仅是惯性。**

---

## 延伸思考
- Thin Agent 架构会不会也是过渡形态，被更强的模型直接跨越？
- 形式化数学（Lean）成熟后，纯理论研究者的不可替代性在哪里？
- "效率内卷"有没有解法，还是人类只能靠自律来对抗？
- 智力商品化后，教育体系的核心价值应该重新定义为什么？

  
> 来源：[拥抱黑盒：一个研究者 All in AI 的实录与反思 - Chao Xu，知乎](https://zhuanlan.zhihu.com/p/2012947554678096288)

---

