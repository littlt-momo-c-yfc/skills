# Third-Party Notices

本文件记录 `skills/` 中本地定制 Skills 使用、参考或组合的第三方项目。它不是对第三方项目许可证的替代，也不代表第三方项目维护者为本项目背书。

## 公开项目和直接参考来源

| 项目 | 地址 | 在本项目中的关系 |
|---|---|---|
| thuthesis | <https://github.com/tuna/thuthesis> | `latex-thesis-zh` 的中文 LaTeX 模板参考 |
| pkuthss | <https://github.com/CasperVector/pkuthss> | `latex-thesis-zh` 的中文 LaTeX 模板参考 |
| figures4papers | <https://github.com/ChenLiu-1996/figures4papers> | `nature-figure` 的绘图脚本和图表设计参考；不是直接上游 |
| Paper-to-patent-Skill | <https://github.com/snipp-zha/Paper-to-patent-Skill> | `nature-paper-to-patent` 的公开参考来源 |
| learning_research | <https://github.com/pengsida/learning_research> | `nature-writing` 的科研写作参考来源 |
| SNL-UCSB/data-visualization-skill | <https://github.com/SNL-UCSB/data-visualization-skill> | `research-writing-skill` 中提及的数据可视化工作流参考 |
| SNL-UCSB/literature-survey-skill | <https://github.com/SNL-UCSB/literature-survey-skill> | `research-writing-skill` 中提及的文献调研工作流参考 |

## 科研工具参考

`scientific-toolkit-skill` 聚合了多个科研计算主题的说明和示例，涉及但不限于：

- [Astropy](https://github.com/astropy/astropy)
- [Matplotlib](https://github.com/matplotlib/matplotlib)
- [NetworkX](https://github.com/networkx/networkx)
- [pymatgen](https://github.com/materialsproject/pymatgen)
- [QuTiP](https://github.com/qutip/qutip)
- [SymPy](https://github.com/sympy/sympy)
- [Google TimesFM](https://github.com/google-research/timesfm)
- [Materials Project API](https://github.com/materialsproject/api)

这些项目的源代码、许可证和商标归各自权利人所有。本仓库中的相关内容主要用于工具使用说明、接口示例和科研工作流参考。

## 许可证和再分发

1. 使用者应优先遵守各 Skill 目录内的许可证、版权声明和引用要求。
2. 参考仓库的许可证不自动覆盖本仓库中的本地定制内容。
3. `nature-figure` 包含较大的示例图片和绘图资源；公开发布前应逐项核对这些资源的再分发权限和原始出处。
4. `scientific-toolkit-skill` 中的 PDF、CSV、BibTeX、RIS、NBIB、图片和示例数据可能带有各自来源限制，不应默认视为本项目原创或可任意再分发。
5. 论文、期刊页面和数据集的文本或图像应遵守原始来源的版权和许可条件。

## 配置和密钥

本项目不应包含 API Key、Token、密码、私钥、个人配置或本机路径。需要 API Key 的 Skill 应通过环境变量或用户本地配置提供；请勿修改 Skill 文件后提交真实凭证。
