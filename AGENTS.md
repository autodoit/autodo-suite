# autodo-suite 项目指令（canonical）

> 本文件是本项目 AI 指令的**唯一正文源**。`CLAUDE.md`、`.github/copilot-instructions.md` 为薄转发壳，不复制正文。
> 详细多根工作区导航见同目录 `WORKSPACE_GUIDE.md`。

## 工作区角色
- `autodo-suite` 是多仓聚合工作区（AOS），只承接聚合配置、开发说明与跨仓入口，**不放业务运行时代码**。
- 实现具体能力先定位子仓：引擎/运行时 → `autodo-engine`；事务/工具 → `autodo-kit`；内容库/安装器 → `autodo-lib`；前端/集成界面 → `autodo-app`。
- 跨仓公共约束以各子仓自己的 `.github/copilot-instructions.md` 为准；本文件只定义聚合层默认行为。

## 构建与测试
- Python 基线 `3.14`，依赖与环境统一用 `uv`。
- **执行仓库命令前必须先切到目标子仓**，禁止在 AOS 根或办公区直接跑仓库命令。
- 联调环境：`uv pip install -e ../autodo-engine -e ../autodo-kit`。
- 引擎测试：`cd ../autodo-engine && pytest`；工具演示看 `../autodo-kit/README.md`；前端启动看 `../autodo-app/README.md`。

## 通用性红线
- 改 `autodo-kit` 必须保持**学科无关的通用性**：只允许通用文档/注释/常量/代码结构/算法/设计模式/架构，**禁止出现任何行业、学科、业务领域术语**。

## 路径与演进契约
- 公开配置只用 `workspace_root` 作根目录基准；不在事务/节点/工作流示例里写相对路径业务逻辑。
- 用户输入可为相对路径，但必须在 tools 层统一转为内部绝对路径再交给业务逻辑。
- 项目按「**不向后兼容**」演进；过时代码/文档/示例直接删除，不留兼容壳。

## 文档同步
- 源码行为变化后，按目标子仓规范同步；最低标准：API 手册、字段表、示例与源码一致。
- 办公文档遵循通用命名 `文档类型-内容名-YYYYMMDD-UID.md`；默认不读 `archives/`，除非任务明确要求。

## 多项目联动治理（mailbox/relay）
- 本项目已接入 autodo mailbox/relay 治理体系。
- AI 行为指引见 `docs/mailbox/relay/.ai-instructions.md`；操作详见用户级 Skill `m_多项目联动治理mailbox-relay_v1`。

## 工作区地图（移动端速查）
- 工程笔记：`Engs_notebook/Projects/自动运作系统` → `tasks/`（任务）、`notes/`（设计）、`archive/`（归档）
- 理论笔记：`ES_notebook/Projects/通用任务事务运作流程管理` → 同上
- 子项目笔记本通常含 `tasks/`、`notes/`、`archive/`；对话中说「查看任务/打开笔记」即按此定位。
- 完整多根清单与各项目子目录：见同目录 `WORKSPACE_GUIDE.md`。
