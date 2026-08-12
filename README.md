# Codex Skills 集合

> 可复用的 Codex 用户级 Skills 集合与安装说明。

本项目整理了一组可复用的 Agent Skills，主要覆盖学术写作、科研计算、论文工作流、数据分析、图表设计、Office 文档和 Skill 管理等场景。仓库内包含 19 个本地定制 Skill 的完整源码，同时记录 4 个已有公开上游的 Skill。

## 目录说明

- 统计时间：**2026-08-12**
- 顶层用户级 Skills：**23 个**，其中本仓库打包本地定制 Skill **19 个**
- 仓库内本地 Skills 路径：`skills/`
- 原始统计路径：`$CODEX_HOME/skills/`，本机对应 `D:\CodexHome\skills\`
- 不纳入统计：Codex 内置的 `.system` 和共享资源目录 `_shared`
- `scientific-toolkit-skill` 内部包含多个科研子能力，但在本清单中作为一个顶层 Skill 统计

这些 Skills 并非全部来自同一个项目或作者：有些可以从公开 GitHub 仓库直接安装，有些是基于公开项目整理或参考的本地组合 Skill，还有一些是本项目维护的本地定制 Skill。第三方来源和再分发注意事项见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

## 快速安装

### 1. 从公开 GitHub 仓库安装

推荐使用通用 Skills CLI：

```powershell
npx skills add <owner>/<repo> --skill <skill-name> -g -y
```

例如：

```powershell
npx skills add tt-a1i/archify -g -y
npx skills add virgiliojr94/book-to-skill -g -y
npx skills add alchaincyf/huashu-design -g -y
npx skills add alchaincyf/nuwa-skill -g -y
```

也可以使用 Codex 自带的 GitHub 安装脚本：

```powershell
python "$env:CODEX_HOME\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --repo <owner>/<repo> `
  --path <skill-path>
```

如果没有设置 `CODEX_HOME`，Codex 通常会使用默认的用户目录。安装完成后，重新开始一个 Codex 会话即可加载新 Skill。

### 2. 安装本地定制 Skill

本地定制 Skill 必须连同完整目录一起发布，至少包含 `SKILL.md`，如果其中引用了 `references/`、`scripts/`、`assets/` 或 `manifest.yaml`，这些文件也必须保留。

如果你的开源仓库结构如下：

```text
your-repo/
└── skills/
    └── your-skill/
        └── SKILL.md
```

可以通过 Codex 安装脚本安装：

```powershell
python "$env:CODEX_HOME\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --repo <your-github-name>/<your-repo> `
  --path skills/your-skill
```

也可以手动复制到 Codex Skills 目录：

```powershell
Copy-Item -Recurse .\skills\your-skill "$env:CODEX_HOME\skills\your-skill"
```

仅发布本 README 而不发布 Skill 源码，无法完成本地定制 Skill 的安装。

### 3. 交给Agent安装
将要安装的skills发送给Ai Agent让他给你安装。

## 仓库结构

```text
.
├── README.md
├── THIRD_PARTY_NOTICES.md
├── .gitignore
└── skills/
    ├── academic-figure-prompt/
    ├── nature-writing/
    ├── scientific-toolkit-skill/
    └── ...
```

每个目录都是一个可独立安装的 Skill，通常包含 `SKILL.md`，并根据需要包含 `README.md`、`manifest.yaml`、`references/`、`static/`、`scripts/`、`agents/`、`examples/`、`templates/` 或 `assets/`。

### 本地定制 Skill 索引

以下 19 个本地定制 Skill 已随本仓库发布：

| Skill | 仓库内目录 |
|---|---|
| `academic-figure-prompt` | [skills/academic-figure-prompt/](skills/academic-figure-prompt/) |
| `academic-figure-prompt-pastel` | [skills/academic-figure-prompt-pastel/](skills/academic-figure-prompt-pastel/) |
| `codebase-to-course` | [skills/codebase-to-course/](skills/codebase-to-course/) |
| `find-skills` | [skills/find-skills/](skills/find-skills/) |
| `latex-thesis-zh` | [skills/latex-thesis-zh/](skills/latex-thesis-zh/) |
| `nature-academic-search` | [skills/nature-academic-search/](skills/nature-academic-search/) |
| `nature-citation` | [skills/nature-citation/](skills/nature-citation/) |
| `nature-data` | [skills/nature-data/](skills/nature-data/) |
| `nature-figure` | [skills/nature-figure/](skills/nature-figure/) |
| `nature-paper-to-patent` | [skills/nature-paper-to-patent/](skills/nature-paper-to-patent/) |
| `nature-paper2ppt` | [skills/nature-paper2ppt/](skills/nature-paper2ppt/) |
| `nature-polishing` | [skills/nature-polishing/](skills/nature-polishing/) |
| `nature-reader` | [skills/nature-reader/](skills/nature-reader/) |
| `nature-response` | [skills/nature-response/](skills/nature-response/) |
| `nature-reviewer` | [skills/nature-reviewer/](skills/nature-reviewer/) |
| `nature-writing` | [skills/nature-writing/](skills/nature-writing/) |
| `office-academic-skill` | [skills/office-academic-skill/](skills/office-academic-skill/) |
| `research-writing-skill` | [skills/research-writing-skill/](skills/research-writing-skill/) |
| `scientific-toolkit-skill` | [skills/scientific-toolkit-skill/](skills/scientific-toolkit-skill/) |

其中，`nature-academic-search` 需要额外的 Python 依赖，并包含会修改 Claude Code MCP 配置的 `install.sh`。请先审阅脚本，再决定是否执行；API Key 只能通过环境变量或用户本地配置提供。`scientific-toolkit-skill` 内含多个科研子能力和第三方参考资料；`nature-figure` 内含较大的示例图片资源。相关再分发风险见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

本仓库中的本地定制 Skill 可以按目录单独安装：

```powershell
npx skills add <owner>/<repo> --skill <skill-name> -g -y
```

或者使用 Codex 官方安装脚本：

```powershell
python "$env:CODEX_HOME\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --repo <owner>/<repo> `
  --path skills/<skill-name>
```

## Skills 总览

| 分类 | 数量 | 覆盖方向 |
|---|---:|---|
| 学术写作与论文工作流 | 13 | 文献检索、论文阅读、写作、润色、审稿、返修、数据声明、专利和 PPT |
| 科研计算与数据分析 | 1 | MATLAB/Python、统计、机器学习、仿真、优化和科研绘图 |
| 图表、架构图与视觉设计 | 4 | 学术配图提示词、架构图、交互原型、动画和信息图 |
| 文档、PPT 与课程生成 | 2 | Office 学术文档和代码库课程化 |
| Skill 管理与知识蒸馏 | 3 | Skill 搜索、书籍转 Skill、人物思维框架蒸馏 |

## 详细清单

### 一、学术写作与论文工作流

| Skill | 主要作用 | 适用场景 | 项目地址 / 来源 | 安装方式 |
|---|---|---|---|---|
| `latex-thesis-zh` | 中文 LaTeX 硕博论文助手，支持编译诊断、GB/T 7714 参考文献、模板结构、三线表和学术表达检查。 | 中文硕博论文、XeLaTeX、Thuthesis、PKUthss、论文排版。 | 本地定制；参考 [thuthesis](https://github.com/tuna/thuthesis) 和 [pkuthss](https://github.com/CasperVector/pkuthss)。 | 发布源码后按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-academic-search` | 多来源文献检索与引用管理，支持 PubMed、CrossRef、arXiv、Scopus、ScienceDirect、MeSH 和 BibTeX/RIS/NBIB 转换。 | 查论文、查相关工作、核对 DOI、导出参考文献。 | 本地组合 Skill；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-citation` | 将论文段落拆分为可引用主张，检索 Nature、Science、Cell 等期刊体系的支持文献并生成引用映射。 | 给段落补引文、Nature/CNS 文献支持、导出 EndNote/RIS/Zotero 格式。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-data` | 准备和审查 Data Availability、数据仓库选择、数据集引用及 FAIR 元数据。 | 论文数据共享、代码和数据可用性声明、敏感数据说明。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-figure` | 面向 Nature 等高水平期刊的 Python/R 科研绘图、导出和质量审查工作流。 | 多面板图、论文图、SVG/PDF/TIFF、期刊级数据可视化。 | 本地组合 Skill；参考 [figures4papers](https://github.com/ChenLiu-1996/figures4papers)，不是该 Skill 的直接上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-paper-to-patent` | 将论文、技术报告、代码和图表转换为有证据对应关系的中文发明专利草案。 | 提取可专利技术点、撰写权利要求、说明书、摘要和专利审查。 | 本地定制；参考 [Paper-to-patent-Skill](https://github.com/snipp-zha/Paper-to-patent-Skill)。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-paper2ppt` | 从论文、预印本或 PDF 制作中文 Nature 风格 PPTX，并进行图表选择、讲稿和版式自检。 | 文献汇报、组会、学术报告、论文答辩、Journal Club。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-polishing` | 按 Nature 风格润色和重构学术英文，也覆盖 LaTeX 排版和补充材料版式问题。 | 摘要、引言、结果、讨论、方法、SCI 英文润色和排版诊断。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-reader` | 制作全文中英对照、图表感知、带来源锚点的 Markdown 论文阅读器。 | PDF、DOI、arXiv 或网页论文的精读、翻译和图表定位。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-response` | 起草、审查和修改逐条审稿意见回复信。 | Major/Minor Revision、Rebuttal、编辑决定信和返修说明。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-reviewer` | 从审稿人角度模拟 Nature 风格预审，输出多份审稿意见和交叉总结。 | 投稿前自审、创新性和技术可靠性评估、模拟同行评审。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `nature-writing` | 根据研究主张、结果、图表和草稿规划或撰写 Nature 风格论文结构。 | 从零写论文、重构摘要/引言/方法/实验/讨论、构建论证链。 | 本地定制；参考 [learning_research](https://github.com/pengsida/learning_research)。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `research-writing-skill` | 中文优先的科研论文写作、改写、润色、章节规划和审稿回复 Skill。 | 中文论文、LaTeX/Markdown 稿件、摘要、引言、实验和讨论。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |

### 二、科研计算与数据分析

| Skill | 主要作用 | 适用场景 | 项目地址 / 来源 | 安装方式 |
|---|---|---|---|---|
| `scientific-toolkit-skill` | 综合科研计算工具箱，覆盖 MATLAB/Octave、Python、信号与图像处理、统计、机器学习、仿真、优化、时间序列、材料、网络和量子系统。 | 科研代码、实验数据分析、传感器数据、论文绘图、可复现实验流程。 | 本地组合 Skill；内部参考 [Astropy](https://github.com/astropy/astropy)、[Matplotlib](https://github.com/matplotlib/matplotlib)、[NetworkX](https://github.com/networkx/networkx)、[pymatgen](https://github.com/materialsproject/pymatgen)、[QuTiP](https://github.com/qutip/qutip)、[SymPy](https://github.com/sympy/sympy) 等项目。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)；具体 Python/MATLAB 依赖需按任务另行安装。 |

### 三、图表、架构图与视觉设计

| Skill | 主要作用 | 适用场景 | 项目地址 / 来源 | 安装方式 |
|---|---|---|---|---|
| `academic-figure-prompt` | 为 NanoBanana、Gemini、DALL-E、Midjourney 等图像工具生成高信息密度的英文论文配图提示词。 | 框架图、网络结构图、流程图、模块图、消融图和数据模式图。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `academic-figure-prompt-pastel` | 生成现代 ICLR/NeurIPS/ICML 风格的柔和配色、留白和轻量化 ML/RL 论文配图提示词。 | 现代机器学习论文架构图、模型流程图和概念图。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `archify` | 生成带深色/浅色主题切换和导出功能的 SVG/HTML 架构图、流程图、时序图、数据流图和生命周期图。 | 系统架构、网络拓扑、CI/CD、API 调用链、ETL、状态机和 Mermaid 美化。 | [tt-a1i/archify](https://github.com/tt-a1i/archify)，MIT。 | `npx skills add tt-a1i/archify -g -y`。 |
| `huashu-design` | 用 HTML 生成高保真原型、交互 Demo、演示页面、动效、信息图，并提供设计方向探索和专家评审。 | App/Web 原型、品牌展示、动画 Demo、PPT 视觉稿、信息图。 | [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design)，MIT。 | `npx skills add alchaincyf/huashu-design -g -y`。 |
| `huashu-nuwa` | 通过资料研究和框架提炼，将人物、主题或模糊需求蒸馏为可运行的思维顾问 Skill。 | 创建人物视角、决策框架、表达风格和主题型 Agent Skill。 | [alchaincyf/nuwa-skill](https://github.com/alchaincyf/nuwa-skill)。 | `npx skills add alchaincyf/nuwa-skill -g -y`。 |

### 四、文档、PPT 与课程生成

| Skill | 主要作用 | 适用场景 | 项目地址 / 来源 | 安装方式 |
|---|---|---|---|---|
| `office-academic-skill` | 中文优先的 Word/PPT 学术工作流，支持报告、PPTX、讲稿、模板匹配和 Office 文件质量检查。 | 文献报告、组会 PPT、开题/中期/答辩、DOCX/PPTX 编辑和检查。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `codebase-to-course` | 把代码库转换成带滚动导航、动画、测验和代码白话翻译的交互式单页课程。 | 向非技术人员讲解代码、制作项目教程、生成代码库导览。 | 本地定制；当前未确认独立公开上游。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |

### 五、Skill 管理与知识蒸馏

| Skill | 主要作用 | 适用场景 | 项目地址 / 来源 | 安装方式 |
|---|---|---|---|---|
| `find-skills` | 帮助发现、搜索和安装 Agent Skills，提供 `skills.sh` 生态和通用 CLI 的使用说明。 | 不知道是否存在某个能力、搜索现成 Skill、扩展 Agent 能力。 | 本地定制；参考 [skills.sh](https://skills.sh/) 和 [vercel-labs/skills](https://github.com/vercel-labs/skills)。 | 按[本地定制 Skill 安装](#2-安装本地定制-skill)。 |
| `book-to-skill` | 将 PDF、EPUB、DOCX、HTML、Markdown 等书籍或文档转换为结构化 Agent Skill，提取框架、原则、技巧和反模式。 | 把书籍变成可检索的知识库、构建个人学习 Skill、按章节调用知识。 | [virgiliojr94/book-to-skill](https://github.com/virgiliojr94/book-to-skill)。 | `npx skills add virgiliojr94/book-to-skill -g -y`。 |

## 安装命令汇总

当前清单中已经确认可直接从公开仓库安装的 Skill：

```powershell
npx skills add tt-a1i/archify -g -y
npx skills add virgiliojr94/book-to-skill -g -y
npx skills add alchaincyf/huashu-design -g -y
npx skills add alchaincyf/nuwa-skill -g -y
```

本仓库中的本地定制 Skill 可使用上面的 `--skill` 方式按名称安装，也可以使用 Codex 官方安装脚本按路径安装：

```powershell
python "$env:CODEX_HOME\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --repo <your-github-name>/<your-repo> `
  --path skills/nature-writing
```

## 来源与许可证说明

- **公开上游**：如 `archify`、`book-to-skill`、`huashu-design` 和 `nuwa-skill`，请以原仓库的 README、LICENSE 和版本信息为准。
- **参考来源**：某些本地 Skill 借鉴了其他项目的工作流、工具或领域知识。参考来源不等同于直接上游，也不代表原项目维护者为本项目背书。
- **本地定制**：当前只能确认存在于本机 `$CODEX_HOME/skills/`，没有确认独立公开仓库的 Skill，统一标注为本地定制。
- 使用、复制或再发布某个 Skill 前，应检查该 Skill 自身目录中的许可证、引用和第三方依赖；第三方项目的许可证优先于本清单的说明。
- 本 README 是一个环境快照，不代表所有 Skill 由同一作者维护，也不代表所有 Skill 可以在没有额外依赖的情况下立即运行。


## 免责声明

本项目只是个人 Codex Skills 清单和使用说明。Skill 的实际行为取决于其 `SKILL.md`、引用文件、运行环境、模型版本和外部工具状态。涉及科研结论、法律、医疗、金融或生产系统的输出，应由具备相应专业能力的人员复核。
