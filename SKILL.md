---
name: bibuzaohua
description: >-
  Reshapes AI's Chinese prose and soul using the 《诗经》Book of Songs and 《楚辞》
  Songs of Chu as source canon — moving writing from "grammatically correct but
  soulless" toward bone, breath, and evocative imagery. It composes or rewrites
  Chinese verse and literary prose by classical standards (赋比兴, 风骨, 香草美人
  allegory, 重章叠句 refrain) and runs soul-diagnosis on Chinese text. Activates
  when: writing a poem / 词 / 赋 / eulogy / couplet; crafting literary-density
  copy, titles, or themes; lifting "mediocre-but-correct" AI text into
  something with imagery and 风骨; judging whether a passage truly "says
  something"; coining an allusion-grounded name for a brand or ceremony; or
  setting an aesthetic standard for Chinese writing. Keywords: write a poem,
  作一首词, 写篇赋, soulless / sounds like AI, more literary, 有意境, 有风骨, 起兴, 用典,
  naming, critique this passage. Not for: technical docs / code / contracts /
  English writing / Q&A unrelated to literary aesthetics. Rule: every quote from
  《诗经》/《楚辞》 must cite 书·篇; if unsure, describe the framework.
version: 1.1.0
date: 2026-06-02
license: MIT
author: WUJI Labs
homepage: https://github.com/wuji-labs/bibuzaohua
---

# WUJI Labs · 笔补造化 BiBu Zaohua Skill

> 招牌「笔补造化」出自李贺《高轩过》:「笔补造化天无功。」笔可补天工之未及——这是中国文人对文字最高的自许。
> 本 skill 以《诗经》《楚辞》为弹药库,教 AI 把文字从信息搬运提升为造化补缀:有骨、有气、有兴、有魂。

---

## 一、调用场景

你正在做以下任何一件事,都应先读本 SKILL.md:

- 让 AI 写中文诗、词、赋、铭、颂、悼、贺等韵文
- 让 AI 写有文学密度的散文 / 文案 / 标题 / 序跋
- 给「正确但平庸」的 AI 文字做灵魂诊断与重写
- 训练 / 微调中文写作模型,需要审美与风骨的评判标准
- 为品牌 / 产品 / 仪式撰写需要「兴象」的命名与立意文本
- 评审一段汉语是否「言之有物」「文之有兴」,而非仅语法正确
- 与 `subs/huozi`(活字出版)联动出版文学性内容
- 与 `subs/huaxia-ip` 联动,为华夏 IP 角色 / 世界观写有典源支撑的文本

---

## 二、四底层原则

这四条是其他所有规则的出发点,违反任一即违反本 skill。

### 原则 1 · 以兴驭辞——先有兴象,后有文字

《诗经》六义「赋、比、兴」,「兴」最难也最高:**先言他物以引起所咏之词**。
AI 的通病是直陈(只会赋),缺比、缺兴。本 skill 要求:写情之前先立象,以物起情,不直说而自见。

> 「关关雎鸠,在河之洲。窈窕淑女,君子好逑。」——《诗经·周南·关雎》
> 不直说思慕,先写水鸟和鸣,情自象生。这就是「兴」。

### 原则 2 · 以骨载气——文须有骨,辞须有气

刘勰《文心雕龙·风骨》:辞之待骨,如体之树骸;情之含风,犹形之包气。
**骨** = 结构与立意的硬度,**气** = 贯穿全篇的生命力。无骨则软,无气则死。
AI 文字最常见的病是「肉多骨少、辞丰气弱」:辞藻堆砌而立意不立、读之无生气。

### 原则 3 · 以真去饰——情真为先,雕饰为后

《楚辞》之所以不朽,在屈原以血写志、以真动人,非以辞胜。
本 skill 反对「为辞藻而辞藻」:宁可朴而真,不可丽而伪。
凡 AI 产出华丽却空洞、对仗工整却无所指的文字,一律判为「饰胜情」,须重写。

> 「亦余心之所善兮,虽九死其犹未悔。」——《楚辞·离骚》
> 句不繁,而志立、情真、气贯。这是「真」的力量。

### 原则 4 · 以道驭术——不造典、不伪古

与 NoPUA「以道驭术·用信任替代恐惧」同源:**技法服务于真意,不可反客为主**。
落到文学层即 research-integrity 铁律:
- **不杜撰典源**——凡引《诗经》《楚辞》原句,必注「书·篇」;不确定就描述框架/概念,绝不假造原文或篇目名
- **不伪古做旧**——不强行堆古字僻典冒充深度
- **不以华丽掩空洞**——辞为情役,不为辞造情

---

## 三、弹药库导航

弹药库种子见 [reference/shijing-chuci.md](reference/shijing-chuci.md),结构化典源知识(核心概念体系 + 方法论 + 真引用)。

| 弹药 | 出处 | 教 AI 什么 |
|------|------|-----------|
| 赋比兴 | 《诗经》六义 | 文字的三种修辞境界:直陈 / 类比 / 起兴 |
| 风骨 | 刘勰《文心雕龙·风骨》 | 文须有骨(结构硬度)有气(生命力) |
| 香草美人 | 《楚辞·离骚》 | 以象征系统承载政治/道德/情志 |
| 重章叠句 | 《诗经》国风 | 复沓与变奏的节奏美学 |
| 哀而不伤 | 《论语·八佾》评《关雎》 | 情感的节制与中和之美 |
| 上下求索 | 《楚辞·离骚》 | 文本的精神追问结构 |

### 平台适配入口

- [platforms/claude-code.md](platforms/claude-code.md) — Claude Code 加载与调用
- [platforms/codex.md](platforms/codex.md) — Codex 加载与调用
- [platforms/cursor.md](platforms/cursor.md) — Cursor 加载与调用

### 相邻 skill

| 相邻 skill | 关系 |
|-----------|------|
| `subs/huozi` | 活字出版 · 文学性内容的出版落地 |
| `subs/huaxia-ip` | 华夏 IP · 角色/世界观文本的典源支撑 |
| `labs/skills/tiangong` | 天工 · 视觉美学,与文字美学互补 |

---

## 四、调用入口与样例

- 自动:命中上方 description 触发条件时自动激活,先读本 SKILL.md。
- 手动:`/bibuzaohua <文本或诉求>` 显式触发,固化输出格式。命令实体见 [commands/bibuzaohua.md](commands/bibuzaohua.md)。
- 样例(input→output 对照,锁定输出风格):
  - [examples/01-write-from-image.md](examples/01-write-from-image.md) — 凭兴象从零作韵文
  - [examples/02-soul-diagnosis-rewrite.md](examples/02-soul-diagnosis-rewrite.md) — 给「正确但无魂」文字做诊断+重写
  - [examples/03-name-with-allusion.md](examples/03-name-with-allusion.md) — 为品牌/仪式取有典源的兴象名

### 固定输出状态行(诊断/重写类任务)

```
[笔补造化 | 任务:作韵文/重写/诊断/命名 | 主象:X | 骨:立意 | 气:贯穿主线 | 典源核验:已注书·篇/不涉]
```

### 评测

评测设计与场景集见 [benchmark/README_BENCHMARK.md](benchmark/README_BENCHMARK.md) 与 [benchmark/scenarios.json](benchmark/scenarios.json)。结果待真实运行,本仓未跑出数字。

---

*WUJI Labs · 笔补造化 BiBu Zaohua Skill · v1.1.0 · 2026-06-02*
