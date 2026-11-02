# 学术技能包（dsh-academic-skills）

给 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 的四个科研技能，面向硕博研究生的真实工作流。中文，模型无关。

> 不是又一个 AI 聊天框，是把一堆论文变成**每条结论都能回溯到原文**的文献卡片和综述大纲。

## 30 秒安装

```bash
dsh plugin add dsh-academic-skills
```

装完新开一个会话，问一句「你现在有哪些技能」。

## 它解决什么问题

- 读了 50 篇 PDF，最后只剩聊天记录？→ 每篇变成 `cards/*.md`，可检索、可 git、可交接。
- 综述写到最后不知道哪句话出自哪篇？→ 大纲每个论点标注来源卡片。
- 模型一本正经编造？→ 缺失信息强制标【原文未提及】，不补、不猜。
- 论文格式被导师打回？→ GB/T 7714 / APA 7 / AMA / MLA 9 一键重排，附变更清单。

## 四个技能

| 技能 | 做什么 | 产出 |
|---|---|---|
| `literature-card` | 精读论文，生成结构化文献卡片；多篇时做横向对比 | `cards/*.md` |
| `citation-format` | 按目标规范重排整篇论文与参考文献，只改格式不改内容 | `formatted/*.md` |
| `journal-polish` | 按目标期刊文风润色（语法纠错 / 学术升级 / 精简压缩） | `polished/*.md` |
| `review-outline` | 基于卡片生成综述分层大纲，含可检验的研究缺口 | `review/outline.md` |

四个技能靠**文件**串起来，不靠聊天历史：

```
你的项目/
├── papers/       放 PDF、docx、txt
├── cards/        技能生成的文献卡片
├── review/       综述大纲与对照矩阵
├── formatted/    格式转换后的论文
└── polished/     润色后的段落
```

## 使用示例

**批量精读**

> 读 `papers/` 下所有 PDF，每篇生成一张文献卡片放到 `cards/`，做完写一份横向对比。

**出综述大纲**

> 基于 `cards/` 里的卡片，按“背景 / 时间线 / 分支 / 争议 / 研究缺口 / 展望”生成综述大纲，每个观点标出来源。

**投稿前**

> 把 `draft.md` 的参考文献按 GB/T 7714-2015 重排，正文格式一起改，输出变更清单。

## 安装方式

**方式一：npm（推荐）**

```bash
dsh plugin add dsh-academic-skills
```

**方式二：本地包**

在 [Releases](../../releases) 下载 `.tgz`，DSH → 插件 → 添加插件 → 填 tgz 的绝对路径。

**方式三：直接复制技能文件（不用插件系统）**

把 `skills/*.md` 复制到 `~/.dsh/skills/`（Windows：`%USERPROFILE%\.dsh\skills\`），重启会话即可。

## 设计原则

- **卡片是唯一数据源**：后续技能只读卡片，不重读全文，省 token，也避免前后不一致。
- **不编造**：缺失信息标【原文未提及】；扫描件读不出文字会停下提示，不会凭标题瞎写。
- **来源可回溯**：卡片记录原始文件路径；大纲标来源卡片。
- **隐私**：不记录学号、身份证号、手机号等与学术判断无关的个人信息。
- **主题不一致就说**：几篇论文不是一个题目时，明确告诉你，不硬凑对比。

## 兼容性

- 需要 DSH `>= 0.2.0`
- 与模型无关：DeepSeek、GPT、Claude、本地模型都能用
- 不依赖任何网关或 API Key

## 开发

```bash
# 修改 skills/*.md 后重新打包
npm pack
# 本地安装验证
dsh plugin add ./dsh-academic-skills-<version>.tgz
```

## License

MIT
