# data-warehouse-modeling · 数仓建模 Skill

> 融合 Kimball · Inmon · Data Vault 2.0 · 阿里巴巴 OneData · Databricks Medallion · dbt 的数仓建模实战方法论

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://makeapullrequest.com)

[English](#english) | [中文](#中文)

---

<a name="english"></a>
## English

A data warehouse modeling methodology skill that teaches AI coding tools (Claude Code, Codex, Cursor, etc.) to systematically approach DW modeling tasks. Not a tool tutorial — a judgment framework forged from production experience.

### What's Covered

- **Methodology selection** — Kimball, Inmon, Data Vault 2.0, OneData, Medallion (with decision tree)
- **Layering architecture** — 4 patterns: Chinese Standard (ODS→DWD→DWS→ADS), Medallion (Bronze→Silver→Gold), dbt, Data Vault
- **Dimensional modeling** — fact tables, dimension tables, star schema, SCD handling (Type 1/2/3/4/7)
- **Metric taxonomy** — atomic, derived, composite indicators (OneData methodology)
- **Subject area design** — 12 common domains with bus matrix template
- **Naming conventions** — table/field naming rules, data dictionary, data types
- **SQL templates** — DDL/DML per layer (Hive/Spark), including SCD2 zipper table DML
- **Real-time DW** — Kafka + Flink + OLAP architecture (with Flink SQL templates)
- **Antipatterns** — 20 antipatterns ranked P0/P1/P2 with fix priorities
- **dbt practices** — project structure, materialization strategies, tests, CI/CD
- **Cloud platforms** — Snowflake, BigQuery, Databricks, Redshift best practices
- **Data governance** — GDPR, CCPA, PIPL, PII handling, data classification (L1–L5)
- **Documentation** — DW design doc template, metric definition template, review checklist

### Why This Skill

Existing DW modeling resources are either textbooks (too abstract) or tool documentation (too specific). This skill bridges the gap — it gives AI assistants the practical decision framework a senior data engineer would apply:

- "Before you say 'never cross layers', understand your constraints first"
- "Don't pick the best methodology — pick the one your team can execute"
- "SCD3 appears in every textbook but I've never seen it used in production"

### Installation

```bash
# Claude Code
cp -r skills/data-warehouse-modeling ~/.claude/skills/

# Codex
cp -r skills/data-warehouse-modeling ~/.codex/skills/

# Cursor / other tools
cp -r skills/data-warehouse-modeling ~/.agents/skills/
```

Compatible with [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) conventions — drop into its `skills/` directory directly.

### Usage

Trigger in any AI coding tool by asking DW-related questions:
- "Design a DW layering architecture for our e-commerce platform"
- "How should I model this metric?"
- "Review my DWD table design"
- Or explicitly: `$data-warehouse-modeling`

### File Structure

```
skills/data-warehouse-modeling/
├── SKILL.md                              Core entry point (149 lines)
├── references/
│   ├── methodology-comparison.md         Methodology comparison (144 lines)
│   ├── layer-architecture.md             Layer architecture (120 lines)
│   ├── subject-domains.md               Subject areas (35 lines)
│   ├── bus-matrix.md                    Bus matrix template (92 lines)
│   ├── naming-conventions.md            Naming & data dictionary (141 lines)
│   ├── realtime-dw-design.md            Real-time DW design (120 lines)
│   ├── antipatterns.md                  Antipatterns P0/P1/P2 (107 lines)
│   ├── dbt-practices.md                 dbt engineering guide (192 lines)
│   ├── cloud-platform-practices.md      Cloud platform practices (183 lines)
│   ├── data-governance.md              Data governance & compliance (195 lines)
│   └── dw-doc-standards.md             Documentation standards (142 lines)
└── scripts/
    └── sql-templates.md                 SQL DDL/DML templates (343 lines)
```

### References

- Ralph Kimball — *The Data Warehouse Toolkit* (3rd Edition)
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- Alibaba Data Platform Team — *The Road to Big Data* (大数据之路)
- Databricks — Medallion Architecture
- dbt Labs — Best Practices Guide

---

<a name="中文"></a>
## 中文

面向 AI 编程工具（Claude Code / Codex / Cursor 等）的数仓建模 skill。不是某个 DW 工具的教程，是踩过坑之后的判断框架。

### 覆盖内容

- **方法论选择** — Kimball、Inmon、Data Vault 2.0、OneData、Medallion（含决策树）
- **分层架构** — 4 种模式：国内标准（ODS→DWD→DWS→ADS）、Medallion（Bronze→Silver→Gold）、dbt、Data Vault
- **维度建模** — 事实表、维度表、星型模型、SCD 处理（Type 1/2/3/4/7）
- **指标体系** — 原子指标、派生指标、复合指标（OneData 方法）
- **主题域设计** — 12 个常见主题域 + 总线矩阵模板
- **命名规范** — 表/字段命名规则、词根词典、数据类型
- **SQL 模板** — 各层 DDL/DML（Hive/Spark），含 SCD2 拉链表 DML
- **实时数仓** — Kafka + Flink + OLAP 架构（含 Flink SQL 模板）
- **反模式** — P0/P1/P2 分级，20 个实战反模式附排查优先级
- **dbt 实践** — 项目结构、物化策略、测试、CI/CD
- **云平台** — Snowflake、BigQuery、Databricks、Redshift 最佳实践
- **数据治理** — GDPR、CCPA、PIPL、PII 处理、数据分级（L1–L5）
- **文档规范** — 数仓设计文档模板、指标定义模板、评审清单

### 为什么需要这个 Skill

现有的数仓建模资料要么像教科书（太抽象），要么像工具文档（太细节）。这个 skill 填补了中间地带——给 AI 助手注入资深数据工程师的判断力：

- "别急着说绝不——先想清楚你面对的约束"
- "不要选最好的方法论，选你团队能落地的"
- "SCD3 教科书里常见，实际项目中我从来没见过谁用"

### 安装

```bash
# Claude Code
cp -r skills/data-warehouse-modeling ~/.claude/skills/

# Codex
cp -r skills/data-warehouse-modeling ~/.codex/skills/

# Cursor / 其他工具
cp -r skills/data-warehouse-modeling ~/.agents/skills/
```

兼容 [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) 规范，可直接放入其 `skills/` 目录。

### 使用方式

在 AI 编程工具中直接提问即可触发：
- 「帮我设计电商平台的分层架构」
- 「这个指标怎么建模」
- 「帮我评审这张 DWD 表的设计」
- 或手动引用：`$data-warehouse-modeling`

### 参考来源

- Ralph Kimball — *The Data Warehouse Toolkit*（第 3 版）
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- 阿里巴巴数据平台部 — *大数据之路*
- Databricks — Medallion Architecture
- dbt Labs — Best Practices Guide

---

## License

MIT License © 2026
