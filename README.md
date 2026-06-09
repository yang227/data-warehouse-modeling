# data-warehouse-modeling · 数仓建模 Skill

> 融合 Kimball · Inmon · Data Vault 2.0 · 阿里 OneData · Databricks Medallion · dbt 的数仓建模实战方法论

面向 AI 编程工具（Claude Code / Codex / Cursor 等）的数仓建模 skill，教 AI 助手系统化地完成数据仓库建模工作。

## 这是什么？

一个教 AI 助手"怎么建模"的方法论 skill。不是某个 DW 工具的教程，而是踩过坑之后的判断框架。

覆盖内容：
- **5 种方法论** 对比选择（Kimball / Inmon / Data Vault 2.0 / OneData / Medallion）
- **4 种分层架构**（国内标准 ODS→DWD→DWS→ADS / Medallion / dbt / Data Vault）
- **维度建模**（事实表、维度表、星型模型、SCD 处理）
- **指标体系**（OneData 原子指标 / 派生指标 / 复合指标）
- **主题域划分**（12 个常见主题域 + 总线矩阵模板）
- **命名规范**（表/字段命名、词根词典、数据类型）
- **SQL 模板**（各层 DDL/DML，Hive/Spark）
- **实时数仓**（Kafka + Flink + OLAP 架构）
- **反模式识别**（P0/P1/P2 分级，20 个实战反模式）
- **dbt 工程化**（项目结构、测试、CI/CD）
- **云平台实践**（Snowflake / BigQuery / Databricks / Redshift）
- **数据治理**（GDPR / CCPA / PII 处理 / 数据分级）
- **文档模板**（设计文档、指标定义、评审清单）

## 安装

### 方式一：手动安装（推荐）

将 `skills/data-warehouse-modeling/` 复制到你的 skill 目录：

```bash
# Claude Code
cp -r skills/data-warehouse-modeling ~/.claude/skills/

# Codex
cp -r skills/data-warehouse-modeling ~/.codex/skills/

# Cursor / 其他工具
cp -r skills/data-warehouse-modeling ~/.agents/skills/
```

### 方式二：配合 superpowers-zh 使用

本项目 skill 结构兼容 [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh) 规范，可直接放入其 `skills/` 目录。

## 文件结构

```
skills/data-warehouse-modeling/
├── SKILL.md                              核心入口（149 行）
├── references/
│   ├── methodology-comparison.md         方法论对比（144 行）
│   ├── layer-architecture.md             分层架构（120 行）
│   ├── subject-domains.md                主题域（35 行）
│   ├── bus-matrix.md                     总线矩阵（92 行）
│   ├── naming-conventions.md             命名+词根词典（141 行）
│   ├── realtime-dw-design.md             实时数仓（120 行）
│   ├── antipatterns.md                   反模式 P0/P1/P2（107 行）
│   ├── dbt-practices.md                  dbt 工程化（192 行）
│   ├── cloud-platform-practices.md       云平台实践（183 行）
│   ├── data-governance.md                数据治理（195 行）
│   └── dw-doc-standards.md               文档模板（142 行）
└── scripts/
    └── sql-templates.md                  SQL 模板（343 行）
```

## 使用方式

在 AI 编程工具中触发：
- 直接问数仓相关问题（"帮我设计一张表"、"数仓怎么分层"、"这个指标怎么建模"）
- 或用 `$data-warehouse-modeling` 手动引用

## 特色

- **实战语气**，不是教科书摘要——踩过坑之后的判断框架
- **核心约束带例外说明**——不教条，告诉你什么场景可以变通
- **方法论选择从现实约束出发**——"团队 5 人以下别碰 Data Vault"
- **反模式分级**——P0 必须修、P1 短期修、P2 建议修，附排查优先级
- **全球通用 + 中国实践**——同时覆盖阿里 OneData 和 Snowflake/Databricks

## 致谢

参考来源：
- Ralph Kimball《The Data Warehouse Toolkit》
- Bill Inmon《Building the Data Warehouse》
- Dan Linstedt《Building a Scalable Data Warehouse with Data Vault 2.0》
- 阿里巴巴《大数据之路》
- Databricks Medallion Architecture
- dbt Labs Best Practices

## 许可证

MIT License
