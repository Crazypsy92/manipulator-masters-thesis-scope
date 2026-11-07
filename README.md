# Robotics Thesis Research Pipeline

面向机械臂、机器人视觉、无序抓取、6D 位姿估计、抓取生成、接触评价和运动规划研究的端到端科研 Skill。

本仓库将三项原本独立的能力整合为一个连续流水线：

**单篇论文深度精读 → 多篇论文横向比较 → 硕士论文方法选型与研究规划。**

## 核心设计

- **证据先行：** 重要结论必须能追溯到论文页码、章节、图表或公式。
- **标准化交接：** 每篇论文形成独立的标准化记录，作为横向比较的正式输入。
- **增量更新：** 新增论文只处理新增材料，并更新受影响的比较和选型；默认不重新精读旧论文。
- **去重与版本管理：** 使用 SHA-256、DOI、标题/作者/年份识别重复文件和论文版本。
- **研究适配：** 将论文方法与用户的相机、机械臂、夹爪、仿真平台、算力和实验条件逐项核对。
- **实验闭环：** 强制考虑基线、对照、消融、失败案例，并区分仿真与真机证据。

## Repository Contents

| Path | Purpose |
|---|---|
| [`SKILL.md`](SKILL.md) | 主 Skill：完整阶段流程、门禁、证据规范、增量更新机制 |
| [`references/paper-record-schema.md`](references/paper-record-schema.md) | 单篇精读到横向比较的标准化交接结构 |
| [`assets/literature_manifest.template.json`](assets/literature_manifest.template.json) | 文献库状态、哈希、版本和分析状态模板 |
| [`assets/change_log.template.md`](assets/change_log.template.md) | 每轮增量更新记录模板 |
| [`docs/research/reference_papers_and_research_plan.md`](docs/research/reference_papers_and_research_plan.md) | 已有参考论文、图表、软件平台与研究规划汇总 |
| [`docs/research/thesis_framework_and_implementation_plan.md`](docs/research/thesis_framework_and_implementation_plan.md) | 已有硕士论文框架、创新点和实施计划 |

## Single-paper Deep Reading Outputs

When one paper is supplied and the user asks for a full reading, the default is **single-paper mode**. It produces four required Chinese Markdown files for independent review:

| File | Purpose |
|---|---|
| `01_one_page_card.md` | One-page overview of the question, gap, method, key findings, novelty, and limitations |
| `02_deep_reading_notes.md` | Full reading notes: research logic, method reconstruction, figures/tables, software and simulation roles, experiments, critique, and research reuse |
| `03_claim_evidence_index.md` | Claim–Evidence–Location traceability with PDF pages, sections, figures, tables, equations, and confidence |
| `04_standardized_paper_record.md` | Structured record used as the formal input for cross-paper comparison and thesis planning |

A fifth file, `05_missing_evidence.md`, is created only when the PDF, figures, supplementary materials, software usage, or essential parameters contain unresolved gaps.

Templates:
- [One-page card](templates/paper_records/01_one_page_card.md)
- [Deep-reading notes](templates/paper_records/02_deep_reading_notes.md)
- [Claim-evidence index](templates/paper_records/03_claim_evidence_index.md)
- [Standardized paper record](templates/paper_records/04_standardized_paper_record.md)
- [Missing evidence (optional)](templates/paper_records/05_missing_evidence.md)

The substantive content of these files is written in Chinese. File names and paths remain English.

## Pipeline

1. `Stage 0` — 文献接收、清单、去重和可读性检查。
2. `Stage 1` — 快速筛选与技术分类。
3. `Stage 2` — 单篇论文深度精读、图表盘点、软件用途审计和证据索引。
4. `Stage 3` — 多篇论文横向比较、实验可比性审查和研究空白分析。
5. `Stage 4` — 结合真实课题约束进行方法适配与选型。
6. `Stage 5` — 硕士论文框架、图表规划、工作量分级和实验矩阵。
7. `Stage 6` — 总体验收、证据审计和下一步任务。

## Incremental Update Policy

Adding papers does **not** trigger a full re-reading of the existing library.

For each update, the workflow reads the manifest and change log, fingerprints incoming files, classifies them as `NEW`, `DUPLICATE`, `POSSIBLE_DUPLICATE`, `REVISION`, or `UNCHANGED`, and processes only the new or changed material.

Existing deep-reading records remain reusable. Only relevant comparison groups, research-gap conclusions, method-selection decisions, or thesis plans are updated. Old papers are rechecked only when a concrete evidence conflict, missing field, version change, or user request requires it; the reason and scope must be logged.

## Language and Markdown

- Repository metadata, paths, file names, and identifiers: English.
- Research analysis and substantive documents: Chinese.
- Obsidian-compatible Markdown is preferred for research notes.
- Use `##` as the highest heading level in generated research notes.
- Preserve Obsidian heading links such as `[[#Section|Display text]]` and native callouts.

## Research Integrity

This workflow does not equate author claims with verified facts. It separates source facts, author interpretations, cross-paper synthesis, analytical judgments, and hypotheses requiring validation. It does not rank numerical results across incompatible datasets or protocols, and it never treats simulation visualization as real-robot validation.