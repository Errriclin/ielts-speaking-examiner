# 将 IELTS Speaking Examiner 开源到 GitHub

这份教程适合第一次发布 GitHub 项目。推荐先完成版权检查，再创建公开仓库和 Release。

## 1. 决定哪些内容可以公开

项目包含两种权利边界不同的内容：

- `SKILL.md`、`references/`、`agents/`、README 和图案属于 Skill 项目内容，可以由项目维护者选择开源许可证。
- `corpora/` 中的 PDF、题目原文和整理数据可能来自第三方。除非你拥有版权或明确的公开再分发许可，否则不要把它们提交到公开仓库或公开 Release。

当前题库清单把来源标记为用户提供的第三方汇编。这不等于已经取得公开传播授权。稳妥的公开方式是：

1. 开源 Skill 的流程、评分规则和题库格式。
2. 保留含第三方题库的完整 ZIP 作为个人使用版本。
3. 在公开仓库中提供经过授权、自行编写或明确开放许可的题库；也可以只提供导入说明。

## 2. 选择开源许可证

GitHub 仓库没有 `LICENSE` 文件时，其他人通常没有明确的复制、修改和再分发授权。常见选择：

| 许可证 | 适合情况 |
| --- | --- |
| MIT | 希望规则简单，允许商业和非商业使用，只要求保留许可证与版权声明 |
| Apache-2.0 | 希望采用宽松许可，同时包含明确的专利授权条款 |
| GPL-3.0 | 希望修改后再分发的版本继续以相同许可证开源 |

如果没有特殊要求，个人工具项目通常会选择 MIT。许可证只覆盖你有权授权的项目内容，不自动覆盖第三方题库。

在 GitHub 创建仓库时可直接选择许可证，也可以从 [choosealicense.com](https://choosealicense.com/) 了解差异后添加 `LICENSE` 文件。

## 3. 发布前整理目录

准备发布的仓库根目录应当直接包含：

```text
SKILL.md
README.md
agents/
references/
assets/
docs/
corpora/        # 仅包含有权公开的题库或公开导入说明
LICENSE
```

不要把 `ielts-speaking-examiner` 再套一层无关的项目目录，否则别人克隆后还要手动寻找 `SKILL.md`。

发布前检查：

- README 图片能显示，内部相对链接能打开。
- `SKILL.md` 位于仓库根目录。
- 没有身份证、账号、绝对本机路径、访问令牌或其他个人信息。
- 没有无授权的 PDF、题目全文、出版社图片或付费内容。
- 活动题库的 `index.json`、`manifest.json` 和实际文件互相匹配。
- ZIP 解压后只有一个清晰的 `ielts-speaking-examiner/` 顶层目录。

## 4. 创建 GitHub 仓库

### 网页方式

1. 登录 GitHub。
2. 打开 <https://github.com/new>。
3. Repository name 填写 `ielts-speaking-examiner`。
4. Description 可以填写：

   ```text
   A Voice-first IELTS Speaking mock examiner Skill with replaceable question banks and evidence-based feedback.
   ```

5. 选择 **Public**。
6. 如果本地目录已经有 README，不要让 GitHub 再生成同名 README。
7. 根据你的决定选择 MIT、Apache-2.0 或 GPL-3.0 许可证。
8. 创建仓库。

### 命令行方式

在终端进入准备公开的 Skill 目录：

```powershell
cd C:\path\to\ielts-speaking-examiner
git init
git add .
git commit -m "Initial release of IELTS Speaking Examiner"
git branch -M main
git remote add origin https://github.com/Errriclin/ielts-speaking-examiner.git
git push -u origin main
```

这个地址是本项目的正式仓库。其他维护者发布自己的分支或副本时，应替换成自己拥有写入权限的仓库地址。第一次推送前，应先在 GitHub 网页创建仓库。

如果使用 GitHub Desktop：

1. 选择 **File → Add local repository**。
2. 指向准备公开的 Skill 目录。
3. 如果提示不是 Git 仓库，选择创建仓库。
4. 填写首次提交说明并 Commit。
5. 选择 **Publish repository**，取消 Private 选项后发布。

## 5. 设置仓库首页

发布后进入仓库的 **About** 设置：

- Description：填写一句英文简介。
- Website：可留空或填写项目演示页。
- Topics 建议填写：

  ```text
  ielts
  speaking
  language-learning
  chatgpt
  codex
  voice
  skill
  english-learning
  ```

确认仓库首页能正常显示 README 横幅、徽章、Mermaid 流程图和目录链接。

## 6. 创建首个 Release

1. 在仓库首页选择 **Releases → Draft a new release**。
2. 创建标签，例如 `v1.0.0`。
3. Release title 填写 `IELTS Speaking Examiner v1.0.0`。
4. Release notes 可写：

   ```markdown
   ## Highlights

   - Complete IELTS Speaking Part 1/2/3 flow in Voice
   - Replaceable packaged question-bank format
   - Minimum 4, normally 5 primary questions in Part 1 and Part 3
   - Detailed four-criterion feedback for every part
   - Cross-platform user-level installation
   ```

5. 上传可公开分发的安装 ZIP。
6. 再次确认 ZIP 中没有无授权题库或个人文件。
7. 选择 **Publish release**。

## 7. 告诉用户如何安装

Release 页面中保留以下最短说明：

```text
1. Download and extract ielts-speaking-examiner.zip.
2. Copy the folder to ~/.agents/skills/ielts-speaking-examiner.
3. Restart the ChatGPT desktop app.
4. Run: $ielts-speaking-examiner 使用当前题库，开始完整口语模拟。
```

Windows 的 `~` 对应 `%USERPROFILE%`。

## 8. 后续版本维护

建议使用语义化版本：

- `v1.0.1`：修正文案、README 或小问题。
- `v1.1.0`：增加题库管理、反馈格式等兼容功能。
- `v2.0.0`：出现不兼容的目录或使用方式变化。

每次更新：

1. 修改源 Skill。
2. 校验流程规则和题库引用。
3. 重新生成 ZIP。
4. 在干净目录解压测试。
5. 提交 GitHub 变更。
6. 新建标签和 Release，并说明迁移事项。

## 9. 推荐的 Issue 模板信息

收到问题报告时，请用户提供：

- 应用和操作系统版本；
- 使用的 Skill 版本与题库版本；
- 问题发生在 Part 1、Part 2、Part 3 还是反馈阶段；
- 实际发生的行为；
- 期望行为；
- 去除个人信息后的相关文字或截图。

不要要求用户公开上传完整语音、身份证明或包含隐私的考试记录。
