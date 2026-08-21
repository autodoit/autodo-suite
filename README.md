# Autodo Suite (AOS)

Autodo Suite（AOS）是一个多仓库的开发聚合目录，用于协调和统一 `autodo-engine`、`autodo-kit`、`autodo-lib` 与 `autodo-app` 的本地开发、测试与文档工作流。

## 目录结构（工作区）

- `autodo-engine`：核心调度引擎与运行时。
- `autodo-kit`：预置事务（Affairs）、示例与业务工具。
- `autodo-lib`：基础库、Prompt 与 Agent 定义。
- `autodo-app`：前端/集成应用（示例 GUI、VS Code 集成等）。

## 目标

- 提供统一的快速启动与本地联调说明。
- 记录跨仓库的开发约定与文档同步策略。
- 作为开发者进入多个子仓库的入口说明文档。

## 快速启动（Windows / Git Bash）

1. 在 AOS 根目录创建并激活虚拟环境：

```bash
uv venv --python 3.13 .venv
source .venv/Scripts/activate
```

2. 使用项目约定的 `uv` 工具将本地包以可编辑模式安装（示例）：

```bash
uv pip install -e ../autodo-engine
uv pip install -e ../autodo-kit
```

3. 进入子仓库查看并遵循各自的 `README.md` 获得更详细的运行或安装说明。

## 常用命令

- 运行引擎测试（在 `autodo-engine` 目录）：

```bash
cd ../autodo-engine
pytest
```

- 运行示例/演示（在 `autodo-kit` 目录）：

```bash
cd ../autodo-kit
python demos/demo_v3_decision_rule_framework_examples.py
```

## 文档同步约定

- 源码变更后，请参考仓库内的更新同步约定（例如 `.github/skills/update-sync/SKILL.md`）决定是否更新 `docs/` 下的文档。
- 最低同步标准：API 手册、字段表与示例必须与源码一致。

## 提交与 PR 要求

- 说明变更目标、范围与验证步骤。
- 避免在单次 PR 中大幅调整公共 API 或目录结构；优先小而明确的变更。

## 多项目联动治理（mailbox/relay）

本聚合工作区及各子项目已接入 autodo mailbox/relay 多项目联动治理体系。

- 每个项目在 `docs/mailbox/relay/` 维护信箱，用于上下游变更通知和适配建议。
- AI Agent 行为指引见各项目的 `docs/mailbox/relay/.ai-instructions.md`。
- 完整协议说明见 `docs/mailbox/relay/README.md`。
- 用户级 Skill：`m_多项目联动治理mailbox-relay_v1`。
- 后端启动：`cd autodo-app && pnpm run mailbox:api`。

## 贡献与问题反馈

请在仓库根目录创建 Issue，或分别查看子仓库的 `README.md` 获取维护者联系方式。

---

如需我把各子仓库的 README 内容合并进此文件，或生成带有更多示例和 CI 步骤的扩展版，请告诉我。