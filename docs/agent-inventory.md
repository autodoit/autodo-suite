# Copilot Agent 清单与映射状态

> 最后更新：2026-07-30
> 
> 本清单记录用户级 `.copilot/agents/` 下所有 Agent 的事务映射与边界说明。

## 角色说明

Agent 不承载脚本。Agent 负责：
1. 角色定义与职责边界
2. AOK affair/tool 入口声明
3. 编排说明与调用约定

## 事务型 Agent（学术科研）

### v7 系列（当前推荐版本，AOE runtime 直接调度）

| Agent | 对应节点 | 默认入口 | 状态 |
|---|---|---|---|
| `ar_A010_项目初始化事务智能体_v7` | A010 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A020_文献导入与预处理事务智能体_v7` | A020 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A020_在线文献检索管理事务智能体_v7` | A020 | AOE runtime → registry | ✅ 已对齐 |
| `ar_A030_生成关键词集合事务智能体_v7` | A030 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A030_研究问题与关键词生成事务智能体_v7` | A030 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A040_文献检索与入库事务智能体_v7` | A040 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A040_本地文献检索管理事务智能体_v7` | A040 | AOE runtime → registry | ✅ 已对齐 |
| `ar_A050_文献下载与主附件入库事务智能体_v7` | A050 | AOE runtime → registry | ✅ 已对齐 |
| `ar_A060_统一文献预处理解析事务智能体_v7` | A060 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A070_统一文献预处理执行事务智能体_v7` | A070 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A080_阅读优先级生成事务智能体_v7` | A080 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A090_文献泛读与轻量分析事务智能体_v7` | A090 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A090_标准文献笔记生成事务智能体_v7` | A090 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A105_文献批判性研读与标准笔记事务智能体_v7` | A105 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A060_综述文献候选视图构建事务智能体_v7` | A110 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A120_研究脉络梳理事务智能体_v7` | A120 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A065_综述参考文献预处理与笔记骨架事务智能体_v7` | A120 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A070_综述文献研读事务智能体_v7` | A130 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A130_领域知识框架构建事务智能体_v7` | A130 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A075_普通文献候选视图构建事务智能体_v7` | A140 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A150_创新点可行性验证事务智能体_v7` | A150 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A080_普通文献泛读事务智能体_v7` | A150 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A160_报告收敛与交付事务智能体_v7` | A160 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A095_普通文献研读候选视图构建事务智能体_v7` | A160 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A100_文献批判性研读事务智能体_v7` | A170 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A110_研究脉络梳理事务智能体_v7` | A180 | AOE runtime → affair | ✅ 已对齐 |
| `ar_A140_创新点凝练事务智能体_v7` | A190 | AOE runtime → affair | ✅ 已对齐 |

### 编排与调度

| Agent | 职责 | 状态 |
|---|---|---|
| `ar_PA项目经理编排智能体_v7` | 人类指令转译、异常裁决、单节点补位 | ✅ 已对齐 |
| `ar_EA柔性工作流调度智能体_v1` | content.db 当前态管理与候选动作派发 | ✅ 已对齐 |

### v4 系列（兼容层）

| Agent | 对应节点 | 状态 |
|---|---|---|
| `ar_文献导入与预处理事务智能体_v4` | A020 | 🗑️ deprecated（v7 替代） |
| `ar_候选文献视图构建事务智能体_v4` | A060-A080 | 🗑️ deprecated |
| `ar_文献泛读事务智能体_v4` | A090 | 🗑️ deprecated |
| `ar_单篇文献精读事务智能体_v4` | A100 | 🗑️ deprecated |
| `ar_创新点池构建事务智能体_v4` | A140 | 🗑️ deprecated |
| `ar_创新点可行性验证事务智能体_v4` | A150 | 🗑️ deprecated |

### 专项事务 Agent

| Agent | 职责 | 对应 Skill | 状态 |
|---|---|---|---|
| `ar_在线检索与下载调试智能体_v1` | 独立 sandbox 验证检索/下载链路 | — | ✅ |
| `ar_毕业答辩事务智能体_v1` | 答辩 PPT + 演讲稿 + 问答准备 | 3 个 Skill | ✅ |
| `ar_计量经济学专家智能体_v1` | 计量模型与实证分析 | — | ✅ |
| `ar_理论与仿真模型事务智能体_v1` | 理论机制框架、数理模型、仿真 | — | ✅ |
| `ar_实证分析事务智能体_v1` | 变量操作化、实证四件套 | — | ✅ |
| `ar_数据检索与入库事务智能体_v1` | 外部数据源检索与入库 | — | ✅ |
| `ar_写作与投稿事务智能体_v1` | 章节草稿、投稿准备 | — | ✅ |
| `ar_审阅投稿与回流闸门智能体_v1` | 自审、外审、投稿判断 | — | ✅ |

### 管理运维 Agent

| Agent | 职责 | 状态 |
|---|---|---|
| `m_AOB用户级内容运作智能体_v1` | 编排 AOB 四大功能 | ✅ |
| `m_Skill运维管理智能体_v1` | Skill 脚本运维管理 | ✅ |
| `m_Obsidian运作智能体_v1` | Obsidian 笔记维护 | ✅ |
| `m_LaTeX智能体_v1` | LaTeX 编译与维护 | ✅ |
| `m_通用任务运作智能体_v1` | 通用任务执行 | ✅ |
| `m_设计与计划智能体_v1` | 设计文档与实施计划 | ✅ |
| `m_总管智能体_v1` | 开发验证文档同步 | ✅ |
| `m_独立测试调试智能体_v1` | 回归执行、故障定位 | ✅ |
| `cd_软件工具开发文档维护智能体_v2` | 工具包与宿主项目文档 | ✅ |
| `ar_多项目联动治理mailbox-relay注册事务智能体_v1` | 项目接入治理体系 | ✅ |
| `ar_多项目联动治理mailbox-relay投递事务智能体_v1` | 跨项目信件投递 | ✅ |

### 讲义幻灯片 Agent（非 AOK 体系）

| Agent | 职责 |
|---|---|
| `proofreader` | 学术讲义校对 |
| `slide-auditor` | 幻灯片视觉审计 |
| `tikz-reviewer` | TikZ 图审阅 |
| `domain-reviewer` | 领域实质审阅 |
| `pedagogy-reviewer` | 教学法审阅 |
| `r-reviewer` | R 代码审阅 |
| `quarto-critic` | Quarto→Beamer 对比审阅 |
| `quarto-fixer` | 修复 critic 指出的问题 |
| `beamer-translator` | Beamer→Quarto 翻译 |
| `verifier` | 端到端验证 |

## 统计

| 类别 | 数量 |
|---|---|
| v7 事务 Agent | ~27 |
| v4 兼容 Agent (deprecated) | ~6 |
| 编排调度 Agent | 2 |
| 专项事务 Agent | ~8 |
| 管理运维 Agent | ~12 |
| 讲义幻灯片 Agent | ~10 |
| **总计** | **~65** |

## 设计规则

1. Agent 不承载脚本 —— 脚本在 Skill 或 AOK 中。
2. Agent 默认声明 AOE runtime 为主执行路径。
3. Agent 仅在人工指定、异常修复、旁路排障时直接调用。
4. `.agent.md` 中的 AOK 入口声明应与 `affair_entry_registry` 一致。
