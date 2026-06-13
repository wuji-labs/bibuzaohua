# 笔补造化 · Claude Code 适配入口

## 加载

把整个 skill 目录拷到 Claude Code 的 skills 目录:

```bash
cp -r labs/skills/bibuzaohua ~/.claude/skills/
```

或在 monorepo 内,本 skill 已位于 `labs/skills/bibuzaohua/`,Claude Code 会按项目级 skill 自动发现。

## 调用

Claude Code 通过 `SKILL.md` 的 frontmatter(`name: bibuzaohua` + `description`)做语义匹配。触发时机:

- 你显式说「用笔补造化 / bibuzaohua」
- 你让我写中文诗词赋、有文学密度的散文/文案/标题/序跋
- 你让我给「正确但平庸」的中文文字做灵魂诊断与重写
- 你让我评判一段汉语是否「言之有物、文之有兴」

触发后我会先读 `SKILL.md`(四底层原则)→ 按需读 `reference/shijing-chuci.md`(弹药库)→ 用「立象/铸骨/贯气/去饰存真」四步产出或重写。

## 与相邻 skill 协作

- 出版文学性成稿 → 联动 `subs/huozi`(活字出版)
- 为华夏 IP 角色/世界观写有典源支撑的文本 → 联动 `subs/huaxia-ip`
- 配套视觉美学 → 联动 `labs/skills/tiangong`

## 铁律提醒

引《诗经》《楚辞》原句必注书·篇;不确定就描述框架/概念,绝不杜撰。详见 `reference/shijing-chuci.md` 第五节真引用索引。
