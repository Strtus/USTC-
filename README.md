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

---

## Git LFS（大文件存储）
为了避免 Git 仓库体积膨胀，我们建议使用 Git LFS 存储 Figures 下的大型图片或 PDF 文件。

1. 安装 Git LFS：

Windows：
```powershell
# 使用 Chocolatey（如你已安装）
choco install git-lfs
# 或使用 Scoop
scoop install git-lfs
# 或从 https://git-lfs.github.com/ 下载 Windows 安装包
```

2. 初始化并跟踪：

```powershell
git lfs install
# 跟踪整个 Figures 目录
git lfs track "Figures/**"
# 可选：跟踪常见二进制扩展
git lfs track "*.pdf"
git lfs track "*.png"
git lfs track "*.jpg"
```

3. 将 `.gitattributes` 和 Figures 文件加入暂存区并推送：

```powershell
git add .gitattributes
git add Figures/**
git commit -m "Add large assets (Figures) via Git LFS"
git push origin main
```

注意：如果你之前已把大文件提交到仓库，需要使用 `git lfs migrate`（会改写历史，慎用）迁移历史：

```powershell
# 警告：会改写历史，请先备份或在团队内沟通
git lfs migrate import --include="Figures/**,*.pdf,*.png,*.jpg"
# 完成后强制推送（如果必要）：
git push --force --all origin
```

4. 克隆包含 LFS 对象的仓库：

```powershell
git clone git@github.com:Strtus/USTC-.git
git lfs pull
```

---

