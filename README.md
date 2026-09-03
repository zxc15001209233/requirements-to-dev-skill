# requirements-to-dev

把已有材料转成大模型能执行的**需求规格**，再按固定顺序做到可验收的 Vue / Spring。不绑定 IDE。不管编码风格、排期、部署。

- Gitee：https://gitee.com/zxc19890923/requirements-to-dev-skill
- GitHub：https://github.com/zxc15001209233/requirements-to-dev-skill

## 怎么用

把材料放进对话或仓库，说：

> 根据提供的材料开始开发

这是**讨论**：读材料、问歧义、出确认卡。**没发 `go` 不改任何文件。**「好的 / 同意 / 可以」和这句开工话都不算 `go`。

| 你说 | 阶段 |
|---|---|
| 「根据提供的材料开始开发」 | 讨论；先出需求规格确认卡，不写代码 |
| 对确认卡发 `go` | 只落盘卡上那一份 |
| 「下一步」 | 再讨论下一份；仍要再 `go` 才写 |
| 「go 执行 M1–M3」 | 仅计划已审核后，按范围实现 |

一次一份：需求规格 → 选型 §2 → 数据模型 → 设计契约 → 开发计划 → 实现。无已审核计划不得写 Vue / Spring。每份落盘后写 `review/`，再等人审。

项目已有总规则则跟项目的；否则跟 `SKILL.md`（无 `go` 不改文件）。

## 材料

格式不限，能读出业务文字即可（docx / 可检索 PDF / md / 粘贴正文；可选 Figma、原型、截图）。PRD、方案、需求说明都只是原材料，**不能直接当实现依据**。扫描件、纯图无字先问。已有按本规范写好的规格且用户点名按它开发时，不再从 PRD 转一遍。

大屏 HTML 委托 `bi-dashboard-generator`（未安装则停）；转 Vue / Spring 交回本 Skill。混合材料由本 Skill 先判定范围，禁止两边各做一整份。

**不要只拷 `SKILL.md`**，附件是同目录 `通用*.md`。

## 安装

```bash
# Gitee（国内推荐）；第一条当前项目，-g 全局
npx skills add https://gitee.com/zxc19890923/requirements-to-dev-skill.git
npx skills add https://gitee.com/zxc19890923/requirements-to-dev-skill.git -g

npx skills add zxc15001209233/requirements-to-dev-skill
npx skills add zxc15001209233/requirements-to-dev-skill -g
```

不支持 `skills add` 时：整目录放进项目，指令里写先读本目录 `SKILL.md`。

木兰宽松许可证第 2 版，见 [LICENSE](./LICENSE)。
