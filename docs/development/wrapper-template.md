# Skill-local Wrapper 模板说明

## 目标

为每个需要调用 AOK affair 的 Skill 提供标准化的薄封装脚本，使 Agent 可以统一方式调用。

## 何时需要 wrapper

| Skill 类型 | 需要 wrapper? | 说明 |
|---|---|---|
| 业务型，已匹配 AOK affair | ✅ 是 | 需要 wrapper 调用统一 runner |
| 业务型，未匹配 AOK affair | ⚠️ 视情况 | 先匹配 affair，再补 wrapper |
| 通用工具型（第三方） | ❌ 否 | scripts 可保留自有实现 |
| 管理/运维型 | ⚠️ 视情况 | AOB 系列已有 wrapper |
| 纯说明型 | ❌ 否 | 无需脚本 |

## Wrapper 职责

1. **参数解析**：读取 `--params` 指定的 JSON 文件。
2. **路径定位**：找到 autodo-kit 仓库根目录。
3. **调用 Runner**：`run_affair(affair_name, params_path, repo_root, dry_run)`。
4. **结果输出**：将 `AffairResult` 序列化为 JSON 输出。

## Wrapper 不应做的事

1. ❌ 包含业务逻辑
2. ❌ 直接 import affair 模块（应通过 runner）
3. ❌ 硬编码绝对路径（使用环境变量或自动查找）
4. ❌ 实现参数校验（交给 runner 和 affair）

## 迁移指南

### 从 heavy 脚本迁移

如果现有 Skill 的 `scripts/` 中包含业务逻辑：

1. 将核心逻辑迁入 `autodo-kit/autodokit/affairs/<affair>/` 或 `autodokit/tools/`。
2. 将原脚本替换为薄 wrapper。
3. 更新 `params.examples.json` 与 affair.json 保持一致。

### 从空 scripts 迁移

1. 确认 Skill 对应的 AOK affair 名称。
2. 复制模板 wrapper 到 `scripts/run_affair.py`。
3. 从对应 `affair.json` 生成 `params.examples.json`。
4. 运行 `--dry-run` 验证。
