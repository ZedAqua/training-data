# ModelScope 评测数据集注释清单

以下内容可直接复制到对应 ModelScope Dataset 的 README 或数据集介绍页。所有数据集均为私有评测数据，只用于模型回归和能力诊断，不作为训练数据。

## 1. AIME 2025–2026

- **用途**：数学竞赛推理能力回归，观察训练后数学保护项是否退化。
- **内容**：AIME 2025 和 AIME 2026 的结构化题目、整数答案、题目 ID，以及 PDF、来源 README、HTML 和 manifest 等来源快照。
- **来源**：`math-ai-org/aime25`、`math-ai-org/aime26`；结构化数据使用已固定的 Hugging Face revision。
- **评测维度**：数学推理、最终答案准确率。
- **使用限制**：仅评测，不得用于 SFT、RL 或拒绝采样。
- **建议标签**：`evaluation`、`mathematics`、`aime`、`reasoning`

## 2. Seal-0

- **用途**：通用搜索与研究型问答回归，重点观察搜索后答案是否有帮助、是否正确。
- **内容**：Seal-0 评测题目和原始任务字段，保留本项目使用的 2026-11-04 快照。
- **来源**：`vtllms/sealqa`。
- **评测维度**：搜索问答正确性、帮助性、拒答和无效回答比例。
- **使用限制**：题目用于评测，不得改写后进入训练集。
- **建议标签**：`evaluation`、`search`、`question-answering`、`agent`

## 3. FinSearchComp T2/T3

- **用途**：金融搜索和历史调查能力回归。
- **内容**：FinSearchComp T2 和 T3 主任务文件，覆盖历史查询、复杂调查、Global 与 Greater China 子集。本 Dataset 不包含被排除的 AkShare 替代主 split。
- **来源**：`randomtutu/FinSearchComp`，revision `55b6393fcf3c8f749ba5a69a70b20d4ef6f67caf`。
- **评测维度**：金融事实检索、期间和口径判断、答案证据与引用质量。
- **使用限制**：仅用于固定版本回归；不要与其他 FinSearchComp 版本混合计算。
- **建议标签**：`evaluation`、`finance`、`financial-search`、`deep-research`

## 4. BrowseComp

- **用途**：开放域深度浏览和多步搜索能力回归。
- **内容**：已解密的核心任务输入和题目字段；加密原始题源不在此 Dataset 中。
- **来源**：`openai/simple-evals`，revision `652c89d0ca9df547706735883097e9537d40dc47`。
- **评测维度**：网页检索、跨来源整合、复杂问题回答和搜索预算控制。
- **使用限制**：题面仅供评测，不能把题目或改写版本用于训练。
- **建议标签**：`evaluation`、`browse`、`web-search`、`deep-research`

## 5. xbench DeepSearch 2510

- **用途**：多步深度搜索能力回归。
- **内容**：xbench 2510 的已解密核心任务输入；2505/2510 的加密原始来源不直接上传。
- **来源**：`xbench-ai/xbench-evals`，revision `17c562192cc7e62215bfb98b65e9f8806fb95504`。
- **评测维度**：多跳检索、证据整合、长链路搜索和最终答案质量。
- **使用限制**：保持 2510 版本独立报分，不与 2505 合并。
- **建议标签**：`evaluation`、`deep-search`、`web-search`、`research-agent`

## 6. τ3 Agent

- **用途**：工具调用 Agent 的闭环行为回归。
- **内容**：airline、retail、telecom 三个业务域的任务文件，打包在 `tau3-tasks.zip` 中。
- **来源**：tau2-bench / τ3 adapter，revision `v1.0.0`，包含本项目固定修订。
- **评测维度**：工具选择、多步状态变更、失败恢复、任务终态和用户模拟器交互。
- **使用限制**：任务需要配合对应环境和工具 schema 执行；不能只把题目文本当作普通问答数据。
- **建议标签**：`evaluation`、`agent`、`tool-use`、`tau-bench`、`multi-turn`

## 7. Finance Agent v1/v2

- **用途**：金融分析 Agent 工作流回归。
- **内容**：Finance Agent v1 和 v2 的公开任务文件，分别保存为 `finance-agent-v1.csv` 和 `finance-agent-v2.csv`。
- **来源**：`vals-ai/finance-agent`，分别固定 v1 和 v2 revision。
- **评测维度**：金融任务规划、工具使用、信息整合和最终交付质量。
- **使用限制**：v1、v2 分开统计，不要混成一个版本；Dataset 中的历史 `public.csv` 是首次上传遗留文件。
- **建议标签**：`evaluation`、`finance`、`financial-agent`、`tool-use`

## 8. GPQA Diamond

- **用途**：专家级科学推理能力回归。
- **内容**：GPQA Diamond 题目和选项字段，保留本项目使用的题目文件。
- **来源**：`idavidrein/gpqa`，仓库 revision `83022cefff930aea54f654c0b282e74b9eeda5c`。
- **评测维度**：物理、化学、生物等领域的高难度知识和推理。
- **使用限制**：仅评测，不得用于训练或教师拒绝采样。
- **建议标签**：`evaluation`、`science`、`reasoning`、`gpqa`

## 9. IFEval / IFBench / MultiChallenge

- **用途**：通用多约束指令遵循能力回归。
- **内容**：IFEval multiturn、IFBench test/multiturn 和 MultiChallenge test 四个 parquet 文件。
- **来源**：`allenai/IFBench`、`ScaleAI/MultiChallenge`，使用项目固定 revision。
- **评测维度**：格式约束、多个同时生效的指令、跨轮指令保持和复杂约束满足。
- **使用限制**：不同 benchmark 文件保持独立统计；不能把四个文件合并成一个官方分数。
- **建议标签**：`evaluation`、`instruction-following`、`multi-turn`、`constraints`

## 10. SpreadsheetBench 2

- **用途**：表格操作、金融建模和表格调试能力回归。
- **内容**：SpreadsheetBench 2 核心任务、模板和验证所需的必要附件，打包在 `SpreadsheetBench-2-core.zip` 中。
- **来源**：`RUCKBReasoning/SpreadsheetBench-2`，revision `a7bdc2d358e052d35a94768e1f487c0d9e9c0011`。
- **评测维度**：单元格结果、公式、金融模型、模板填充和调试修复。
- **使用限制**：运行时需要固定重算环境；不得把模型输出或运行结果当作题目文件。
- **建议标签**：`evaluation`、`spreadsheet`、`financial-modeling`、`table-agent`

## 11. DeepResearch Bench

- **用途**：深度研究报告生成能力回归。
- **内容**：DeepResearch Bench 核心任务和必要参考数据，打包在 `deepresearch-data.zip` 中。
- **来源**：`Ayanami0730/deep_research_bench`，revision `f2735b5c3636759c22f9e936c0232de8bf545b67`。
- **评测维度**：研究报告质量、事实正确性、证据引用和多步研究流程。
- **使用限制**：RACE、FACT 等评分维度保持原协议，不直接合并成单一总分。
- **建议标签**：`evaluation`、`deep-research`、`report-generation`、`citation`

## 12. FinEval

- **用途**：金融知识和金融任务能力回归。
- **内容**：Salesforce FinEval finance parquet，以及 SUFE FinEval 压缩数据包。
- **来源**：`Salesforce/FinEval`、`SUFE-AIFLM-Lab/FinEval`，具体 revision 见 Dataset manifest。
- **评测维度**：中文金融知识、金融概念理解和金融问答。
- **使用限制**：许可和可再分发条件仍需复核；不得把 FinQA、FinanceIQ 或 FinBen 排除项混入本 Dataset。
- **建议标签**：`evaluation`、`finance`、`financial-knowledge`、`chinese`

## 13. BFCL v4

- **用途**：函数调用和工具 schema 遵循能力回归。
- **内容**：BFCL v4 核心任务和必要工具定义，打包在 `bfcl-data.zip` 中。
- **来源**：`ShishirPatil/gorilla`，项目冻结的 BFCL v4 快照。
- **评测维度**：函数选择、参数结构、并行调用、多轮调用和工具调用准确率。
- **使用限制**：需要配合 BFCL scorer 和对应工具协议运行；不能只看自由文本答案。
- **建议标签**：`evaluation`、`function-calling`、`tool-use`、`bfcl`

## 14. SWE-bench Verified

- **用途**：Coding Agent 修复真实软件仓库问题的能力回归。
- **内容**：SWE-bench Verified 核心任务和运行所需的精选附件，打包在 `swebench-verified-core.zip` 中。
- **来源**：`swebench-verified@1.0`，revision `86723674f04e4209ac479d0fb75d9d9f44b4377e`。
- **评测维度**：代码定位、补丁生成、测试通过和仓库级任务完成。
- **使用限制**：需要隔离的代码执行环境；题目、仓库快照和测试许可必须按上游规则使用。
- **建议标签**：`evaluation`、`coding-agent`、`software-engineering`、`swe-bench`

## 15. XSTest / HarmBench

- **用途**：安全拒答、过度拒答和有害请求边界回归。
- **内容**：XSTest 核心题目和 HarmBench 核心数据，分别打包为 `xstest-core.zip` 和 `harmbench-data.zip`。
- **来源**：`paul-rottger/xstest`、`centerforaisafety/HarmBench`。
- **评测维度**：应拒请求、应答请求、过度拒答、越狱边界和安全分类。
- **使用限制**：仅限授权评测人员访问；许可和安全数据使用规则仍需遵循上游要求。
- **建议标签**：`evaluation`、`safety`、`refusal`、`over-refusal`

## 16. LEDGER

- **用途**：金融文档和财务数据推理能力回归。
- **内容**：LEDGER 评测 parquet 文件，包含金融文档任务和验证所需字段。
- **来源**：`artefactory/LEDGER`，revision `fa3d8b7666b22b3359cd6d57ed8a769d1dc57c09`。
- **评测维度**：财报文档理解、金融事实抽取、数值推理和证据定位。
- **使用限制**：金融原文和 OCR/文档许可需要按上游规则使用；不得把评测题直接转成训练样本。
- **建议标签**：`evaluation`、`finance`、`financial-documents`、`document-understanding`

## 17. LiveCodeBench v6

- **用途**：模型代码生成能力回归。
- **内容**：LiveCodeBench v6 test6 核心题目 JSONL。
- **来源**：`LiveCodeBench/code_generation_lite`，Hugging Face revision `0fe84c3912ea0c4d4a78037083943e8f0c4dd505`。
- **评测维度**：算法题理解、代码生成、测试通过和时间切片后的新题泛化。
- **使用限制**：题目和隐藏测试只用于评测；执行时需要固定编译器、测试器和资源限制。
- **建议标签**：`evaluation`、`code-generation`、`programming`、`livecodebench`

## 18. LongMemEval

- **用途**：长期记忆和跨会话信息保持能力回归。
- **内容**：`longmemeval_s_cleaned.json` 和 `longmemeval_oracle.json` 两个核心任务文件。
- **来源**：`xiaowu0162/longmemeval-cleaned`，revision `98d7416c24c778c2fee6e6f3006e7a073259d48f`。
- **评测维度**：记忆写入、检索、时间关系、多会话信息整合和长期事实保持。
- **使用限制**：不同 split 独立报告；不要把 oracle 文件当作普通训练数据。
- **建议标签**：`evaluation`、`long-term-memory`、`memory`、`multi-session`

## 19. SkillsBench

- **用途**：Skill/plugin 使用、选择和任务完成能力回归。
- **内容**：SkillsBench 核心任务、任务注册表、taxonomy 和必要 skill 资产，打包在 `skillsbench-core.zip` 中。
- **来源**：SkillsBench，revision `f860ecf02ef53412a030f8661c83d644b739ff01`。
- **评测维度**：是否选择正确 Skill、Skill 调用后的任务完成、干扰 Skill 处理和工具协同。
- **使用限制**：需要配合 SkillsBench runner 和固定 Skill 版本执行；核心包不等于完整上游仓库。
- **建议标签**：`evaluation`、`skills`、`plugins`、`agent`

## 暂缓和排除项

- **RULER**：已保留源代码，但生成版本、seed 和上下文配置尚未冻结，暂不建立最终评测 Dataset。
- **FinEval/FinBen 组合项**：按当前项目范围排除，不与独立 FinEval Dataset 混用。
