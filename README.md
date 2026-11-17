# training-data

训练数据工程仓库，负责从来源数据到可训练 SFT/RL 样本的处理流程、质量门槛和版本记录。

## 职责

- 维护原始数据登记、来源 revision、授权记录和数据 manifest。
- 实现清洗、去重、去污染、筛选、格式转换和质量检查。
- 维护 SFT、RL、Harbor task、mock/snapshot task 的样本 schema。
- 记录数据版本、文件 hash、处理代码版本和生成关系。
- 为训练运行时提供稳定、可校验的数据发布包。

## 不负责

- 不实现训练框架、GPU launcher 或 checkpoint 管理。
- 不维护评测 runner 和评分器。
- 不把未授权数据、隐藏答案或密钥写入 Git。

## 数据约定

原始数据、清洗后的训练集、评测题目、gold 和大文件统一存放在 ModelScope；GitHub 仓库只保存处理代码、schema、manifest、hash 和下载/校验脚本。

ModelScope 的分类约定如下：

- `evaluation-datasets`：评测题目、评测输入、gold 和评测所需的来源快照。
- `training-datasets`：原始训练来源、去污染候选、SFT 数据、RL 数据和生成轨迹。
- 每个 benchmark 或数据来源单独建立 Dataset，合集只负责分类，不把多个数据集拼成一个大仓库。

## 上传前检查

上传任何新数据前，先在 ModelScope 搜索现有 Dataset，并记录搜索关键词、候选数据集、revision、许可、字段和样本规模。

1. 如果现有 Dataset 满足来源、版本、许可和字段要求，直接固定 revision 使用，并在 manifest 中记录引用关系。
2. 如果现有 Dataset 只有部分满足要求，记录差异和处理步骤；只有派生结果确实需要共享时才新建 Dataset。
3. 如果没有符合条件的 Dataset，再新建 Dataset，并在 README 和 manifest 中保存来源、下载时间、原始 hash、处理代码版本和数据许可。

所有 Dataset 的 README 使用 ModelScope YAML 元数据，至少填写 `license`、`task`、`language` 和 `tags`。评测数据与训练数据不能通过同一个 Dataset 或同一个 manifest 混用。

具体模板见 [`docs/modelscope-dataset-policy.md`](docs/modelscope-dataset-policy.md)。

## 计划目录

```text
pipelines/     数据处理流水线
schemas/       任务、轨迹、验证结果 schema
validators/    结构、事实、工具调用和质量校验
manifests/     来源、版本、hash 和发布清单
tasks/         自建训练任务定义
scripts/       可重复执行的命令行入口
docs/          数据契约和授权说明
```
