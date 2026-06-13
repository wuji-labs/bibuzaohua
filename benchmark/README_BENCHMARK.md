# 笔补造化 BiBu Zaohua — Benchmark Design

> **⚠️ 结果待真实运行。本文件是评测设计,不是评测结果。**
> 本仓库 **不含任何 before/after 数字、得分、p 值、效应量或胜率**。所有此类数字必须由你在本地真实运行后产出。
> research-integrity 铁律:在跑出真实数据之前编造统计结果,直接违反本 skill 第四原则「以道驭术·不造」。

---

## 1. 评测目的

衡量启用 `bibuzaohua` skill 是否让 AI 的汉语写作 / 重写 / 命名 / 诊断:

- 从「只会赋(直陈)」走向「会兴(立象起情)」;
- 从「肉多骨少、辞丰气弱」走向「有骨有气」;
- 从「饰胜于情」走向「以真去饰」;
- 在反触发场景(技术文档)保持平直、不滥施辞藻;
- 在伪造典源陷阱前 **拒绝杜撰**,不把假引用当真。

## 2. 对照条件设计(baseline vs skill)

| 条件 | 系统提示 | 含义 |
|------|----------|------|
| **baseline** | 通用「请完成这个写作/重写/命名任务」 | 不加载 skill 的原生模型 |
| **bibuzaohua** | 完整 `SKILL.md` + `reference/shijing-chuci.md` | 加载本 skill |

可选第三条件(消融):**ornament**——只给「写得华丽文艺一点」的提示,用于区分「真有兴象风骨」与「只是堆辞藻」。

每条件 × 每场景 ≥ 5 次重复运行,降低单次抽样波动。

## 3. 题库

`scenarios.json` 含 8 个场景,覆盖五类:

| category | 场景 | 考点 |
|----------|------|------|
| compose-verse | 1, 6 | 立象起兴、哀而不伤、有骨有气 |
| diagnose-rewrite | 2, 7 | 诊断有骨吗/有气吗、去饰存真 |
| naming | 3, 8 | 真典源命名、系统性象征 |
| integrity-trap | 4 | **伪造典源拒绝**(一票否决项) |
| anti-trigger | 5 | 反触发场景保持平直 |

每场景含:`description`(ground truth,不给 agent)、`task`(给 agent 的 prompt)、`expected_actions`、`difficulty`。

## 4. 评分 rubric

### 4.1 expected_actions 命中率(客观)

对每次运行,逐条核对 `expected_actions` 是否被满足(0/1),命中率 = 命中条数 / 总条数。这是主指标,可自动或人工标注。

### 4.2 维度评分(1–5,人工或 LLM-judge 双盲)

| 维度 | 1 分 | 5 分 |
|------|------|------|
| 兴(立象) | 全程直陈,无象 | 先立象、情自象生 |
| 骨(立意/结构) | 辞藻堆砌、立意空 | 立意硬、结构立得住 |
| 气(贯穿) | 字字正确而无生气 | 一线生命力贯穿首尾 |
| 真(去饰) | 饰胜于情、对仗无所指 | 辞为情役、句句有所指 |
| 节制(哀而不伤) | 情感泛滥/堆形容词 | 情感节制、留白动人 |

### 4.3 一票否决:典源诚信(integrity gate)

适用于 **场景 4(伪造陷阱)** 与任何引用古籍的运行:

- 若把伪造句当作《诗经/楚辞》原文接受、复述或为其编造篇目 → **该次运行 integrity = FAIL,整次记 0 分**,不论其余维度多高。
- 真引用必须可核到「书·篇」;不确定时只描述框架视为合格。

> 这一项对应 skill 第四原则,也对应本仓 research-integrity 铁律——评测自身亦不得编造。

### 4.4 反触发正确性(场景 5)

技术文档场景中,若注入古典辞藻/强加意境 → 判为 over-trigger 失分;保持平实直陈 → 满分。衡量 skill 是否「该出手时出手,不该出手时不扰」。

## 5. 统计方法(待真实数据后执行)

- **Wilcoxon signed-rank**:同场景 × 同 run 跨条件配对比较(非参数,适合小样本)。
- **Mann-Whitney U**:非配对回退。
- **Cohen's d / rank-biserial r**:效应量。|d|<0.2 可忽略,0.2–0.5 小,0.5–0.8 中,>0.8 大。
- 显著性:`*` p<0.05,`**` p<0.01,`***` p<0.001,`n.s.` 不显著。

> 上述阈值是统计学通用判据,**非本 skill 的实测结果**。

## 6. CLI 用法(参考 nopua 范式)

```bash
# 全条件全场景,各 5 次
python run_benchmark.py --model claude-opus-4 --condition all --runs 5

# 单条件
python run_benchmark.py --model gpt-4o --condition bibuzaohua --runs 5

# 单场景调试
python run_benchmark.py --model gemini-2.5-pro --scenario 4 --condition baseline --runs 1

# 干跑(只打印计划)
python run_benchmark.py --model claude-opus-4 --condition all --dry-run

# 分析(仅在有真实 results 时产出数字)
python analyze_results.py --input-dir results/ --plots --json-report
```

> 注:`run_benchmark.py` / `analyze_results.py` 为可选加分件,本目录暂未交付执行器;评测可先以人工 + LLM-judge 按本 rubric 运行。交付时不预置任何 results。

## 7. 输出结构

```
benchmark/
├── scenarios.json          # 8 场景(本仓已交付)
├── README_BENCHMARK.md     # 本文件:评测设计
└── results/                # 真实运行后自动生成(本仓为空)
    ├── <model>_baseline.json
    └── <model>_bibuzaohua.json
```

每条 result 记录建议字段:`scenario_id / condition / model / run_number / timestamp / expected_actions_hit / dim_scores{xing,gu,qi,zhen,restraint} / integrity_pass / output_text / notes`。

## 8. 成本估算(量纲,非实测)

每全跑 = 8 场景 × 2 条件 × 5 次 = 80 次生成调用(+ 若用 LLM-judge 再 80 次评分调用)。具体 token 与费用取决于模型与输出长度,运行前以 `--dry-run` 核算,**不在此预填具体金额**。

## 9. 如何加场景

在 `scenarios.json` 追加:

```json
{
  "id": 9,
  "category": "compose-verse|diagnose-rewrite|naming|integrity-trap|anti-trigger",
  "name": "简短名",
  "description": "ground truth(不给 agent)",
  "task": "给 agent 的 prompt",
  "expected_actions": ["合格响应应做的事"],
  "difficulty": "easy|medium|hard"
}
```

加 integrity-trap 类时,务必确保「伪造句」确非《诗经/楚辞》原文,且 ground truth 明确要求 agent 拒绝。

---

*WUJI Labs · 笔补造化 BiBu Zaohua · Benchmark Design · 结果待真实运行*
