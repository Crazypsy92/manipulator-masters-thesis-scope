# Robotics Thesis Research Pipeline

一个整合“单篇论文深度精读 → 多篇论文横向比较 → 硕士论文方法选型与研究规划”的科研 Skill。

## 安装
将整个 `robotics-thesis-research-pipeline` 文件夹放入 Codex/Agent 可识别的 skills 目录，并确保 `SKILL.md` 位于该文件夹根目录。

## 核心特点
- 一个 Skill，分阶段执行，不再维护三个彼此独立的 Skill。
- 每篇论文生成标准化记录，作为横向比较的正式输入。
- 横向比较结果继续传递给方法适配、创新点审查、论文框架和实验规划。
- 证据定位贯穿全流程；明确区分原文事实、作者解释、跨论文归纳和分析推断。
- 增量新增论文时只更新受影响的阶段。

## 主要文件
- `SKILL.md`：完整流程和执行规则。
- `references/paper-record-schema.md`：单篇精读到横向比较的标准交接结构。