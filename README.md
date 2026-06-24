# notion-paper-compilation

这是一个用于构建 **Notion 论文知识库** 的工作流项目。它结合 Notion、ChatGPT 或 Codex，帮助用户快速将英文论文系统化整理到自己的 Notion 工作区中。

该项目适合科研人员、研究生、课题组和论文阅读小组使用，尤其适合需要长期积累文献、整理研究方向、撰写论文 Introduction / Related Work 的场景。

---

## 1. 项目简介

`notion-paper-compilation` 的目标是：  
**利用 Notion 搭建结构化论文知识库，并借助 ChatGPT 或 Codex 自动完成论文整理。**

你只需要提供一篇论文 PDF，并告诉 ChatGPT 或 Codex 要整理到 Notion 的哪个页面，它就可以按照预设工作流自动完成论文阅读、翻译、归类、摘录和标签整理。

该工作流可以完成的内容包括但不限于：

- 将英文论文主体内容翻译为中文
- 自动填写论文元信息
  - 论文标题
  - 作者单位
  - 发表年份
  - 期刊 / 会议
  - GitHub 链接
  - 方法概括
- 对论文方法部分进行系统化总结
  - 研究问题
  - 输入与输出
  - 方法流程
  - 模型结构
  - 损失函数
  - 实验结论
- 对生涩难懂的位置加入通俗解释
- 自动生成论文标签
- 自动创建重要观点摘录
- 将摘录语句整理到 Notion 数据库中
- 支持以看板形式浏览论文摘录
- 支持多人协作，共同搭建课题组论文知识库

相比手动阅读和整理论文，该工作流可以显著降低文献整理成本。一般情况下，使用 ChatGPT 或 Codex 整理一篇论文大约需要 **10 分钟左右**，具体时间取决于论文长度、方法复杂度以及 Notion 页面内容多少。

---

## 2. Notion 模板

本项目提供了一个配套的 Notion 论文知识库模板。

模板链接：

[Link](https://oasis-flood-4b1.notion.site/1cfdfe6b51f982b388f5015f856acf6a?source=copy_link)

打开链接后，点击页面左上角的 **复制 / Duplicate**，即可将模板复制到你自己的 Notion 工作区中。

如果你是刚接触 Notion 的用户，建议使用教育邮箱注册 Notion 账号，这样可以获得更完整的教育版功能支持。

复制模板后，你需要将 ChatGPT 或 Codex 与你的 Notion 工作区进行关联。只有完成授权后，ChatGPT 或 Codex 才能访问你的 Notion 页面，并将论文内容整理到指定的页面中。

---

## 3. Notion 模板结构说明

该模板主要包含以下几个部分（这些可以自己设置也可以让ai给你创建，AI优先在已有的标签库里面检索合适的标签，如果没有找到就会自主创建）：

### 3.1 论文数据库

用于存放每一篇论文的主页面。

每篇论文可以记录：

- 论文名称
- 英文标题
- 发表年份
- 发表单位
- 期刊 / 会议
- GitHub 链接
- 阅读状态
- 论文概括
- 论文标签
- 论文摘录

### 3.2 标签库

用于管理论文标签。

标签可以按照研究方向、数据模态、任务类型、模型结构、方法类别等自由设置，例如：

- Autism Spectrum Disorder
- Medical Image Analysis
- Diffusion MRI
- Brain Morphology
- Normative Modeling
- Transformer
- Foundation Model
- Explainable AI

### 3.3 论文摘录数据库

用于存放论文中的重要观点、方法描述、实验结论和可复用写作句子。

摘录内容可以包括：

- 论文核心工作
- 研究动机
- 现有方法不足
- 方法创新点
- 关键实验结论
- 局限性
- 未来工作
- 可用于论文写作的表达

摘录数据库可以使用表格、列表或看板形式展示，方便后续撰写论文 Introduction、Related Work 和 Discussion。

### 3.4 期刊 / 会议数据库

用于统一管理论文来源。

如果整理论文时发现新的期刊或会议，ChatGPT / Codex 可以自动创建对应条目并关联到论文页面。

---

## 4. 使用方式一：ChatGPT 网页端

如果你使用的是 ChatGPT 网页端，可以直接使用本项目中的提示词文件：

```text
notion_paper_workflow.md
```

### 使用步骤

1. 打开 ChatGPT 网页端。
2. 确保 ChatGPT 已经连接你的 Notion 工作区。
3. 将 `notion_paper_workflow.md` 中的提示词复制到聊天窗口。
4. 上传需要整理的论文 PDF。
5. 告诉 ChatGPT 要整理到哪个 Notion 页面。
6. ChatGPT 会自动完成论文整理、翻译、注释、摘录和标签关联。

### ChatGPT 使用示例

你可以这样输入：

```text
请你按照下面的论文整理工作流，将我上传的英文论文整理到 Notion 工作区中的 ASD-project 页面。
```

然后上传论文 PDF，例如：

```text
Profiling brain morphology for autism spectrum disorder with two cross-culture large-scale consortia.pdf
```

ChatGPT 会自动搜索 Notion 中的 `ASD-project` 页面，并将论文内容整理进去。

---

## 5. 使用方式二：Codex Skill

如果你使用 Codex，可以将本项目中的 skill 文件夹复制到 Codex 的 skills 目录中。

### 安装方式

将项目中的：

```text
notion-paper-compilation
```

文件夹复制到：

```text
C:\Users\<你的用户名>\.codex\skills
```

或者：

```text
%USERPROFILE%\.codex\skills
```

复制完成后，重新启动 Codex，使 skill 生效。

### Codex 使用方式

在 Codex 中使用该 skill 时，可以通过如下方式调用：

```text
$notion-paper-compilation @Notion
```

然后给出简单的自然语言指令即可。

### Codex 使用示例

例如，你可以在 Codex 中输入：

```text
$notion-paper-compilation @Notion

我上传了一篇英文论文，请你将这篇论文整理到 Notion 工作区中的 ASD-project 页面。
```

如果你已经上传了论文 PDF，Codex 会读取论文内容，并通过 Notion 连接器将整理结果写入指定页面。

---

## 6. 适用场景

该项目适用于以下场景：

- 个人论文阅读与知识管理
- 研究生文献精读
- 课题组多人共建论文库
- 论文 Introduction 写作素材积累
- Related Work 分类整理
- 研究方向调研
- 快速理解陌生领域论文
- 构建长期可复用的科研知识库

---

## 7. 推荐工作流

建议按照以下方式使用：

1. 在 Notion 中为每篇论文新建一个页面。
2. 使用 ChatGPT 或 Codex 自动整理论文。
3. 检查自动生成的翻译和方法总结。
4. 手动补充论文中的关键图表截图。
5. 在摘录数据库中筛选重要观点。
6. 写论文时直接从摘录看板中调用相关观点和句子。

---

## 8. 注意事项

- ChatGPT 或 Codex 必须先获得 Notion 工作区访问权限。
- Notion 页面名称应尽量明确，避免多个页面同名导致定位错误。
- 如果论文较长，整理时间会相应增加。
- 自动翻译和总结结果建议人工复核，尤其是公式、实验设置和方法细节。
- 参考文献部分默认不翻译、不复制到 Notion 正文中。
- 图片和表格默认不直接插入，只会标记推荐插入位置，方便后续人工截图补充。

---

## 9. 项目文件说明

```text
notion-paper-compilation/
├── notion-paper-compilation/      # Codex skill 文件夹
├── notion_paper_workflow.md       # ChatGPT / Codex 通用论文整理提示词
├── README.md                      # 项目说明文件
└── LICENSE                        # 开源许可证
```

---

## 10. License

本项目基于 Apache-2.0 License 开源。

你可以自由使用、修改和分发本项目，但请遵守许可证要求。

---

## 11. 致谢

本项目主要面向科研论文知识库构建场景，结合 Notion、ChatGPT 和 Codex 的能力，帮助科研人员更高效地完成论文阅读、知识沉淀和写作素材积累。
