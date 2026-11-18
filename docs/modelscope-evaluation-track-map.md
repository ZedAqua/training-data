# ModelScope 评测分轨

总合集：[`evaluation-datasets`](https://modelscope.cn/collections/Zed2000/evaluation-datasets)

细分类：

- [`model-eval`](https://modelscope.cn/collections/Zed2000/model-eval)：模型本身的知识、推理、代码、长上下文、指令遵循和结构化输出能力。
- [`agent-eval`](https://modelscope.cn/collections/Zed2000/agent-eval)：搜索、工具调用、环境交互、任务完成、研究流程和 Coding Agent 能力。

## model-eval

- `aime-eval-2025-2026`：数学推理
- `bfcl-v4-eval`：函数调用和工具 schema 遵循的模型能力
- `livecodebench-v6-eval`：代码生成
- `ifeval-ifbench-multichallenge`：多约束指令遵循
- `gpqa-diamond`：高难科学推理
- `fineval-eval`：闭卷金融知识

## agent-eval

- `xbench-deepsearch-2510`：多步深度搜索
- `browsecomp-eval`：开放域浏览和深度搜索
- `seal0-eval`：通用搜索 Agent
- `swebench-verified-eval`：Coding Agent 仓库修复
- `spreadsheetbench2-eval`：表格和金融建模 Agent
- `finance-agent-v1-v2`：金融分析 Agent
- `tau3-eval`：多轮工具调用和业务状态变更
- `finsearchcomp-t2t3`：金融搜索 Agent
- `deepresearch-bench-eval`：深度研究 Agent

## 分轨规则

如果标准协议只给模型固定输入并直接读取模型输出，归入 `model-eval`。如果结果依赖搜索、MCP、工具 schema、沙箱、业务状态、仓库操作或多步环境交互，归入 `agent-eval`。

同一个 benchmark 可以存在两个协议轨：模型侧分数和 Hermes/Agent E2E 分数必须分别记录，不能混成一个总分。
