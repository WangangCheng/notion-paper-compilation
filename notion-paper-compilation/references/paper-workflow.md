# Paper Workflow Reference

Use this reference for every `$notion-paper-compilation` run.

## 1. Intake and Target Resolution

1. Confirm the paper source and target Notion location.
2. Search the target page by exact title or URL. If several plausible pages appear and context is insufficient, ask the user to confirm.
3. Fetch the target Notion page and its parent database/data source.
4. Fetch linked databases visible from the page or schema, especially journals/conferences, tags, and excerpts.
5. Identify exact property names and types before updating:
   - paper title/name, often `Name`
   - English title, often `Title`
   - `发表单位`
   - `发表年份`
   - journal/conference relation such as `期刊`, `会议`, or `📚 期刊`
   - `概括`
   - `github`
   - status, importance, reading date, and owner if present
   - tag relation
   - excerpt relation
6. Treat page buttons such as `添加摘录` or `生成标签` as UI shortcuts. If tools cannot click them, create the equivalent relation records directly.

## 2. Paper Extraction Checklist

Extract and keep source evidence for:

- title, authors, affiliations, venue/journal/conference, year, DOI/arXiv if present
- abstract and contribution statements
- problem setting, motivation, and existing method gaps
- proposed method, modules, inputs, outputs, data shapes, training targets, losses, inference, and evaluation metrics
- if not a model-training paper: data source, variables, analysis pipeline, statistical tests, model/estimator choices, outputs, and conclusion logic
- quantitative and qualitative conclusions
- limitations, challenges, future work, and failure cases
- GitHub, project page, code, data, or supplementary links
- equations, algorithm boxes, figure captions, and table captions

If the GitHub/code link is absent, leave the field blank.

## 3. Metadata Rules

- Fill `title`/`Name` with the paper's display name used by the local database.
- Fill `Title` with the exact English title when a separate title field exists.
- Fill `发表单位` with concise main affiliations, not an exhaustive author-address dump unless the target database expects that.
- Fill `发表年份` from publication year, accepted year, arXiv year, or the most appropriate visible paper date.
- Fill the venue relation by searching the venue database. Create a venue record only when no match exists.
- For arXiv-only papers, use `arXiv` or `arXiv preprint` as the venue if the schema supports it.
- Fill `概括` in Chinese, focused on method rather than only abstract:
  - what problem the paper targets
  - what gap or limitation existing methods have
  - what method/model/analysis the authors propose
  - what core modules or stages it contains
  - what inputs and outputs are
  - what main conclusion the experiments support
  - why the method matters
- Do not fabricate missing metadata. Leave unknown fields empty and mention them in the final report.

## 4. Body Scope and Structure

Translate the paper body, including sections such as:

- Abstract
- Introduction
- Related Work
- Results
- Methods / Proposed Method / Methodology
- Discussion
- Conclusion
- Data Availability
- supplementary method content when it is necessary to understand the main paper

Skip and do not put in the Notion body:

- References
- Author contributions
- Acknowledgements
- Funding
- Competing interests / conflict of interest
- pure figure content
- pure table content

If citations like `[1]` or `[23]` appear in translated body text, preserve the citation markers when useful, but do not expand the bibliography.

Use the target page's existing style when visible. Otherwise use this order:

1. `论文信息`
2. `方法总览`
3. translated sections following the original paper order
4. `图表插入清单`
5. `核心摘录`
6. `标签与归档`
7. `参考文献处理说明`

## 5. Translation Style

- Translate into natural, readable Chinese; do not hard-translate sentence by sentence when it harms clarity.
- Preserve necessary technical terms. On first mention, include the English full term and Chinese explanation for important abbreviations.
- Keep mathematical symbols, variable names, dataset names, model names, and metric names precise.
- Do not translate references line by line.
- Do not translate raw tables or recreate original figures.

## 6. Formula Handling

Use Notion-supported formula environments.

- Inline formulas: prefer Notion inline equation syntax such as `$`X \in \mathbb{R}^{N\times P}`$` when supported by the fetched spec.
- Display formulas: use independent formula blocks:

```markdown
$$
L=\frac{1}{N}\sum_{i=1}^{N}\mathrm{CE}(\ell_i,y_i)
$$
```

- Preserve variables and explain important terms in a callout when the formula is conceptually important.
- Do not convert formulas to screenshots or plain code unless they cannot be represented otherwise.

## 7. Callout Rules

All beginner explanations, intuition, method motivations, analogies, formula explanations, experiment-design explanations, ablation interpretations, important-result interpretations, limitations, and future-work explanations must be written as Notion callouts.

Use gray callouts for explanations:

```markdown
<callout icon="💡" color="gray_bg">
**注释：标题**

用通俗语言解释概念、方法设计动机、公式含义或实验结论。
</callout>
```

Rules:

- Do not write explanatory notes as ordinary loose paragraphs.
- If a note is long, place `<details>` folded lists inside the callout.
- Use accessible language without weakening technical accuracy.
- Prefer callouts near the exact paragraph where the concept appears.

## 8. Method Overview Callout

Before the translated Methods / Proposed Method / Methodology section, insert a method overview callout.

Use this template for model-training papers:

```markdown
<callout icon="💡" color="gray_bg">
**方法总览：模型训练流程、输入输出、数据形状与损失函数**

<details>
<summary>一句话概括</summary>

...

</details>

<details>
<summary>1. 训练输入是什么？</summary>

...

</details>

<details>
<summary>2. 模型模块和形状如何变化？</summary>

...

</details>

<details>
<summary>3. 训练输出是什么？</summary>

...

</details>

<details>
<summary>4. 损失函数如何定义？</summary>

...

</details>

<details>
<summary>5. 完整训练流程</summary>

...

</details>

<details>
<summary>6. 推理或迁移时如何使用？</summary>

...

</details>
</callout>
```

For model-training papers, include when available:

- input data and shape
- each module's role and output shape
- encoder/decoder/classification head/prediction head behavior
- training labels
- loss function and each term's meaning
- inference output
- frozen vs. trainable modules
- downstream-task use
- augmentation, batch size, epochs, learning rate, and other training details

For non-model-training papers, use a method overview callout that covers:

- research question
- data sources
- variable definitions
- analysis pipeline
- statistical methods
- outputs
- how the conclusion is derived

## 9. Figures and Tables

Do not recreate original figures or tables unless the user explicitly asks. Insert a blue Notion callout at the nearest relevant location.

Figure template:

```markdown
<callout icon="🖼️" color="blue_bg">
**图片放置建议：图 1**

这里建议插入原文 Figure 1。该图展示……
</callout>
```

Table template:

```markdown
<callout icon="🧾" color="blue_bg">
**表格放置建议：表 1**

这里建议插入原文 Table 1。该表比较……
</callout>
```

Placement examples:

- overall model framework -> Figure 1
- segmentation/classification performance -> Table 1
- embedding visualization -> Figure 2
- attention maps -> Figure 3
- downstream task performance -> relevant tables
- ablation study -> ablation table
- dataset statistics -> dataset table

Also include a `图表插入清单` near the end for quick manual screenshot insertion.

## 10. Excerpts

Create or update excerpt records in the paper-excerpt database when it exists. If the page has an add-excerpt button but the tool cannot click it, create entries directly in the underlying excerpt data source.

Each excerpt should include, when the schema supports it:

- `摘录标题`
- `摘录内容`
- `我的笔记`
- `类型`
- `重要程度`
- paper relation
- tag relation if useful

Coverage should include:

- paper's core work
- target problem
- existing method challenges/gaps
- proposed key method
- key modules
- important experimental conclusion
- transferability or generalization
- limitations
- future work direction
- reusable writing/motivation points

Quantity:

- Generate 10-20 excerpts for typical papers.
- Generate at least 8 excerpts for short papers.
- Generate around 15 excerpts for complex method papers.

Link excerpt records back to the paper through the relation field discovered from the schema.

## 11. Tags

Generate tags that help retrieval and归档:

- research area
- data modality
- method type
- task/problem type
- model architecture
- interpretability, transferability, foundation-model status, or other defining features
- evaluation target

Search the tag database before creating new tags. When creating tags, fill category fields such as `研究方法`, `学科领域`, `研究对象`, `理论框架`, `数据类型`, or `其他` when those options exist. Add a short explanation if the tag schema has a description field.

## 12. Notion Update and Verification

1. Update metadata in small batches if Notion tool calls are large or unstable.
2. Insert long body content in chunks rather than one huge update.
3. After writing, fetch the updated paper page.
4. Check that metadata, body sections, formula syntax, callouts, figure/table placement notes, excerpts, and tags are present.
5. Report:
   - updated paper page
   - created venue/tag/excerpt records
   - skipped sections, especially references
   - fields left blank because the paper did not provide them
   - any extraction or formula-rendering uncertainty

## 13. Final Response

Keep the final response short. Mention that references were skipped and figures/tables were not inserted, only marked for later screenshots.
