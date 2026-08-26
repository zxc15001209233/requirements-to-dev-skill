# requirements-to-dev

一个 Cursor Agent Skill：把「通用需求规格 / 技术选型 / 开发计划」做成可跨项目使用的流程，覆盖中后台类新项目从需求到按模块验收。

不包含编码风格、排期人力、部署运维。

仓库：

- Gitee：https://gitee.com/zxc19890923/requirements-to-dev-skill
- GitHub：https://github.com/zxc15001209233/requirements-to-dev-skill

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

## 使用方式

安装后在 Cursor 里直接说即可，例如：

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

改文件必须用户输入以 `go` 开头。细则见 `SKILL.md`。

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
