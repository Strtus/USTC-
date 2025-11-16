# USTC 代培生不完全入学指北

本仓库包含基于 IPLeiria Thesis 模板的 LaTeX 项目（IPLeiriaMain.tex）。

## 构建（Windows）
1. 安装 TeX 发行版（推荐 TeX Live 或 MiKTeX），确保包含 XeLaTeX、biber、minted 所需包。
2. 安装 Python 和 Pygments（用于 minted）：

```powershell
pip install Pygments
```

3. 编译步骤（在项目根目录下）：

```powershell
xelatex -shell-escape -interaction=nonstopmode -halt-on-error "IPLeiriaMain.tex"
biber IPLeiriaMain
xelatex -interaction=nonstopmode -halt-on-error "IPLeiriaMain.tex"
xelatex -interaction=nonstopmode -halt-on-error "IPLeiriaMain.tex"
```

说明：`-shell-escape` 参数用于允许 `minted` 调用 Pygments。若机器上未安装 `pygments`，请先安装（见第 2 步）。

## 目录结构
- `IPLeiriaMain.tex` – 主文件
- `Configurations/` – 自定义 .sty 文件
- `Chapters/`、`Matter/`、`Bibliography/`、`Figures/` – 文档内容
- `Code/` – 示例代码

## 注意
- 我未在初步推送中包含 Figures 目录里的二进制大型图片（PDF/PNG）。
- 你可以把本地的 Figures 直接推送到仓库，或在后续提交中使用 Git LFS。