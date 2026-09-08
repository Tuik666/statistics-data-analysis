# statistics-data-analysis

> 一个用于学习 AI / 大模型相关概念的练习仓库，包含一个可复用的**项目级 Skill**
> 与该 Skill 生成并经人工核查的三份概念学习资料。

## 仓库用途

本仓库用于存放我对"AI Agent / 大模型上下文 / Skill"等概念的理解，
以及把它们沉淀成可复用资产的过程。

- **可继续迭代的个人作品集**：后续课程项目可在此基础上添加新概念、新 Skill。
- **项目级 Skill 模板**：演示如何把"学习一个新概念"这件事标准化为一次 Skill 调用。

## 仓库结构

```
statistics-data-analysis/
├── .workbuddy/
│   └── skills/
│       └── concept-learning-material-generator/
│           └── SKILL.md          # 概念学习资料生成 Skill（项目级）
├── learning-materials/
│   ├── agent.html                # 概念：Agent（智能体）
│   ├── llm-context.html          # 概念：大模型的上下文 / LLM Context
│   ├── skill.html                # 概念：Skill（Anthropic 风格 Agent Skill）
│   └── concept-relationship.html # 三者关系图 + 重点关系说明
├── README.md                     # 本文件
└── .gitignore
```

## Skill 存放路径

Skill 文件位于：

```
.workbuddy/skills/concept-learning-material-generator/SKILL.md
```

这是一份**项目级 Skill**——只在克隆本仓库并用 WorkBuddy 打开时才会被发现，
不会污染你的全局工作环境。

### Skill 元数据

- **name**：`concept-learning-material-generator`
- **description**：根据输入的概念名称，生成结构化的概念学习资料 HTML，
  含个人解释、核心机制、应用场景、易混淆边界、自测题与可核查的参考资料。

### Skill 适用场景

| 适合 | 不适合 |
|---|---|
| 想系统学习一个新概念并希望留下可复习材料 | 紧急的实战问题（直接要答案） |
| 教学前整理某个概念的速查手册 | 已经熟悉的概念（更建议脑图） |
| 阅读到陌生术语想搞清楚它是什么不是什么 | 需要论文级别的长篇综述 |

### 输入参数

调用 Skill 时应提供：

- `concept`（必填）：要学的概念名称
- `level`（可选，默认 `intermediate`）：深度档位（beginner/intermediate/advanced）
- `focus`（可选，默认 `balanced`）：关注重点（mechanism/application/boundary/balanced）
- `audience`（可选，默认 `general`）：目标读者背景
- `length`（可选，默认 `standard`）：篇幅（compact/standard/deep）

## 如何在 WorkBuddy 中调用

1. 在 WorkBuddy 中打开本仓库（把仓库目录作为 Workspace Folder）。
2. 项目启动时，WorkBuddy 会读取 `.workbuddy/skills/` 下的所有 Skill 的
   `name + description` 注入到系统提示（这就是 Skill 的"第一级披露"）。
3. 直接用自然语言提问即可，例如：

   > "请用 concept-learning-material-generator Skill 帮我整理 Transformer 的笔记，
   > 重点是机制（focus=mechanism），面向开发者（audience=developer）。"

4. Skill 被识别为相关后，WorkBuddy 会读入 `SKILL.md` 正文，按里面的步骤生成资料。
5. 生成的 HTML 可以保存到 `learning-materials/<concept-slug>.html`，并可继续迭代修订。

> 提示：如果当前 WorkBuddy 会话**没有自动发现 Skill**，可以：
> - 检查仓库根目录是否存在 `.workbuddy/skills/<你的-skill-名称>/SKILL.md`
> - 确认 YAML frontmatter 里有合法的 `name` 和 `description`
> - 重启 WorkBuddy session 让其重新扫描项目级 Skill

## 已生成的学习资料

| 资料 | 路径 | 重点（focus） | 深度（level） |
|---|---|---|---|
| Agent 概念 | [`learning-materials/agent.html`](learning-materials/agent.html) | balanced（机制+边界均衡） | intermediate |
| 大模型的上下文 | [`learning-materials/llm-context.html`](learning-materials/llm-context.html) | mechanism（重点讲机制） | intermediate |
| Skill 概念 | [`learning-materials/skill.html`](learning-materials/skill.html) | boundary（重点讲与相似概念的区分） | intermediate |
| 三者关系说明 | [`learning-materials/concept-relationship.html`](learning-materials/concept-relationship.html) | relationship | intermediate |

每份资料末尾都有"自检清单"+"✅ 已自检"标注。

## AI 协作与人工核查记录

我使用 AI（WorkBuddy + AI 助手）协作完成本作业，**不**接受 AI 直接产出而未经审视的内容。
下面记录了我使用了 AI 做什么、读了什么、改了什么：

### AI 做了什么

| 阶段 | AI 的角色 | 我的动作 |
|---|---|---|
| Skill 设计 | AI 草拟了 SKILL.md 的初稿（含 YAML frontmatter、输入/流程/输出/自检） | 我通读、对每一条做调整：精简 YAML description、追加"完成信号"小节 |
| 资料生成 | AI 按 Skill 描述的步骤生成三份 HTML 初稿 | 我对每份资料做了人工核查 |
| 关系说明 | AI 草拟了关系图与文字说明 | 我重写了 § 3 "上下文如何影响 Agent 的工作"，把影响切分成 4 个面 |
| README 与 .gitignore | AI 输出初稿 | 我删除/合并了 .gitignore 的冗余条目，并保证 README 真实反映实际仓库结构 |

### 人工核查与修改清单

- [x] 所有引用链接均经过 WebSearch 抽样验证（确认 URL 真实存在、内容对应主题）
- [x] 三份 HTML 都包含：个人理解（含类比）、核心机制、端到端应用场景、
      ≥ 2 组易混淆对照、≥ 5 道自测题、参考资料清单与自检 checklist
- [x] SKILL.md 含合法 YAML frontmatter（`name` + `description`），且描述里
      有清晰的**触发场景**（避免"用来帮助处理一些文档"这类模糊措辞）
- [x] **未**复制 AI 整段话当成"个人理解"：每一段都结合自身工程经验重写
- [x] 资料来源不得伪造：所有 URL 均为搜索结果中确实存在的页面
- [x] 未上传 API Key、密码、个人隐私或 session 级 memory 数据（`.gitignore`
      排除了 `.workbuddy/sessions/`、`.workbuddy/memory/`）

### 数据安全说明

- 本仓库**不**包含：
  - 任何 LLM API key、GitHub PAT、SSH 私钥、密码
  - 个人家庭住址、身份证号等隐私
  - 工作中受保密协议约束的代码或文档
- `.gitignore` 主动排除 `*.log`、`.workbuddy/sessions/`、`.workbuddy/memory/`
  等可能含敏感上下文数据的目录

## 后续计划

- 把更多概念（如 RAG、Function Calling、Token Economics、记忆机制）用同样的 Skill 生成。
- 把"自测题"拓展为题库，支持抽题复习。
- 给 Skill 加一个 `references/glossary.md`，让生成结果里的术语自动链接。

## License

本仓库以教学/演示用途发布。如需复用 Skill，请保留署名。
