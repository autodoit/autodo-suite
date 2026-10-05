# Autodo Suite 开发与运行指南

本仓库（Autodo Suite，简称 AOS）作为多个子仓库的逻辑聚合目录，便于统一开发、验证与本地联调。AOS 本身不包含运行时代码，主要用于说明、快速启动脚本与跨仓库的开发流程。

**子仓库一览**
- `autodo-engine`：核心调度引擎与运行时（AOE）。
- `autodo-kit`：预置事务、示例与业务工具（AOK）。
- `autodo-app`：前端/集成应用（AOA）。

## 快速开始（推荐顺序）
1. 在 AOS 根目录创建虚拟环境并切换（Windows / Git Bash）：

```bash
uv venv --python 3.13 .venv
source .venv/Scripts/activate
```

2. 使用 `uv`（项目约定）安装并以可编辑模式连接本地子包：

```bash
uv pip install -e ../autodo-engine
uv pip install -e ../autodo-kit
```

3. 阅读各子仓库的 README 以了解子模块的额外依赖或本地运行步骤。

## 常用开发命令
- 运行引擎测试（在 `autodo-engine` 下）：

```bash
cd ../autodo-engine
pytest
```

- 运行示例/演示（在 `autodo-kit` 下）：

```bash
cd ../autodo-kit
python demos/demo_v3_decision_rule_framework_examples.py
```

## 文档与同步约定
- 源码变更后，请参考仓库内的 `.github/skills/update-sync/SKILL.md`（若存在）来决定是否同步 `docs/` 中的内容。
- 文档更新应遵循“最低同步标准”：API 手册、字段表与示例必须与源码一致。

## 本地调试建议
- 若在导入包时遇到意外依赖或导入副作用，检查子包的 `__init__.py` 是否做了过度的 eager import；优先使用懒加载或明确导入子模块。
- Windows 环境下若虚拟环境异常，请参照项目级别的调试备忘（例如：重建 `.venv`）。

## 多项目联动治理（mailbox/relay）

开发过程中若修改了公共 API，请通过 mailbox/relay 体系通知下游项目。

### 信箱位置

每个子项目在 `docs/mailbox/relay/` 维护信箱：
- `out-up/` — 写给上游依赖项目的反馈
- `out-down/` — 写给下游被依赖项目的适配建议
- `in-up/` — 上游发来的建议
- `in-down/` — 下游发来的反馈

### 启动后端

```bash
cd autodo-app && pnpm run mailbox:api
```

### AI Agent 操作

详见用户级 Skill `m_多项目联动治理mailbox-relay_v1`。

## 提交与 PR 要求
- 变更应说明目标、范围与验证步骤。
- 小步快进：避免在单次 PR 中大幅调整公共 API 或目录结构。

## 联系与贡献
如需帮助，请在仓库根目录打开 Issue，或直接联系维护者（见各子仓库的 `README.md`）。

---

以上为精简版开发启动与约定说明。如需更详细的运行示例、CI 指南或发布流程，我可以把相应子仓库的 README 整合为更完整的 AOS 指南。
