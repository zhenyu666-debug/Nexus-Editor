# Nexus-Editor PR 检查清单

发 PR 前必读并勾选以下项目。

## 1. 仓库规范文件

- [ ] 已阅读 [CONTRIBUTING.zh.md](./CONTRIBUTING.zh.md) —— 了解分支命名、Conventional Commits scope 白名单、OpenSpec 流程
- [ ] 已阅读 [.github/PULL_REQUEST_TEMPLATE.md](./.github/PULL_REQUEST_TEMPLATE.md) —— PR 描述模板
- [ ] 如有新增 capability 或破坏性 API 变更: 已阅读 [openspec/AGENTS.md](./openspec/AGENTS.md)

## 2. 分支命名

- [ ] 分支名遵循规范: `feat/<scope>/<short-description>` 或 `fix/<scope>/<description>`
- [ ] 示例: `feat/core/get-selected-text`, `fix/live-preview/caret-position`

## 3. Commit 规范

- [ ] 使用 [Conventional Commits](https://www.conventionalcommits.org/) 格式
- [ ] 标题格式: `<type>(<scope>): <description>`
- [ ] **重要**: 使用已验证的 CLA 邮箱 (`zhuangzhenyu19@gmail.com` 或 `zhenyulius@163.com`)
- [ ] 示例: `fix(live-preview): place caret at click point inside table cells`

## 4. PR 描述模板 (双语必须)

PR body 必须包含以下所有章节,**缺一不可**:

- [ ] **Title**: 遵循 Conventional Commits (带 scope)
- [ ] **Summary / 摘要**: 用中文和英文描述改动,各一段
- [ ] **Motivation / 背景与动机**: 为什么需要这个改动 (中英双语)
- [ ] **Changes / 变更内容**: 列出具体改了什么文件、什么函数 (中英双语)
- [ ] **Testing / 测试**: 列出手动/自动化测试结果 (中英双语)
- [ ] **Compliance / 合规自检**:
  - [ ] CLA 已签
  - [ ] AI 使用说明 (如适用)
  - [ ] 无新增依赖
  - [ ] 无 build artifacts
  - [ ] 无 secrets
- [ ] **Checklist / 自检清单**: 按 CONTRIBUTING.zh.md 要求勾选

## 5. 代码质量

- [ ] `pnpm test` 全绿
- [ ] `pnpm build` 成功
- [ ] `pnpm lint` 无错误 (如有 lint 配置)
- [ ] 新代码有测试覆盖
- [ ] 改动范围与 PR 标题一致 (不夹带无关改动)

## 6. 特殊要求

### Table Widget 改动 (如改 `live-preview-table.ts`)
- [ ] 已通读 CLAUDE.md 中的 12 条 Table Widget 规则
- [ ] 手动验证: cell focus / editing / IME / selection / undo-redo / copy-paste

### AI 辅助代码
- [ ] 已按模板要求说明 AI 使用情况
- [ ] 核心逻辑不是纯 AI 生成

## 7. 提交检查

```bash
# 1. 确认邮箱正确
git config --local user.email
# 期望: zhuangzhenyu19@gmail.com 或 zhenyulius@163.com

# 2. 确认只有相关改动
git diff --stat

# 3. 确认测试通过
pnpm test

# 4. 确认构建通过
pnpm build
```

---

## 模板: PR Body 格式

```markdown
## fix(<scope>): <short description>

## Summary / 摘要

[English: What this PR does]

[中文: 这个 PR 做了什么]

## Motivation / 背景与动机

[English: Why this change is needed]

[中文: 为什么需要这个改动]

## Changes / 变更内容

- `packages/core/src/xxx.ts`:
  - [具体改动1]
  - [具体改动2]

- 其他包: no changes

## Testing / 测试

- [x] `pnpm test` passes
- [x] Manual UI check:
  - [场景1] -> [期望结果]
  - [场景2] -> [期望结果]

## Compliance / 合规自检

- [x] **CLA signed** (YOUR_EMAIL)
- [x] **AI disclosure**: [说明 AI 用法]
- [x] **No new dependencies**
- [x] **No build artifacts committed**
- [x] **No secrets committed**

## Checklist / 自检清单

- [x] Title follows Conventional Commits
- [x] PR body includes all required sections (Summary, Motivation, Changes, Testing, Compliance, Checklist)
- [x] All sections are in both Chinese and English
- [x] No public API changes (or OpenSpec linked if applicable)
```
