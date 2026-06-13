# 笔补造化 BiBu Zaohua — 给 AI 的汉语以骨、气、兴象

> **笔补造化天无功** ——李贺《高轩过》。笔可补天工之未及,这是中国文人对文字最高的自许。

**一句话:你的 AI 写的中文「语法正确但没灵魂」——本 skill 以《诗经》《楚辞》为弹药库,给它骨、气、兴象。**

这是华夏道脉献给世界开源社区的十件礼物之一。我们不立华夏本位、不主张任何文明优于他者;只是先从自己最熟悉的道脉开始,把它打磨成一件可用工具,放上人类共同的开源工具架。

---

## 它解决什么

AI 写中文最常见的三种病:

| 病 | 表现 | 本 skill 的药 |
|----|------|---------------|
| 只会赋 | 直说「我很想你」,无象 | **兴**:先立象,情自象生 |
| 肉多骨少 | 辞藻堆砌、立意空 | **风骨**:铸硬立意为骨、贯一气 |
| 饰胜于情 | 对仗工整却无所指 | **去饰存真**:辞为情役,不为辞造情 |

## 能力对照(Before / After)

| | 未启用 | 启用后 |
|--|--------|--------|
| 思念 | 我很想你,日日夜夜思念(直陈) | 先写河洲水鸟,思自象生(兴) |
| 茶文案 | 高山云雾,匠心独运,极致享受(肉多骨少) | 晨雾里凉在叶尖的一只手——一象承意 |
| App 取名 | 致远星辰(好看无出处) | 修远——《离骚》「路漫漫其修远兮」,象与「长期坚持」同构 |

完整 input→output 见 [examples/](examples/)。

## 适用场景

- 写诗 / 词 / 赋 / 铭 / 颂 / 悼 / 贺 / 序跋 / 对联等韵文
- 写有文学密度的文案 / 标题 / 立意
- 给「正确但平庸」的 AI 文字做灵魂诊断与重写
- 为品牌 / 产品 / 仪式取有典源的兴象名
- 评判一段汉语是否「言之有物、文之有兴」
- 建立中文写作的审美评判标准

**反触发(不该用)**:技术文档 / API 说明 / 代码注释 / 法律合同 / 数据报表 / 英文写作——保持平实直陈即可。

## 安装

### 作为 Claude Code 插件(一键)
```bash
/plugin marketplace add wuji-labs/bibuzaohua
/plugin install bibuzaohua
```

### 裸 clone / 拷贝
```bash
cp -r labs/skills/bibuzaohua ~/.claude/skills/   # 或 ~/.codex/skills/
```

平台说明:[claude-code](platforms/claude-code.md) · [codex](platforms/codex.md) · [cursor](platforms/cursor.md)。

## 调用方式

| 方式 | 用法 | 何时 |
|------|------|------|
| 自动 | 直接提中文写作 / 重写 / 命名 / 诊断诉求 | 命中触发词即自动激活 |
| 手动 | `/bibuzaohua <文本或诉求>` | 显式触发 + 固定输出格式,见 [commands/bibuzaohua.md](commands/bibuzaohua.md) |

## 方法论背书与溯源

- 招牌:李贺《高轩过》「笔补造化天无功」
- 赋比兴:《诗经》六义 · 风骨:刘勰《文心雕龙·风骨》 · 香草美人:《楚辞·离骚》 · 哀而不伤:《论语·八佾》
- **凡引原句必注「书·篇」,不杜撰**。真引用索引见 [reference/shijing-chuci.md](reference/shijing-chuci.md)。
- 评测仅交付设计,**不含任何编造数字**,见 [benchmark/README_BENCHMARK.md](benchmark/README_BENCHMARK.md)。
- 与 [NoPUA](https://github.com/wuji-labs/nopua)「以道驭术」同源:技法服务真意,不可反客为主。

## 许可

MIT · WUJI Labs · github.com/wuji-labs/bibuzaohua

---

*笔补造化 BiBu Zaohua — 笔补造化。写,要有骨、有气、有兴象。*
