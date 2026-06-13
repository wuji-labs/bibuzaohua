# 笔补造化 · Codex 适配入口

## 加载

把整个 skill 目录拷到 Codex 的 skills 目录:

```bash
cp -r labs/skills/bibuzaohua ~/.codex/skills/
```

集团默认 codex 后端为 app-server 长连接(见 ADR-0008)。skill 以纯文本规范(`SKILL.md` + `reference/`)形式加载,无运行时依赖,任何 codex 后端均可用。

## 调用

Codex 读取 `SKILL.md` 作为系统级写作规范注入上下文。建议在 prompt 或项目配置中显式引用:

```
请遵循 labs/skills/bibuzaohua/SKILL.md 的四底层原则与
reference/shijing-chuci.md 的弹药库,完成以下中文写作/重写任务。
```

执行顺序:读四底层原则 → 取弹药库相关条目 → 按「立象 / 铸骨 / 贯气 / 去饰存真」四步产出。

## 适用任务

- 中文诗词赋、铭颂悼贺等韵文生成
- 文学密度散文 / 文案 / 标题 / 序跋
- 「正确但无魂」文字的灵魂诊断与重写
- 中文写作模型微调时的审美与风骨评判标准

## 铁律提醒

引《诗经》《楚辞》原句必注书·篇;不确定就描述框架/概念,绝不杜撰原文或篇目名。
