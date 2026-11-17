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

原始数据、清洗后的训练集、评测题目、gold 和大文件统一存放在 ModelScope；GitHub 仓库只保存处理代码、schema、manifest、hash 和下载/校验脚本。ModelScope 数据集地址、组织权限和 revision 规则将在下一步补充。

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
