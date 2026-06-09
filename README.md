# data-warehouse-modeling · 数仓建模 Skill

> 融合 Kimball · Inmon · Data Vault 2.0 · 阿里巴巴 OneData · Databricks Medallion · dbt 的数仓建模实战方法论
> A practical DW modeling methodology skill covering Kimball, Inmon, Data Vault 2.0, Alibaba OneData, Databricks Medallion, and dbt

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://makeapullrequest.com)

[English](#english) | [中文](#中文)

---

<a name="english"></a>
## English

A data warehouse modeling methodology skill for AI coding tools (Claude Code, Codex, Cursor, etc.). Not a tool tutorial — a judgment framework forged from production experience.

### What's Covered

- Methodology selection: Kimball, Inmon, Data Vault 2.0, OneData, Medallion (with decision tree)
- Layering architecture: 4 patterns — ODS→DWD→DWS→ADS, Medallion (Bronze→Silver→Gold), dbt, Data Vault
- Dimensional modeling: fact tables, dimension tables, star schema, SCD handling (Type 1/2/3/4/7)
- Metric taxonomy: atomic, derived, composite indicators (OneData methodology)
- Subject area design: 12 common domains with bus matrix template
- Naming conventions: table/field naming rules, data dictionary, data types
- SQL templates: DDL/DML per layer (Hive/Spark), including SCD2 zipper table DML
- Real-time DW: Kafka + Flink + OLAP architecture (with Flink SQL templates)
- Antipatterns: 20 antipatterns ranked P0/P1/P2 with fix priorities
- dbt practices: project structure, materialization strategies, tests, CI/CD
- Cloud platforms: Snowflake, BigQuery, Databricks, Redshift best practices
- Data governance: GDPR, CCPA, PII handling, data classification (L1–L5)
- Documentation: DW design doc template, metric definition template, review checklist

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

Trigger in any AI coding tool by asking DW-related questions, or use `$data-warehouse-modeling` explicitly.

### File Structure

```
skills/data-warehouse-modeling/
├── SKILL.md                              Core entry point
├── references/
│   ├── methodology-comparison.md         Methodology comparison
│   ├── layer-architecture.md             Layer architecture
│   ├── subject-domains.md               Subject areas
│   ├── bus-matrix.md                    Bus matrix template
│   ├── naming-conventions.md            Naming & data dictionary
│   ├── realtime-dw-design.md            Real-time DW design
│   ├── antipatterns.md                  Antipatterns (P0/P1/P2)
│   ├── dbt-practices.md                 dbt engineering guide
│   ├── cloud-platform-practices.md      Cloud platform practices
│   ├── data-governance.md              Data governance & compliance
│   └── dw-doc-standards.md             Documentation standards
└── scripts/
    └── sql-templates.md                 SQL DDL/DML templates
```

### References

- Ralph Kimball — *The Data Warehouse Toolkit* (3rd Edition)
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- Alibaba Data Platform Team — *The Road to Big Data*
- Databricks — Medallion Architecture
- dbt Labs — Best Practices Guide

---

<a name="中文"></a>
## 中文

面向 AI 编程工具（Claude Code、Codex、Cursor 等）的数仓建模技能。不是工具教程，是踩过坑之后积累的判断框架。

### 覆盖内容

- 方法论选择：Kimball、Inmon、Data Vault 2.0、OneData、Medallion（含决策树）
- 分层架构：四种模式 — 国内标准（ODS→DWD→DWS→ADS）、Medallion（Bronze→Silver→Gold）、dbt、Data Vault
- 维度建模：事实表、维度表、星型模型、SCD 处理（一至四种类型）
- 指标体系：原子指标、派生指标、复合指标（OneData 方法论）
- 主题域设计：十二个常见主题域与总线矩阵模板
- 命名规范：表命名、字段命名、词根词典、数据类型
- SQL 模板：各层建表与 ETL 模板（Hive/Spark），含缓慢变化维拉链表处理
- 实时数仓：Kafka + Flink + OLAP 架构（含 Flink SQL 模板）
- 反模式排查：二十个常见反模式，按 P0/P1/P2 分级附修复优先级
- dbt 工程化：项目结构、物化策略、测试、持续集成
- 云平台实践：Snowflake、BigQuery、Databricks、Redshift 最佳实践
- 数据治理：GDPR、CCPA、个人信息保护、数据分级（一至五级）
- 文档规范：数仓设计文档模板、指标定义模板、评审清单

### 为什么需要它

现有的数仓资料要么像教科书（太抽象），要么像工具手册（太细碎）。这个技能填补了中间地带——给 AI 助手注入资深工程师才会说的实话：

- "别急着说绝不——先想清楚你面对的约束"
- "不要选最好的方法论，选你团队能落地的那一个"
- "SCD3 教科书里每本都有，实际项目中我一次没见过谁用"

### 安装

```bash
# Claude Code
cp -r skills/data-warehouse-modeling ~/.claude/skills/

# Codex
cp -r skills/data-warehouse-modeling ~/.codex/skills/

# Cursor 或其他工具
cp -r skills/data-warehouse-modeling ~/.agents/skills/
```

兼容 [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) 规范，可直接放入其 `skills/` 目录。

### 使用方式

在 AI 编程工具中直接提问数仓相关问题即可触发，或使用 `$data-warehouse-modeling` 手动引用。

### 参考来源

- Ralph Kimball — *The Data Warehouse Toolkit*（第 3 版）
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- 阿里巴巴数据平台部 — *大数据之路*
- Databricks — Medallion Architecture
- dbt Labs — 最佳实践指南

---

## License

MIT License © 2026
