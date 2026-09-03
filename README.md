# requirements-to-dev

通用 Agent Skill：**把已有材料转成大模型能执行的需求规格，再按固定顺序做到可验收的 Vue / Spring**。不绑定某一 IDE。

- 材料格式不限（docx / PDF / md / 粘贴正文 / 图），不必自己写规格模板
- **开发前必须先转需求规格**，不能拿原材料直接写代码
- 一次一份：规格 → 选型 §2 → 数据模型 → 设计契约 → 开发计划 → 实现
- 大屏 HTML 委托 `bi-dashboard-generator`；转 Vue / Spring 交回本 Skill

不覆盖编码风格、排期人力、部署运维。

仓库：

- Gitee：https://gitee.com/zxc19890923/requirements-to-dev-skill
- GitHub：https://github.com/zxc15001209233/requirements-to-dev-skill

## 效果预览

> 示例：把 PRD 和截图放进对话，对 AI 说「根据提供的材料开始开发」。先进入讨论（问歧义、出确认卡），你发 `go` 后才落盘需求规格，再一份一份走到可验收实现。

## 安装

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

## 使用方式

Agent 能读到本 Skill 后即可说，例如：

- 「根据提供的材料开始开发」（日常主入口：文件、图片、粘贴正文均可）
- 「下一步」（上一份已审，出下一份确认卡）
- 「go 执行 M1–M3」（开发计划已审核后，按范围实现）

「根据提供的材料开始开发」是**讨论**：读材料、问歧义、出确认卡。**没发 `go` 不改任何文件。**「好的 / 同意 / 可以」和这句开工话都不算 `go`。

之后按固定流程走：

```
读材料 → 本份歧义清单（未确认先问）
   ↓
出确认卡（恰好一份文档，或实现时的 Mx–My）
   ↓
go 只写这一份 → 独立机审（结论进 review/）→ 停，交人审
   ↓
用户确认「下一步」
   ↓
需求规格 → 选型 §2 → 数据模型 → 设计契约 → 开发计划（各一份、各审一次）
   ↓
实现 go（计划已审核；卡上写 Mx–My）范围内按依赖连续实现
```

项目已有总规则则协作门禁用项目的；没有时用 `SKILL.md` 默认（无 `go` 不改文件）。

## 材料怎么认

认的是「能不能读出业务文字」，不是扩展名白名单。

| 输入 | 怎么用 |
|---|---|
| PM 正文 | docx、可检索 PDF；md、txt、粘贴章节。角色、范围、规则、口径 |
| UI（可选） | Figma、Axure / HTML、截图。大屏图交给 `bi-dashboard-generator` |
| 已有需求规格 | 用户点名「按这份规格开发」时，不再从 PRD 转一遍 |

扫描件、纯图无字、表和正文对不上：先问。Sketch / XD 先导出成图或 HTML。飞书 / 在线文档请导出或把正文放进仓库。PRD、方案、需求说明叫什么都可以，都只是原材料。

混合材料（大屏 + 中后台）由本 Skill 先判定范围：大屏页只委托 HTML，其余留在本 Skill。对方 Skill 未安装则停。

## 输出

| 产物 | 说明 |
|---|---|
| 需求规格 | 一章一个功能；确定 / 待定 / 示例分开；有界面则链原型或标「待生成」 |
| 选型 §2 / 数据模型 / 设计契约 / 开发计划 | 各一份、各审一次；无已审核计划不得写 Vue / Spring |
| 业务代码 | 确认卡上的 Mx–My；大屏转 Vue 交回本 Skill |

## 文件说明

| 文件 | 作用 |
|---|---|
| `SKILL.md` | 流程、门禁、统一顺序 |
| `通用需求规格规范.md` | 需求怎么写（另有使用指南 / 示例 / 附录） |
| `通用技术选型规范.md` | 默认栈与项目覆盖 |
| `通用开发计划管理规范.md` | 怎么拆模块（另有使用指南 / 示例 / 附录） |

## License

木兰宽松许可证第 2 版（Mulan PSL v2），见 [LICENSE](./LICENSE)。

## 更新

| 时间 | 说明 |
|---|---|
| 2026-09-03 | README 按 bi-dashboard 排版：安装 → 使用方式 → 材料 → 输出 → 文件说明 |
| 2026-09-03 | 主入口「根据提供的材料开始开发」= 讨论；没 `go` 不改文件 |
| 2026-09-03 | 文档落盘后强制独立机审；人审「下一步」仍是门禁 |
