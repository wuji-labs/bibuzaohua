# 笔补造化 · Cursor 适配入口

## 加载

Cursor 通过 `.cursor/rules/` 下的 `.mdc` 规则文件注入能力。把本 skill 的核心规范转为一条 project rule:

```bash
mkdir -p .cursor/rules
cp labs/skills/bibuzaohua/SKILL.md .cursor/rules/bibuzaohua.mdc
```

在 `bibuzaohua.mdc` 顶部补 Cursor frontmatter,设为按需触发(避免污染全部对话):

```
---
description: 笔补造化 — 中文文学写作/重写时启用,以诗经楚辞为弹药库
globs:
alwaysApply: false
---
```

弹药库 `reference/shijing-chuci.md` 体量较大,不必整体注入;在 `.mdc` 中以相对路径引用,需要时让 Cursor 读取:

```
弹药库详见 labs/skills/bibuzaohua/reference/shijing-chuci.md
```

## 调用

- 选中一段「正确但平庸」的中文,让 Cursor「按笔补造化重写」
- 写新文学性文本时,在 Composer 中 @ 引用 `bibuzaohua.mdc`
- 触发后 Cursor 应按四底层原则 + 「立象/铸骨/贯气/去饰存真」四步执行

## 铁律提醒

引《诗经》《楚辞》原句必注书·篇;不确定就描述框架/概念,绝不杜撰。
