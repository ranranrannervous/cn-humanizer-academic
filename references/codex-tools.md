# Codex CLI 工具映射

本 skill 原生针对 Claude Code 编写,SKILL.md 中 `allowed-tools` 字段使用 Claude Code 工具命名。
在 Codex CLI 中加载时,等价工具如下:

| Claude Code 工具 | Codex CLI 等价 | 用途 |
|---|---|---|
| Read | `shell` (cat / Get-Content) 或 Codex 文件读取原语 | 读取用户论文文件 |
| Write | `apply_patch` 或 `shell` (写文件) | 写出改写后的版本 |
| Edit | `apply_patch` | 局部替换原文 |

## 安装到 Codex CLI

```bash
git clone https://github.com/ranranrannervous/cn-humanizer-academic.git
cp -r cn-humanizer-academic/skills/cn-humanizer-academic ~/.codex/skills/
```

或者把 `skills/cn-humanizer-academic/SKILL.md` 的内容直接粘贴到 Codex 的 system prompt / instructions 区域。

## 使用注意

本 skill 主体是文本改写指导,工具调用频率很低——大部分场景是 Codex 基于 prompt 直接生成改写后的段落。
所以工具映射的精确性影响不大,关键是 SKILL.md 的内容被 Codex 读到并遵守。

## 触发方式

在 Codex CLI 对话里说:

```
按 cn-humanizer-academic skill 的 7 条硬性约束帮我改这段:
[粘贴论文文本]
```

或者直接复述触发关键词:"降 AIGC 检测率""降 AI 痕迹"等。
