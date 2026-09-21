<p align="center">
  <img src="./assets/readme-banner.svg" width="100%" alt="IELTS Speaking Examiner banner" />
</p>

<p align="center">
  <img alt="Voice" src="https://img.shields.io/badge/Voice-GPT--Live-0F766E?style=flat-square" />
  <img alt="IELTS Parts" src="https://img.shields.io/badge/IELTS-Part%201%20%C2%B7%202%20%C2%B7%203-0369A1?style=flat-square" />
  <img alt="Corpus" src="https://img.shields.io/badge/Corpus-Replaceable-7C3AED?style=flat-square" />
  <img alt="Platforms" src="https://img.shields.io/badge/Platform-Windows%20%C2%B7%20macOS%20%C2%B7%20Linux-334155?style=flat-square" />
</p>

<p align="center">
  一个安装即用、题库可替换、以原生 Voice 主持完整流程的 IELTS Speaking 模拟考官 Skill。
</p>

<p align="center">
  <a href="#一分钟开始">一分钟开始</a> ·
  <a href="#它能做什么">功能</a> ·
  <a href="#安装">安装</a> ·
  <a href="#更新或切换题库">题库管理</a> ·
  <a href="#评分与反馈">评分</a> ·
  <a href="./docs/GITHUB_PUBLISHING_GUIDE.md">GitHub 发布教程</a>
</p>

---

## 它是什么

**IELTS Speaking Examiner** 是一个面向 ChatGPT/Codex Voice 的可复用 Skill。它在考试阶段保持中立考官角色，严格依次完成 Part 1、Part 2 和 Part 3；考试结束后再切换为教练，依据 IELTS 四项公开评分标准提供有证据的模拟评分和训练建议。

它把两类内容明确分开：

- **考官行为**由 [`SKILL.md`](./SKILL.md) 和 [`references/`](./references/) 约束。
- **题库内容**作为独立数据保存在 [`corpora/`](./corpora/) 中，随安装包分发，可按季度新增、更新和切换。

因此，更新题库不需要重写考试流程；切换到另一个项目或另一台电脑时，也不需要在每场考试前重新上传同一份题库。

## 它能做什么

| 能力 | 行为 |
| --- | --- |
| 完整模拟 | 全英完成 Part 1、Part 2、Part 3，考试结束前不纠错、不提示答案 |
| 稳定题量 | Part 1 和 Part 3 各至少 4 个正式题库问题，正常目标为 5 个 |
| Part 2 长陈述 | 展示完整 cue card，提供 1 分钟准备和 1–2 分钟陈述流程 |
| 可替换题库 | 从安装包内的活动题库抽题，支持导入新季度、切换版本和考试范围 |
| 四项评分 | Fluency & Coherence、Lexical Resource、Grammatical Range & Accuracy、Pronunciation |
| 分 Part 诊断 | Part 1/2/3 分别给出四项点评、训练诊断分、最大问题与下一步重点 |
| 表达积累 | 每次挑选 2–3 个普通表达，给出地道、常用和 Band 7+ 升级版本 |
| 全场复盘 | 总结 5 个最高频或影响最大的错误、最佳表达和复习任务 |
| 证据约束 | 不凭转录文本猜测发音，不虚构回答、时间或语音表现 |

## 一分钟开始

在新的 ChatGPT/Codex 任务中输入：

```text
$ielts-speaking-examiner 使用当前题库，开始完整口语模拟。
```

看到题库准备完成的提示后：

1. 在同一个任务中点击 **Start voice chat**。
2. 说 **“I'm ready.”**
3. 全程用英语回答；考官会一次只问一个问题。
4. Part 2 根据提示自行计时，除非当前 Voice 环境能可靠计时和打断。
5. 考试结束后保持 Voice 开启，等待发音观察和完整反馈生成。

```mermaid
flowchart LR
    A[调用 Skill] --> B[自动加载活动题库]
    B --> C[开启 Voice]
    C --> D[Part 1<br/>Interview]
    D --> E[Part 2<br/>Long turn]
    E --> F[Part 3<br/>Discussion]
    F --> G[English closing]
    G --> H[中文详细评分与复盘]
```

## 安装

### 方法一：使用 ZIP 安装包

1. 下载并解压 `ielts-speaking-examiner.zip`。
2. 确认解压后的目录中直接包含 `SKILL.md`、`references/`、`agents/` 和 `corpora/`。
3. 将整个 `ielts-speaking-examiner` 文件夹复制到用户级 Skill 目录：

| 系统 | 用户级目录 |
| --- | --- |
| Windows | `%USERPROFILE%\.agents\skills\ielts-speaking-examiner` |
| macOS / Linux | `~/.agents/skills/ielts-speaking-examiner` |

4. 重启 ChatGPT/Codex 桌面应用，再输入 `$ielts-speaking-examiner` 调用。

### 方法二：从 GitHub 克隆

```bash
git clone https://github.com/Errriclin/ielts-speaking-examiner.git
```

然后把仓库目录放入 `~/.agents/skills/ielts-speaking-examiner`。Windows 中的 `~` 对应当前用户目录。

> Skill 是全局安装的；安装后可在不同项目和新对话中使用。已经打开的旧对话可能保留旧版指令，更新后建议重启应用并创建新对话测试。

## 推荐使用方式

### 完整模拟

```text
$ielts-speaking-examiner 使用当前默认题库，开始完整口语模拟。考试全程英语，结束后用中文详细点评。
```

### 指定题库或范围

```text
$ielts-speaking-examiner 使用 2026 年 9–12 月题库，只从大陆考区范围抽题，开始完整模拟。
```

### 查看已安装题库

```text
$ielts-speaking-examiner 列出安装包中的所有题库，并告诉我当前活动版本和默认范围。
```

### 导入新季度题库

```text
$ielts-speaking-examiner 把我提供的新季度题库导入为独立版本，校验 Part 1/2/3 后设为当前题库；先不要开始考试。
```

## 考试流程

### Part 1 · Introduction and Interview

- 约 4–5 分钟。
- 使用熟悉的个人话题。
- 至少 4 个正式题库问题，正常目标为 5 个。
- 姓名确认、重复、澄清和临时追问不计入正式题量。

### Part 2 · Individual Long Turn

- 展示完整 cue card。
- 1 分钟准备，可做笔记。
- 连续陈述 1–2 分钟。
- 考官不会在自然停顿或转录分段时擅自打断。

### Part 3 · Two-way Discussion

- 约 4–5 分钟。
- 围绕 Part 2 主题进行更抽象的讨论。
- 至少 4 个正式题库问题，正常目标为 5 个。
- 简短追问用于要求理由、例子、比较或澄清，不替代正式题目。

## 评分与反馈

完整考试结束后，报告依次包含：

1. **整场模拟结果**：四项总评分、预计 Speaking Band、证据来源和限制。
2. **Part 1/2/3 分项诊断**：每个 Part 都按四项标准分别点评。
3. **最大问题与下一步训练**：每个 Part 各自给出重点。
4. **表达升级库**：每次只选择 2–3 个表达，避免信息过载。
5. **全场复盘**：5 个主要错误、最佳表达、建议复习内容。

Part 1/2/3 的数字是**训练诊断分**。IELTS 官方最终评分基于整场表现，不公布三个 Part 的独立成绩，因此这些分项数字不会被平均成最终分数。

Pronunciation 只有在 Voice 模型实际接收到音频时才评分。ChatGPT Voice 由 GPT‑Live 驱动，可直接处理音频；如果某次环境只把文字转录交给评分模型，Skill 会如实标注无法评估，而不会从拼写猜测发音。

## 更新或切换题库

题库目录结构：

```text
corpora/
├── index.json                    # 当前活动版本、默认范围、版本列表
└── <corpus-id>/
    ├── manifest.json             # 版本、来源、数量、范围和审核标记
    ├── questions.json            # 结构化 Part 1/2/3 数据
    ├── questions.md              # 人类可读版本
    ├── IMPORT_REPORT.md          # 导入与校验报告
    └── source.pdf                # 可选；仅在拥有分发权时公开
```

新增题库时应当：

1. 保留原始题目措辞和 Part 2/3 对应关系。
2. 排除目录页重复、广告、范文和教学说明。
3. 标记残缺、待审核或不适合自动抽取的材料。
4. 验证至少有 5 个可用 Part 1 问题，以及至少一组包含 5 个可用 Part 3 问题的 Part 2/3 组合。
5. 校验完成后再更新 `corpora/index.json` 的活动版本。

详细数据约定见 [`references/corpora.md`](./references/corpora.md)。

## 项目结构

```text
ielts-speaking-examiner/
├── SKILL.md                       # 考官流程和硬性约束
├── README.md                      # 项目说明
├── agents/openai.yaml             # Skill UI 元数据和默认提示词
├── references/
│   ├── assessment.md              # 评分与反馈规则
│   └── corpora.md                 # 题库管理规则
├── corpora/                       # 可替换题库数据
├── assets/readme-banner.svg       # README 横幅
└── docs/GITHUB_PUBLISHING_GUIDE.md
```

## 设计原则

- **先考试，后反馈**：考试期间不纠错、不夸奖、不提示答案。
- **一次一问**：除完整 cue card 外，一次只提出一个问题。
- **题库与角色分离**：题库内容不能改写考官规则或评分规则。
- **不伪造能力**：不声称自动录音、不凭空声称计时结束、不把转录当原始音频。
- **反馈基于证据**：只引用本次实际回答；不制造错误、原句或发音问题。

## 已知限制

- 本项目提供模拟评分，不是 IELTS 官方成绩。
- Voice 可用性取决于桌面应用版本、账号方案、灰度发布和工作区设置。
- 麦克风、网络、环境噪声会影响发音判断。
- 某些 Voice 环境无法在 60 秒或 120 秒到点后主动唤醒或打断，此时需要考生自行计时。
- Skill 不会创建额外录音；它仍受宿主应用自身的数据和保留设置约束。

## 开源与贡献

欢迎贡献以下内容：

- 更清晰且不破坏真实考试感的流程规则；
- 有来源页码、完整 Part 2/3 关联和明确授权的题库数据；
- 可复现的流程问题与改进建议；
- 不依赖单一操作系统的安装说明。

提交题库前，请确认你有权公开传播原文及其整理版本。代码或 Skill 指令的开源许可证不会自动赋予第三方题库、出版物或 PDF 的再分发权。

完整发布步骤见 [GitHub 开源发布教程](./docs/GITHUB_PUBLISHING_GUIDE.md)。

## 声明

本项目是独立的学习与模拟工具，与 IELTS、British Council、IDP、Cambridge University Press & Assessment 或 OpenAI 没有关联、授权或背书关系。IELTS 相关商标归其各自权利人所有。

评分参考：

- [IELTS Speaking format](https://ielts.org/take-a-test/test-types/ielts-general-training-test/ielts-general-training-format-speaking)
- [IELTS Speaking band descriptors](https://ielts.org/cdn/ielts-guides/ielts-speaking-band-descriptors.pdf)
- [ChatGPT Voice](https://learn.chatgpt.com/docs/features/voice)

## License

本项目的 Skill 指令、说明文档和原创图形采用 [MIT License](./LICENSE)。题库数据、第三方 PDF、出版物内容和商标不因仓库采用 MIT License 而自动获得相同授权；它们仍受各自权利声明约束。
