# First-Order Methods Notes Template

这是一个用于中文读书笔记的 XeLaTeX 模板，入口文件为 `main.tex`。

## 目录结构

```text
main.tex                 主文件，编译全部章节
flg/                     全局图像文件夹
config/                  配置文件
  config.tex             总配置文件，集中载入其余配置
  custom.tex             自用宏定义
  format.tex             页面、字号、行距、列表、颜色、页眉页脚、图像路径
  package.tex            宏包配置
  theorem.tex            定理、例题、练习、证明、解答、笔记环境
chap0/                   封面、前言等 tex
  cover.tex
  preface.tex
chap1/
  chap.tex               第一章，可单独编译
  figure/                第一章图像
chap2/
  chap.tex               第二章，可单独编译
  figure/                第二章图像
```

新增章节时，复制 `chap2` 为 `chapN`，然后：

1. 在 `main.tex` 中追加 `\subfile{chapN/chap}`。
2. 在 `config/format.tex` 的 `\graphicspath` 中手动追加 `{chapN/figure/}`。

`\graphicspath` 不能使用通配符。

## 编译

编译全书：

```powershell
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
```

单独编译第一章：

```powershell
cd chap1
latexmk -xelatex -interaction=nonstopmode -halt-on-error "-outdir=../build/chap1" chap.tex
```

## 主要环境

`theorem`、`lemma`、`corollary`、`proposition`、`assumption`、`definition`、`algorithm`、`example`、`exercise`、`remark`、`proof`、`solution`、`note`。

`proof` 和 `solution` 适合放在对应命题、例题或练习的色块内部；`note` 用于写自己的补充、评述和后续要查的内容。
