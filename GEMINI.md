# cn-humanizer-academic — Gemini CLI 入口

这是一个中文学术论文降 AIGC 检测率的 skill,主体内容在 `skills/cn-humanizer-academic/SKILL.md`。

## Gemini CLI 加载方式

将本仓库 clone 到 Gemini 的 skills 目录后,本 skill 会通过 `activate_skill` 工具被激活。

```bash
git clone https://github.com/ranranrannervous/cn-humanizer-academic.git ~/.gemini/skills/cn-humanizer-academic
```

激活方式(在 Gemini CLI 对话里):

```
请激活 cn-humanizer-academic skill 帮我改这段:
[粘贴中文论文段落]
```

## 工具映射

本 skill 在 SKILL.md 里声明 `allowed-tools: Read, Write, Edit`(Claude Code 命名)。
Gemini CLI 等价工具:

| Claude Code | Gemini CLI |
|---|---|
| Read | read_file |
| Write | write_file |
| Edit | replace |

实际本 skill 主要做文本重写,工具调用极少,大部分时间是 Gemini 直接基于 prompt 生成改写文本。

## 触发关键词

- "降 AI 率""降 AIGC""中文论文 AI 痕迹"
- "知网 AIGC 检测""维普 AI 检测""BERT 检测器"
- "论文被判定 AI""降 AI 检测率"

详见 SKILL.md。
