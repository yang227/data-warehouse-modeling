# data-warehouse-modeling · 数仓建模技能

🌐 简体中文 | [English](#english)

> 🧱 **数仓建模不只是建几张表** — 融合 Kimball · Inmon · Data Vault 2.0 · 阿里 OneData · Databricks Medallion · dbt 的实战方法论。教 AI 助手在分层架构、维度建模、指标体系、命名规范、反模式排查等场景下做出专业判断。不是一个 DW 工具教程，是踩过坑之后积累的判断框架。

A practical DW modeling methodology skill for AI coding tools — covering Kimball, Inmon, Data Vault 2.0, Alibaba OneData, Databricks Medallion, and dbt. Teaches AI assistants the professional judgment framework a senior data engineer applies in production.

<!-- 效果对比 -->
<table>
<tr><td>

**没有这个 skill 时：**
```
你：帮我设计一个电商数仓
AI：好的，我建一个 DW 库，把所有表放进去...
    建议用星型模型，维度和事实表分开...
你：分层呢？命名规范呢？SCD 怎么处理？
    OD S 表直接关联会出现什么问题？
```

</td><td>

**有这个 skill 之后：**
```
你：帮我设计一个电商数仓
AI：先问几个关键问题：
    ——数据规模多大？团队多少人？
    ——需要实时吗？审计要求有吗？
    → 5 人以下团队选 Kimball，先出东西再说
    → 金融场景加 Data Vault 整合层
    → 分层：ODS 原样 → DWD 清洗 → DWS 汇总 → ADS 应用
    → 交易、用户、流量三个核心域先建
    确认后给出每层 DDL 模板
```

</td></tr>
</table>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://makeapullrequest.com)

### 技能规模

| 方法论 | 架构模式 | 覆盖主题 | 反模式 | SQL 模板 |
|:---:|:---:|:---:|:---:|:---:|
| **5** | **4** | **12** 个主题域 | **20** 个 P0/P1/P2 分级 | 各层 DDL/DML |

---

## 这是什么？

市面上数仓建模的资料很多：要么是教科书（"星型模型由一张事实表和多张维度表组成"），要么是工具手册（"Snowflake 的 CLUSTER BY 语法"）。中间地带——**告诉 AI 助手什么时候该做什么选择**——是空白的。

这个 skill 填补的就是这块空白。它不是教你"星型模型长什么样"，而是教 AI 在什么约束条件下该选哪个方法论、什么场景下可以跨层引用、指标口径打架时先解决什么问题。

### 和 superpowers-zh 的关系

本项目 skill 结构兼容 [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) 规范，可作为其生态中的一个独立 skill 使用。superpowers-zh 覆盖 AI 编程通用工作流（TDD、调试、代码审查），本项目覆盖数仓建模领域。

| 维度 | superpowers-zh | data-warehouse-modeling |
|------|---------------|------------------------|
| 定位 | AI 编程通用工作方法论 | 数仓建模领域方法论 |
| Skills 数 | 20 | 1（聚焦深） |
| 覆盖 | 需求、设计、实现、测试、审查 | 分层、建模、指标、命名、规范 |
| 安装 | `npx superpowers-zh` | 手动复制到 skills 目录 |
| 语言 | 中文 | 中文（技术术语保留英文） |

---

## 覆盖内容

### 建模方法论选择
不是罗列方法论定义，是告诉你什么时候该选哪个、什么时候不该选哪个：
- **Kimball** — 团队 5 人以下，先出东西再说
- **Data Vault 2.0** — 金融医疗，审计需求。5 人以下别碰
- **OneData** — 公司能推标准、需要指标体系
- **Medallion** — 湖仓一体、已有 Delta Lake
- **Inmon** — 企业级，但建设周期 6-12 个月，扛得住的再选

### 分层架构设计
四套主流模式对比：国内标准（ODS→DWD→DWS→ADS）、Medallion（Bronze→Silver→Gold）、dbt（staging→marts）、Data Vault（Raw Vault→Info Marts）。附五家企业实战对比。

### 维度建模
四步法不是教条，关键是顺序——先选业务过程再选维度。事实表设计选择（事务/周期快照/累积快照）、SCD 策略（SCD3 教科书里每本都有，实际项目中一次没见过谁用）。

### 指标体系
派生子指标公式，但重点不在这——重点在"原子指标的定义权必须收归数据团队"。口径分歧是组织问题，不是技术问题。

### 命名规范与词根词典
表名格式、字段后缀、数据类型、增量标记、词根词典。不是为了好看，是为了让新来的人三天内看懂表结构。

### SQL 建模模板
每层全套 DDL + DML 模板：ODS 建表（分区+生命周期）、DWD 明细宽表（ETL 清洗）、DIM（全量快照+SCD2 拉链表更新）、DWS 汇总（多维聚合）、ADS 应用（指标计算）。

### 实时数仓
Kafka + Flink CDC + OLAP。Lambda vs Kappa 选型、Watermark 乱序处理、维度关联三种方案、Flink SQL 双流 JOIN 模板。

### 反模式识别
20 个反模式，P0（必须修复）/ P1（短期修）/ P2（建议修）三级。附排查优先级：P0 先查主键唯一性和粒度一致性。

### dbt 工程化
项目结构、物化策略、增量模型、测试规范、CI/CD。

### 云平台实践
Snowflake、BigQuery、Databricks、Redshift 四种平台的最佳实践，跨平台 SQL 迁移对照表。

### 数据治理
GDPR、CCPA、PIPL 合规。PII 脱敏策略（删除/掩码/哈希/令牌化）、删除权实现、数据分级（L1-L5）、各平台行级/列级安全实现。

### 文档模板
数仓设计文档模板、指标定义文档模板、建模评审清单。

---

## 文件结构

```
skills/data-warehouse-modeling/
├── SKILL.md                             核心入口（149 行）
├── references/
│   ├── methodology-comparison.md        五种方法论对比 + 决策树
│   ├── layer-architecture.md            分层架构 + 五家企业对比
│   ├── subject-domains.md              十二个主题域
│   ├── bus-matrix.md                   总线矩阵 + 维度 DDL
│   ├── naming-conventions.md           命名规范 + 词根词典
│   ├── realtime-dw-design.md           实时数仓 + Flink SQL
│   ├── antipatterns.md                 二十个反模式（P0/P1/P2）
│   ├── dbt-practices.md                dbt 工程化完整指南
│   ├── cloud-platform-practices.md     云平台实践 + 跨平台 SQL 对照
│   ├── data-governance.md             数据治理 + GDPR/CCPA
│   └── dw-doc-standards.md            文档模板 + 评审清单
└── scripts/
    └── sql-templates.md                各层 DDL/DML 模板
```

---

## 安装

### AI 编程工具

| 工具 | 安装方式 |
|------|---------|
| Claude Code | `cp -r skills/data-warehouse-modeling ~/.claude/skills/` |
| Codex | `cp -r skills/data-warehouse-modeling ~/.codex/skills/` |
| Cursor | `cp -r skills/data-warehouse-modeling ~/.cursor/skills/` |
| 其他工具 | `cp -r skills/data-warehouse-modeling ~/.agents/skills/` |

### 配合 superpowers-zh

直接放入 superpowers-zh 的 `skills/` 目录即可生效。

---

## 使用方式

在 AI 编程工具中直接提问即可触发：
- 「帮我设计电商平台的分层架构」
- 「这个指标怎么定义口径」
- 「帮我评审这张 DWD 表的设计」
- 手动引用：`$data-warehouse-modeling`

---

## 参考来源

- Ralph Kimball — *The Data Warehouse Toolkit*（第 3 版）
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- 阿里巴巴数据平台部 — *大数据之路*
- Databricks — Medallion Architecture
- dbt Labs — Best Practices Guide

---

## 贡献

欢迎参与！报告问题、改进文档、新增内容都可以。

好的 skill 内容应该：
- 教 AI 助手**怎么判断**，不是罗列概念
- 有实战语气——踩过的坑比理论更值钱
- 有明确的步骤和示例，AI 加载后能直接执行

欢迎提 Issue 讨论想法。

---

## 许可证

MIT License — 自由使用，商业或个人均可。

---

<div align="center">

**🧱 让 AI 助手学会数仓建模：不只是建表，是踩过坑之后积累的判断框架**

[Star 本项目](https://github.com/yang227/data-warehouse-modeling) · [提交 Issue](https://github.com/yang227/data-warehouse-modeling/issues)

</div>

---

<a name="english"></a>
## English

A data warehouse modeling methodology skill for AI coding tools. Teaches AI assistants the professional judgment framework a senior data engineer applies in production — not a tool tutorial, not a textbook summary.

### What's Inside

- **Methodology selection** — Kimball, Inmon, Data Vault 2.0, OneData, Medallion with a practical decision tree
- **Layering architecture** — 4 patterns with real company comparisons (Alibaba, Meituan, NetEase, etc.)
- **Dimensional modeling** — fact tables, dimensions, SCD strategies (and which ones you never actually use)
- **Metric taxonomy** — atomic, derived, composite indicators (OneData methodology)
- **Subject areas** — 12 common domains with bus matrix template
- **Naming conventions** — table/field rules, data dictionary with root words
- **SQL templates** — DDL/DML for every layer (Hive/Spark)
- **Real-time DW** — Kafka + Flink + OLAP with Flink SQL examples
- **Antipatterns** — 20 antipatterns ranked P0/P1/P2 with fix priorities
- **dbt practices** — project structure, tests, CI/CD
- **Cloud platforms** — Snowflake, BigQuery, Databricks, Redshift
- **Data governance** — GDPR, CCPA, PII masking, data classification
- **Documentation** — design doc template, metric definition template, review checklist

### Installation

```bash
# Claude Code
cp -r skills/data-warehouse-modeling ~/.claude/skills/

# Codex
cp -r skills/data-warehouse-modeling ~/.codex/skills/

# Cursor / other tools
cp -r skills/data-warehouse-modeling ~/.agents/skills/
```

Compatible with [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) — drop into its `skills/` directory directly.

### Usage

Trigger by asking DW-related questions in any AI coding tool, or use `$data-warehouse-modeling` explicitly.

### References

- Ralph Kimball — *The Data Warehouse Toolkit* (3rd Edition)
- Bill Inmon — *Building the Data Warehouse*
- Dan Linstedt — *Building a Scalable Data Warehouse with Data Vault 2.0*
- Alibaba Data Platform Team — *The Road to Big Data*
- Databricks — Medallion Architecture
- dbt Labs — Best Practices Guide

---

## License

MIT License © 2026
