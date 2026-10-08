# 中央财经大学 Beamer 模板 · CUFE Beamer Template

适用于学术报告、课程展示和论文答辩的非官方中央财经大学风格 LaTeX Beamer 模板。采用 16:9 画布、蓝白配色和斜切封面，默认使用 **pdfLaTeX** 编译。

版式参考 PKU-Beamer-Template，主题在单个 `.tex` 文件中实现，便于直接修改。校徽和书法校名使用透明背景 PNG，无需复制大量绘图代码。

## 模板特点

- **中文支持**：使用 `CJKutf8` 与 `gbsn` 字体，英文使用 Latin Modern。
- **统一版式**：封面、目录、章节页、正文和白底致谢页。
- **学术内容示例**：双栏、流程图、数学公式、三线表和结论讨论。
- **可调整样式**：颜色、页脚文字、章节标题与可选校园封面照片。
- **图片透明背景**：校徽与书法校名作为独立素材引用。

## 项目结构

```text
cufe-beamer-template/
├── cufe-beamer.tex                 # 主文档及主题定义
├── latexmkrc                       # 默认使用 pdfLaTeX
├── README.md                       # 使用说明与来源
├── NOTICE.md                       # 署名与素材权利说明
└── assets/
    ├── cufe-logo-transparent.png    # 校徽
    └── cufe-wordmark-transparent.png # 书法校名
```

## 使用方法

1. 在 GitHub 点击 **Code → Download ZIP**，在 Overleaf 新建项目时选择 **Upload Project**；手动上传时须同时上传 `cufe-beamer.tex` 和 `assets` 文件夹中的两张 PNG 图片。
2. 将编译器设置为 **pdfLaTeX**，主文档设置为 `cufe-beamer.tex`。
3. 搜索“从这里修改报告信息”，填写报告标题、作者、学院与日期。
4. 替换示例正文。表格中的数字仅为演示数据。

本地安装完整 TeX Live 或相应 MiKTeX 包后，在项目目录执行：

```bash
latexmk -pdf cufe-beamer.tex
```

也可执行两次 `pdflatex cufe-beamer.tex`，以更新目录和页码。

### 修改报告信息

在源码中搜索“从这里修改报告信息”，修改以下内容：

```latex
\title[学术报告]{报告标题}
\subtitle{报告副标题}
\author{作者姓名}
\institute{中央财经大学\quad 学院／研究机构}
\date{2026年10月}
```

正文位于 `CJK*` 中文环境中；新增幻灯片也应写在这个环境内。

### 常用命令

| 命令 | 用途 |
| --- | --- |
| `\cufechapter{01}{研究背景}` | 插入章节过渡页 |
| `\footlinecolor{cufeblue}` | 设置页脚背景色 |
| `\footlinecolor{}` | 使用白色页脚 |
| `\footlinepayoff{自定义文字}` | 修改页脚学校名称位置的文字 |
| `\backmatter` | 插入白底致谢页 |
| `\titlebackground*{assets/campus.jpg}` | 使用自行提供的校园照片 |

主题写在源码中，不需要额外 `.sty` 文件。校徽与书法校名使用基于用户提供图片去除白底的透明 PNG 图片，位于 `assets/cufe-logo-transparent.png` 和 `assets/cufe-wordmark-transparent.png`。中文通过 `CJKutf8` 与 TeX Live 的 `gbsn` 字体排版，英文使用 Latin Modern；不再依赖 Fandol。项目附带 `latexmkrc`，默认使用 pdfLaTeX。

## 版式说明

- 16:9 画布，左侧标题与右侧蓝色斜切封面。
- 中财校名、英文校名、校训和官网校徽。
- 目录、章节页、双栏、流程图、公式、三线表、结论和致谢页。
- 支持 `\cufechapter{01}{章节标题}`、`\footlinecolor{颜色}` 与 `\backmatter`。
- 可选 `\titlebackground*{assets/campus.jpg}`：需自行上传校园照片。

封面左上角保留学校标识，右侧为纯色斜切背景。致谢页使用白色背景，以保证蓝色校徽的辨识度。

这是独立主题，并不完整兼容原 SINTEF 主题的全部接口；原版 `chapter`、`sidepic`、`themecolor` 环境或命令未实现。原样例内容已替换为中文学术报告示例。

## 来源

- 封面构图参考：[PKU-Beamer-Template](https://www.overleaf.com/latex/templates/bei-da-zhong-wen-mo-ban-pku-beamer-template/kfxpbtzrqhrn)，Zhuming Shi；原页面标注 CC BY 4.0。
- 原模板主题来源：Federico Zenith 的 SINTEF Presentation，以及 Liu Qilong 的 Beamer-LaTeX-Themes。
- 校徽来源：[中央财经大学官网校徽页](https://www.cufe.edu.cn/info/1029/1066.htm)。当前版本使用用户提供的校徽图片，另配用户提供的书法校名图片。
- 校训来源：[中央财经大学学校章程](https://www.cufe.edu.cn/xxgk/xxzc.htm)。

蓝色 `#123F68` 为本版屏幕设计用色，未声明为学校官方标准色。保留来源署名；校徽权利属于其原权利人。本模板非学校官方发布。

校徽和校名透明素材经过图像工具处理，并非学校提供的官方矢量母版。正式对外使用时，请自行核对标识准确性与学校的使用要求。素材权利与来源见 [NOTICE.md](NOTICE.md)。

## 常见问题

**中文提示 `Unicode character ... not set up for use with LaTeX`？**

确认上传的是当前版本，新增中文幻灯片在 `CJK*` 环境内。当前模板已为 Beamer 初始化时测量的页脚单独启用中文环境。修改版本后，可在 Overleaf 使用 **Recompile from scratch** 清除旧辅助文件。

**提示找不到校徽或校名图片？**

保持 `assets` 文件夹结构，图片名称与源码引用一致；不要只上传主文档。

**本地缺少 `CJKutf8`、`gbsn` 或其他宏包？**

安装相应 CJK、中文字体、Beamer、TikZ 与 Latin Modern 包，或使用包含这些依赖的 TeX Live 环境。

## 验证状态

已有 Overleaf 日志显示旧版本输出了 12 页 PDF，但同时报告文档初始化时的中文错误。当前源码已针对页脚初始化修正中文环境，尚未取得修复版本的完整编译通过记录。

2026年10月8日尝试使用 Codex 内置编译器时，编译环境返回 `Unable to find standard directories for platform`。仓库不将此次检查视为编译通过，也不附未经验证的 PDF。

欢迎通过 GitHub Issues 提交问题。请附编译器类型、TeX Live 版本及最先出现的错误日志，以便定位。
