# ModelScope 数据集管理规范

## 分类

| 合集 | 内容 | 示例 |
| --- | --- | --- |
| `evaluation-datasets` | 评测题目、评测输入、gold、来源快照和评测 manifest | `aime-eval-2025-2026` |
| `training-datasets` | 原始训练来源、去污染候选、SFT、RL 和教师轨迹 | 后续按来源或阶段建立 |

合集只做分类。每个 benchmark、来源或训练阶段单独建立 Dataset，避免不同许可、版本和用途混在同一个数据集里。

## 上传前决策

上传前必须先查 ModelScope。搜索记录至少包括：

- 关键词和筛选条件；
- 找到的候选 Dataset 与 owner；
- revision 或 commit；
- 许可和可再分发条件；
- 字段、split、样本数量和文件格式；
- 选择复用、派生或新建的理由。

符合来源、版本、许可、字段和质量要求时，固定现有 Dataset 的 revision 直接使用。现有 Dataset 只有部分符合时，保留差异说明和处理记录。没有符合条件的 Dataset 时，才创建新的 Dataset。

## Dataset README 最小元数据

```yaml
---
license: apache-2.0
task: text-generation
language:
- en
tags:
- evaluation
---
```

实际值必须以数据集真实许可、任务和语言为准。README 还要说明数据用途、来源、处理步骤、字段、split、禁止用途和复现方法。

## Manifest 最小字段

```json
{
  "dataset_id": "Zed2000/example-eval-v1",
  "collection": "evaluation-datasets",
  "revision": "<modelscope-revision>",
  "source": [{"name": "<source>", "revision": "<source-revision>"}],
  "files": [{"path": "<path>", "sha256": "<sha256>", "records": 0}],
  "license": "<license>",
  "created_at": "YYYY-MM-DD"
}
```

`revision`、文件 hash 和处理代码版本共同确定数据内容。大文件、gold、checkpoint 和运行输出放 ModelScope；GitHub 只保存 manifest、代码和校验入口。
