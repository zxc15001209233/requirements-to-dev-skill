# requirements-to-dev

通用 Agent Skill：把「需求规格 / 技术选型 / 开发计划」做成可跨项目、跨编辑器使用的流程，覆盖中后台类新项目从需求到按模块验收。不绑定某一 IDE 或某一业务仓库。

不包含编码风格、排期人力、部署运维。

仓库：

- Gitee：https://gitee.com/zxc19890923/requirements-to-dev-skill
- GitHub：https://github.com/zxc15001209233/requirements-to-dev-skill

## 安装

支持 [Agent Skills](https://github.com/anthropics/skills) 的环境（Cursor、Claude Code、Codex 等）可用：

```bash
# Gitee（国内推荐）
npx skills add https://gitee.com/zxc19890923/requirements-to-dev-skill.git
npx skills add https://gitee.com/zxc19890923/requirements-to-dev-skill.git -g

# GitHub
npx skills add zxc15001209233/requirements-to-dev-skill
npx skills add zxc15001209233/requirements-to-dev-skill -g
```

第一条装到当前项目，带 `-g` 的为全局安装（所有项目可用）。

不支持 `skills add` 的编辑器（部分 Copilot、Trae、CodeBuddy 等）：把**本目录整份**放进项目（不要只拷 `SKILL.md`），在该产品的项目指令里写明：先读本目录 `SKILL.md`，细则读同目录 `通用*.md`。常见落点包括 `AGENTS.md`、`.github/copilot-instructions.md` 或产品自己的 skills / 自定义指令。

若要同时给 **Cursor 项目规则**用：正文只维护 `.md`。三个核心规范已带规则头，并有同名 `.mdc` 符号链接。把这两套文件放进项目的 `.cursor/rules/` 即可（Cursor 认 `.mdc`，其他编辑器认 `.md`）。不要复制出第二份正文。门禁仍以 `SKILL.md` 为准，不必再放一份 `AI工作规范.mdc`。

## 使用方式

Agent 能读到本 Skill 后即可说，例如：

- 「按这份 PM 文档写需求规格」
- 「补一下本项目技术选型覆盖表」
- 「需求定稿了，拆开发计划」
- 「go 执行 M1.2」

流程：

```
判定轻量 / 完整路径
  → 需求规格（原型 + 业务逻辑 + 验收要点）
  → 技术栈 §2 实际值（与默认不同则记覆盖）
  →（完整路径）数据模型确认 + 设计契约 + 开发计划
  → 按依赖逐模块组装任务包实现
  → 对照验收要点通过后标「已完成」
```

改文件必须用户输入以 `go` 开头。门禁以 `SKILL.md` 为准，不要求项目里存在 Cursor `.mdc`。

**不要只分发 `SKILL.md`。** 写需求 / 选型 / 计划时 Agent 会按阶段打开同目录附件。

## 目录

```
SKILL.md                          # 流程、门禁、路径判定
通用需求规格规范.md / .mdc        # 需求怎么写（.mdc 链到 .md，供 Cursor）
通用需求规格规范-使用指南.md
通用需求规格规范-示例.md
通用需求规格规范-附录.md
通用技术选型规范.md / .mdc        # 默认栈与项目覆盖
通用开发计划管理规范.md / .mdc    # 怎么拆模块、怎么跟
通用开发计划管理规范-使用指南.md
通用开发计划管理规范-示例.md
通用开发计划管理规范-附录.md      # 任务包
```

## 许可证

木兰宽松许可证第 2 版（Mulan PSL v2），见 [LICENSE](./LICENSE)。

## 更新

| 时间 | 说明 |
|---|---|
| 2026-08-31 | 门禁以本 Skill 为准，不再依赖项目内 Cursor `.mdc`；README 补充非 `skills add` 环境的整目录用法 |
| 2026-08-31 | 三个核心规范补规则头，并增加同名 `.mdc` 链接，便于拷进 Cursor `.cursor/rules/` |
