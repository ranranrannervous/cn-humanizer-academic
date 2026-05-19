# cn-humanizer-academic

中文学术论文降 AIGC 检测率 Skill,针对知网 4.0+ / 维普 / PaperPass 等基于 **BERT 语义分类模型** 的检测器,从语义结构层深度改写文本,而非简单的词汇替换。

## 针对哪些 AI 痕迹

基于 BERT 的语义分类器主要抓以下几类特征,本 skill 全部覆盖:

- 段落整体的"AI 标准化结构"(总分总、三段分类)
- 句子之间的"过度逻辑流畅"(因果链严密、过渡完美)
- 抽象论述 vs 具体细节比例失衡(空话多、细节少)
- "客观全面、无观点"的 AI 标志语调
- 段落深度、长度的"均匀感"(每段篇幅相近、每点展开度一致)
- AI 高频词(此外、综合来看、至关重要、进行了、通过 等)
- 句长过度均匀(连续多句都是 30+ 字)

## 从哪些方面更改

通过 **7 条硬性约束 + 5 大重写策略** 对文本进行结构级重写。

### 7 条硬性约束

| 约束 | 内容 |
|---|---|
| 字数控制 | 改写后字数 ≤ 原文 × 1.2 |
| 禁止加粗 | 正文不使用 markdown 加粗,关键概念用引号 |
| 引用守界 | 严格只用原文已有 `[N]` 编号,不新增文献 |
| 学术度红线 | 避免"一直在涨""麻烦的地方"等口语化表述 |
| 修辞节制 | 每段引号 0-2 处、破折号 0-2 处,反问/类比全文 1-2 处 |
| 内容守界 | 补充细节必须是领域常识,不凭空捏造数据 |
| 段落上限 | 单段最多拆为 4 段 |

### 5 大重写策略

| 策略 | 改的是什么 |
|---|---|
| A. 打破工整结构 | 段落长度 / 分点详略故意不均衡 |
| B. 破坏过度流畅 | 因果链中间插入补充、回顾、跳跃 |
| C. 抽象 → 具体 | 抽象动词("影响""作用""体现")替换为具体观察 |
| D. 加入侧重判断 | 用"主要解决的是 X""关键的一点"等研究者口吻 |
| E. 词汇层清扫 | 删 / 替换 AI 高频词 |

## 安装

### 方式 1:Plugin Marketplace(一行安装)

```
/plugin marketplace add ranranrannervous/cn-humanizer-academic
/plugin install cn-humanizer-academic@cn-humanizer-academic
```

### 方式 2:手动 clone

```bash
git clone https://github.com/ranranrannervous/cn-humanizer-academic.git
cp -r cn-humanizer-academic/skills/cn-humanizer-academic ~/.claude/skills/
```

### 方式 3:Codex CLI

```bash
git clone https://github.com/ranranrannervous/cn-humanizer-academic.git
cp -r cn-humanizer-academic/skills/cn-humanizer-academic ~/.codex/skills/
```

工具映射详见 [`references/codex-tools.md`](references/codex-tools.md)。

### 方式 4:Gemini CLI

```bash
git clone https://github.com/ranranrannervous/cn-humanizer-academic.git ~/.gemini/skills/cn-humanizer-academic
```

Gemini CLI 会自动加载根目录的 `GEMINI.md`,通过 `activate_skill` 激活。

## 使用

在对话里说:

```
帮我用语义层降低这段的 AI 痕迹
[粘贴文本]
```

或者:

```
帮我改这段降 AIGC 检测率
[粘贴文本]
```

模型会自动触发本 skill。

## 适用范围

✅ 中文毕业论文(本科 / 硕士 / 博士)
✅ 中文期刊论文
✅ 中文综述
✅ 中文技术报告
❌ 英文论文(BERT 中文版和英文版指纹不同)
❌ 营销文案 / 公众号文章

## License

MIT
