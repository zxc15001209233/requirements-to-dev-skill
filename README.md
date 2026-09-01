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

本 Skill 提供按需流程与细则（均为 `.md`）。协作门禁：项目已有总规则则用项目的；没有时用 `SKILL.md` 默认门禁。要每轮对话都守 `go`，建议项目自行安装 `AI工作规范.md`：Cursor 放 `.cursor/rules/`（需同名 `.mdc` 软链且 `alwaysApply: true`），Trae 放 `.trae/rules/`，CodeBuddy 放 `.codebuddy/rules/`。

## 使用方式

Agent 能读到本 Skill 后即可说，例如：

- 「按这份 PM 文档写需求规格」
- 「补一下本项目技术选型覆盖表」
- 「需求定稿了，拆开发计划」
- 「go 执行 M1.2–M1.4（写契约，不写 Spring）」

流程：

```
（有挡住拆章/选型的不确定点）对话歧义清单 → 用户回答
  → 对话确认卡（路径 / 功能清单 / 选型含数据库实际值 / 本次只写文档或实现）
  →（文档 go）需求规格 + 技术栈 §2
  →（完整路径）数据模型确认 + 设计契约 + 开发计划
  →（实现 go：卡上写 Mx–My 与完成口径）范围内按依赖连续实现
  → 对照该口径自测通过后标「已完成」
```

轻量路径默认不写独立开发计划。同一轮 `go` 不得既写规格又写代码。写需求 / 选型 / 计划时：规模分流、阶段确认与就绪门禁以 `SKILL.md` 为准；协作门禁有项目总规则用项目的，否则用 `SKILL.md` 默认节。数据大屏原型委托 `bi-dashboard-generator`（先读对方 `SKILL.md`，未安装则停）。混合文档由本 Skill 先判定范围。

**不要只分发 `SKILL.md`。** 写需求 / 选型 / 计划时 Agent 会按阶段打开同目录附件。

## 目录

```
SKILL.md                          # 流程、门禁、路径判定
通用需求规格规范.md               # 需求怎么写
通用需求规格规范-使用指南.md
通用需求规格规范-示例.md
通用需求规格规范-附录.md
通用技术选型规范.md               # 默认栈与项目覆盖
通用开发计划管理规范.md           # 怎么拆模块、怎么跟
通用开发计划管理规范-使用指南.md
通用开发计划管理规范-示例.md
通用开发计划管理规范-附录.md      # 任务包
```

## 许可证

木兰宽松许可证第 2 版（Mulan PSL v2），见 [LICENSE](./LICENSE)。

## 更新

| 时间 | 说明 |
|---|---|
| 2026-09-01 | 实现确认卡写 Mx–My 与完成口径，范围内连续执行不空点 go；选型必须含数据库实际值；模块状态按完成口径关闭，禁止用真接口未测卡住契约模块 |
| 2026-09-01 | N.5 分挡开发 / 正文默认 / 不列入；门禁只卡挡开发项 |
| 2026-09-01 | 复杂/歧义材料须先出对话歧义清单并等回答，再出确认卡；不挡拆章的细节仍可进遗留 |
| 2026-09-01 | 增加对话确认卡与文档/实现分阶段 `go`；轻量默认不写独立开发计划；禁止同一轮既写规格又写代码 |
| 2026-09-01 | 补交接读对方 SKILL、未安装则停；混合文档由本 Skill 先判定范围；写明如何判定「已有总规则」 |
| 2026-09-01 | 协作门禁改为「有项目总规则用项目的，否则用本 Skill 默认」；description 去掉 `go` 触发词；大屏原型委托 `bi-dashboard-generator` |
| 2026-08-31 | 门禁以本 Skill 为准，不再依赖项目内 Cursor `.mdc`；README 补充非 `skills add` 环境的整目录用法 |
| 2026-08-31 | 三个核心规范补规则头，并增加同名 `.mdc` 链接，便于拷进 Cursor `.cursor/rules/` |
| 2026-08-31 | 去掉三个 `.mdc` 与规则头；Skill 只保留 `.md`。每轮门禁改为由项目自行安装 AI工作规范 |
