# requirements-to-dev

把 PM 丢来的材料转成大模型能执行的**需求规格**，再按固定顺序做到可验收的 Vue / Spring。不绑定某一 IDE 或业务仓库。

用户不必自己写规格模板。材料格式不限，**开发前必须先完成转换**；不能拿 Word / PDF / 聊天原文直接写代码。

不覆盖编码风格、排期人力、部署运维、CI、本机 JDK 路径。

仓库：

- Gitee：https://gitee.com/zxc19890923/requirements-to-dev-skill
- GitHub：https://github.com/zxc15001209233/requirements-to-dev-skill

## 你可以丢什么

认的是「能不能读出业务文字」，不是固定模板或扩展名白名单。

| 材料 | 常见形态 | 怎么用 |
|---|---|---|
| PM 正文（主入口） | **docx、可检索 PDF**；md、txt、对话里粘贴的章节 | 角色、范围、规则、口径 |
| UI（可选） | Figma、Axure / HTML 原型、截图、PDF 里的设计图 | 界面引用；大屏图交给下方另一个 Skill |
| 已有需求规格 | 按本仓库规范写好的 md | 用户点名「按这份规格开发」时，不再从 PRD 转一遍 |

扫描件、纯图无字、表和正文对不上：先问，不假装已经读懂。Sketch / XD 须先导出成图或 HTML。飞书 / 在线文档请导出或把正文放进仓库。

PRD、产品方案、需求说明叫什么都可以，都只是原材料。

## 必须先转需求规格

| | 原材料（PRD 等） | 需求规格（本 Skill 产出） |
|---|---|---|
| 给谁看 | 人 | 大模型 + 人审 |
| 结构 | 不限 | 一章一个功能；确定 / 待定 / 示例分开；有界面就链原型或标「待生成」 |
| 能否开发 | 不能 | 转换并审核后，才能进入后面的写死流程 |

后面顺序写死，不再分轻量 / 完整：

```
需求规格 → 技术选型 §2 → 数据模型 → 设计契约 → 开发计划 → 实现
```

一次只落盘一份；每份独立机审（`review/`）后再等人审「下一步」。无已审核开发计划，不得写 Vue / Spring / 转 Vue。

## 中后台还是大屏

| 项目 | 你提供 | 谁做什么 |
|---|---|---|
| 纯中后台 / CRUD | PRD 类材料（+ 可选 UI） | 本 Skill 从转换规格一路做到实现 |
| 纯大屏 / 看板 | 同上即可 | 本 Skill 负责规格与写死流程；HTML 原型委托 `bi-dashboard-generator`；转 Vue / 写 Spring 交回本 Skill |
| 大屏 + 中后台混在一份材料里 | 同一份即可 | 本 Skill 先判定范围：大屏页只委托 HTML，其余章节留在本 Skill；禁止两边各做一整份 |

对方 Skill 未安装则停，请先安装或点名调用。

## 使用方式

Agent 能读到本 Skill 后即可说，例如：

- 「按这份 PRD 写需求规格」（docx / pdf / 粘贴正文均可）
- 「补一下本项目技术选型覆盖表」
- 「需求定稿了，拆开发计划」
- 「go 执行 M1.2–M1.4（写契约，不写 Spring）」

对话节奏：

```
本份歧义清单（未确认先问）→ 用户回答
  → 本份确认卡（恰好一份文档，或实现时的 Mx–My）
  → go 只写这一份 → 立刻独立机审（结论进 review/）→ 停，交人审
  → 用户确认下一步
  → 按上一节顺序继续
  →（实现 go：计划已审核；卡上写 Mx–My 与完成口径）范围内按依赖连续实现
```

项目已有总规则（如 `AI工作规范.md`）则协作门禁用项目的；没有时用 `SKILL.md` 默认门禁（没有 `go` 不改文件）。要每轮都守 `go`，建议项目自行安装该规范。

**不要只分发 `SKILL.md`。** 写需求 / 选型 / 计划时 Agent 会按阶段打开同目录 `通用*.md`。

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

不支持 `skills add` 的编辑器（部分 Copilot、Trae、CodeBuddy 等）：把**本目录整份**放进项目，在该产品的项目指令里写明：先读本目录 `SKILL.md`，细则读同目录 `通用*.md`。常见落点包括 `AGENTS.md`、`.github/copilot-instructions.md` 或产品自己的 skills / 自定义指令。

## 目录

```
SKILL.md                          # 流程、门禁、统一顺序
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
| 2026-09-03 | README：写清材料入口（格式宽泛）、必须先转需求规格、中后台与大屏分工 |
| 2026-09-03 | 文档落盘后强制独立机审（结论进 review/）；人审「下一步」仍是门禁 |
| 2026-09-01 | 取消轻量/完整分流；一份一审；无已审核计划不得写业务代码 |
