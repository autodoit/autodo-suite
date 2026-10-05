# autodo-suite 项目文档

## 概述

本目录记录 autodo 多仓库体系中 AOK 事务、Copilot Skill、Copilot Agent 的适配状态与开发进展。

## 文档索引

| 文档 | 说明 |
|---|---|
| [aok-affair-inventory.md](aok-affair-inventory.md) | AOK 事务清单，含实现状态、测试状态、对应 Skill |
| [skill-inventory.md](skill-inventory.md) | Copilot Skill 清单，含脚本状态、AOK 映射、适配进度 |
| [agent-inventory.md](agent-inventory.md) | Copilot Agent 清单，含事务映射、边界说明 |
| [mapping/skill_agent_aok_mapping.csv](mapping/skill_agent_aok_mapping.csv) | 机器可读的 Skill-Agent-AOK 映射表 |
| [mapping/skill_agent_aok_mapping.schema.json](mapping/skill_agent_aok_mapping.schema.json) | 映射表字段 Schema |
| [development/runner-design.md](development/runner-design.md) | 统一 AOK affair runner 设计文档 |
| [development/wrapper-template.md](development/wrapper-template.md) | Skill-local wrapper 模板说明 |
| [reports/](reports/) | 审计报告与阶段性进展 |

## 关键约定

1. **真源位置**：Skill/Agent 的 canonical 真源在内容库的 `libs/`，用户级 `.copilot/` 是部署产物。
2. **脱敏原则**：所有文档中不出现真实用户名、绝对 home 路径、密钥、令牌；统一使用 `${HOME}`、`AUTODO_KIT_ROOT`、`AUTODO_LIB_ROOT` 等占位符。
3. **状态标记**：
   - `ok`：已完成且验证通过
   - `needs_wrapper`：缺少 Skill-local wrapper
   - `needs_migration`：脚本过重，需迁入 AOK
   - `needs_params`：缺少参数模板
   - `docs_only`：纯说明型，无需脚本
   - `third_party`：通用第三方工具，不纳入 AOK
   - `deprecated`：已废弃的旧版本
4. **开发顺序**：先改内容库的 `libs/`（canonical 真源），再通过 AOB 发布到 `.copilot/`。
