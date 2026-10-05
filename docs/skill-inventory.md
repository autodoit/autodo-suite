# Copilot Skill 清单与适配状态

> 最后更新：2026-07-30（第二轮铺完：wrapper + 迁移标记 + 废弃标注）
> 
> 本清单记录 canonical 内容库 `libs/skills/` 下所有 Skill 的脚本状态、AOK 映射与适配进度。
> 
> **注意**：所有路径中的用户 home 目录已替换为 `{HOME}`。

## 状态标记

| 标记 | 含义 |
|---|---|
| ✅ ok | 已完成适配，wrapper 经调试验证可用 |
| 🟡 wrapper_untested | wrapper 已就位（run_affair.py + params.examples.json），待调试验证 |
| 📦 needs_migration | 脚本过重，已有 MIGRATION_NEEDED.md 标记，待迁入 AOK |
| 📋 needs_params | 缺少参数模板 |
| 📖 docs_only | 纯说明型，无需脚本 |
| 🔌 third_party | 通用第三方工具，保留自有脚本 |
| 🗑️ deprecated | 已标注废弃（SKILL.md 含废弃说明块） |

## P1 优先适配清单（已铺完 wrapper + params，待调试验证）

以下 21 个业务型 Skill 已于 2026-07-30 批量补齐 `scripts/run_affair.py` + `params.examples.json` + `README.md`。
所有 wrapper 通过统一的 `autodokit.tools.adapters.runner.run_affair` 调用对应 AOK 事务。
**尚未进行调试验证。**

### A030/A040/A050 系列（关键词、检索、下载）

| Skill | AOK Affair | 状态 | 备注 |
|---|---|---|---|
| `ar_A030_生成关键词集合_v6` | `生成关键词集合` | 🟡 wrapper_untested | |
| `ar_A040_CNKI基础检索_v5` | `CNKI基础检索` | 🟡 wrapper_untested | |
| `ar_A040_CNKI高级检索_v5` | `CNKI高级检索` | 🟡 wrapper_untested | |
| `ar_A040_CNKI结果解析_v5` | `CNKI结果解析` | 🟡 wrapper_untested | |
| `ar_A040_CNKI文献详情提取_v5` | `CNKI单篇详情提取` | 🟡 wrapper_untested | |
| `ar_A040_CNKI文献下载_v5` | `CNKI全文下载规划` | 🟡 wrapper_untested | |
| `ar_A045_文献下载与主附件入库_v1` | `文献下载与主附件入库` | 🟡 wrapper_untested | affair.json 不存在，参数为推断值 |

### A060-A080 系列（预处理、视图）

| Skill | AOK Affair | 状态 | 备注 |
|---|---|---|---|
| `ar_A050_统一文献预处理解析_v1` | `统一文献预处理解析` | 🟡 wrapper_untested | |
| `ar_A060_综述候选文献视图构建_v7` | `候选文献视图构建` | 🟡 wrapper_untested | |
| `ar_A060_综述预处理_v6` | `综述预处理` | 🟡 wrapper_untested | |
| `ar_A075_非综述候选种子生成_v1` | `非综述候选种子生成` | 🟡 wrapper_untested | affair.json 不存在，参数为推断值 |
| `ar_A080_非综述候选文献视图构建_v5` | `非综述候选视图构建` | 🟡 wrapper_untested | affair.json 为空对象，参数为推断值 |

### A090-A180 系列（阅读、矩阵、脉络）

| Skill | AOK Affair | 状态 | 备注 |
|---|---|---|---|
| `ar_A090_文献泛读与粗读_v6` | `文献泛读与粗读` | 🟡 wrapper_untested | affair.json 不存在，参数为推断值 |
| `ar_A100_单篇文献精读_v6` | `文献研读与正式知识回写` | 🟡 wrapper_untested | |
| `ar_A110_文献矩阵构建_v6` | `文献矩阵` | 🟡 wrapper_untested | |
| `ar_A120_引文化研究脉络综述_v6` | `研究脉络梳理` | 🟡 wrapper_untested | |
| `ar_A130_领域知识框架构建_v6` | `领域知识框架构建` | 🟡 wrapper_untested | |

### A140-A150 系列（创新点）

| Skill | AOK Affair | 状态 | 备注 |
|---|---|---|---|
| `ar_A140_创新点池生成_v6` | `创新点池构建` | 🟡 wrapper_untested | |
| `ar_A150_创新点可行性验证_v6` | `创新点可行性验证` | 🟡 wrapper_untested | |

### 辅助系列

| Skill | AOK Affair | 状态 | 备注 |
|---|---|---|---|
| `ar_CNKI期刊检索_v1` | `CNKI期刊检索` | 🟡 wrapper_untested | |
| `ar_文献检索治理与路由_v1` | `检索治理` | 🟡 wrapper_untested | 另有 params.json |

## 已适配清单

以下 Skill 已有正确 wrapper 且不需额外操作：

| Skill | 脚本状态 | AOK Affair | 状态 |
|---|---|---|---|
| `m_AOB用户级内容发布_v1` | wrapper | `AOB用户级内容发布` | ✅ ok |
| `m_AOB用户级内容同步_v1` | wrapper | `AOB用户级内容同步` | ✅ ok |
| `m_AOB用户级内容备份_v1` | wrapper | `AOB用户级内容备份` | ✅ ok |
| `m_AOB用户级内容聚合_v1` | wrapper | `AOB用户级内容聚合` | ✅ ok |

## 第三方工具 Skill（不纳入 AOK）

以下 Skill 为通用文档/系统/配置工具，保留自有 scripts，不纳入 AOK 事务治理：

`docx`, `pptx`, `pdf`, `xlsx`, `markitdown`, `marp-slides-creator`,
`fetch4ai`, `arxiv`, `github-trending`, `chinese-quote-converter`,
`ssh-key-remote-login-v1`, `ubuntu26-04-sftp-samba`, `m-direct-link-smb-share-v1`,
`m-remote-training-keepalive-v1`, `install-linux-package`,
`compile-latex`, `extract-tikz`, `translate-to-quarto`, `create-lecture`,
`deploy`, `slide-excellence`, `command-development`, `skill-creator`, `learn`,
`frontend-design`, `context-status`, `commit`, `cc-insights`,
`chat-history-summarizer`, `obsidian-tag-style-analyzer`,
`validate-bib`, `proofread`, `pedagogy-review`, `devils-advocate`,
`interview-me`, `lit-review`, `review-paper`, `review-r`, `data-analysis`,
`research-ideation`, `web-research`, `qa-quarto`, `visual-audit`,
`md-to-docx`, `docx-to-tex`, `mineru-pdf-converter`,
`version-promotion`, `update-file-to-final-version`

## 重脚本待迁移（已有 MIGRATION_NEEDED.md 标记）

| Skill | 脚本 | AOK Affair | 状态 | 备注 |
|---|---|---|---|---|
| `A010_项目初始化_v6` | `generate_config.py` | `项目初始化` | 📦 needs_migration | 核心初始化逻辑（目录树、content.db DDL、AOE 工作流注入）；已同时补 `scripts/run_affair.py` 作为迁移后目标形态 |
| `ar_文献导入与预处理事务综合技能_v1` | `run_a02_import_and_preprocess.py` | `导入和预处理文献元数据` | 📦 needs_migration | 附件复制骨架实现（TODO 阶段）；已同时补 `scripts/run_affair.py` 作为迁移后目标形态 |

## 已废弃版本（SKILL.md 已标注 `## ⚠️ 已废弃 (deprecated)`）

共计 **32** 个旧版本已于 2026-07-30 在 SKILL.md 末尾添加废弃说明块。

### v5 → v7 升级

| 废弃版本 | 推荐版本 |
|---|---|
| `ar_A020_文献导入和预处理元数据_v5` | `ar_A020_文献导入和预处理元数据_v7` |
| `ar_A020_文献导入和预处理元数据_v6` | `ar_A020_文献导入和预处理元数据_v7` |

### v5 → v6 升级

| 废弃版本 | 推荐版本 |
|---|---|
| `ar_A060_综述预处理_v5` | `ar_A060_综述预处理_v6` |
| `ar_A090_文献泛读与粗读_v5` | `ar_A090_文献泛读与粗读_v6` |
| `ar_A100_单篇文献精读_v5` | `ar_A100_单篇文献精读_v6` |
| `ar_A110_文献矩阵构建_v5` | `ar_A110_文献矩阵构建_v6` |
| `ar_A140_创新点池生成_v5` | `ar_A140_创新点池生成_v6` |
| `ar_A150_创新点可行性验证_v5` | `ar_A150_创新点可行性验证_v6` |

### v1/v3 → v5 升级（CNKI 系列）

| 废弃版本 | 推荐版本 |
|---|---|
| `ar_CNKI基础检索_v1` | `ar_A040_CNKI基础检索_v5` |
| `ar_CNKI基础检索_v3` | `ar_A040_CNKI基础检索_v5` |
| `ar_CNKI高级检索_v1` | `ar_A040_CNKI高级检索_v5` |
| `ar_CNKI高级检索_v3` | `ar_A040_CNKI高级检索_v5` |
| `cnki_CNKI高级检索_v1` | `ar_A040_CNKI高级检索_v5` |
| `ar_CNKI文献下载_v1` | `ar_A040_CNKI文献下载_v5` |
| `ar_CNKI文献下载_v3` | `ar_A040_CNKI文献下载_v5` |
| `ar_CNKI文献详情提取_v1` | `ar_A040_CNKI文献详情提取_v5` |
| `ar_CNKI文献详情提取_v3` | `ar_A040_CNKI文献详情提取_v5` |
| `ar_CNKI结果解析_v3` | `ar_A040_CNKI结果解析_v5` |

### v3 → v6/v7 升级

| 废弃版本 | 推荐版本 |
|---|---|
| `ar_文献导入和预处理元数据_v3` | `ar_A020_文献导入和预处理元数据_v7` |
| `ar_综述候选文献视图构建_v3` | `ar_A060_综述候选文献视图构建_v7` |
| `ar_候选文献视图构建与批次分发_v3` | `ar_A060_综述候选文献视图构建_v7` |
| `ar_非综述候选文献视图构建_v3` | `ar_A080_非综述候选文献视图构建_v5` |
| `ar_综述精读与研究脉络梳理_v3` | `ar_A120_引文化研究脉络综述_v6` |
| `ar_综述精读与研究脉络梳理_v5` | `ar_A120_引文化研究脉络综述_v6` |
| `ar_文献泛读与粗读_v3` | `ar_A090_文献泛读与粗读_v6` |
| `ar_单篇文献精读_v3` | `ar_A100_单篇文献精读_v6` |
| `ar_文献矩阵构建_v3` | `ar_A110_文献矩阵构建_v6` |
| `ar_引文化研究脉络综述_v3` | `ar_A120_引文化研究脉络综述_v6` |
| `ar_领域知识框架构建_v3` | `ar_A130_领域知识框架构建_v6` |
| `ar_创新点池生成_v3` | `ar_A140_创新点池生成_v6` |
| `ar_创新点可行性验证_v3` | `ar_A150_创新点可行性验证_v6` |
| `ar_研究缺口识别_v3` | `ar_A110_研究缺口识别_v6` |

## 统计

| 类别 | 数量 |
|---|---|
| wrapper 已就位，待调试验证 (P1) | 21 |
| 重脚本待迁移 (已有标记) | 2 |
| 已适配 (AOB 系列) | 4 |
| 已标注废弃 (SKILL.md 含废弃块) | 32 |
| 第三方工具 | ~40+ |
