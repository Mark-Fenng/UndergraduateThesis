# 哈尔滨工业大学LaTeX论文源码

### 基本信息
本论文以[hithesis](https://github.com/dustincys/hithesis)模板为基础
论文相关的项目源码见[JENA-RL](https://github.com/Mark-Fenng/JENA-RL)

### 版本要求

LaTeX 中的ctex package版本要求：

	ctex >= v2.4.3 (2016年9月份发布)

注意，如果下载最新版本（>= 2018）的texlive或Miktex或Mactex，如果使用自带的模板，可能会出现一些错误，因为自带的版本老。
查看自带版本的命令是

	texdoc hithesis

### 编译方法

1. 生成论文格式文件(第一步要生成 *.cls，*.cfg，*.ist，然后再生成论文)

   - 如果是Linux/Mac执行 （此处作者没测试过Mac，如遇到问题到谈论区可以问一下热心刀客大侠们，比如陈登泰教授、郭大侠等）
	
			latex hithesis.ins
		
   - 如果是Windows执行（作者没测试过，如遇问题同上）
	
			lualatex hithesis.ins

   - 如果喜欢玩 make

			make cls

2. 生成论文的方式

   - 手动狙击（源文件更改后每次编译逐行命令输入一轮）

            xelatex -shell-escape main.tex
            bibtex main
            xelatex -shell-escape main.tex
            xelatex -shell-escape main.tex
            splitindex main -- -s hithesis.ist  # 自动生成索引
            xelatex -shell-escape main.tex
            
   - 半自动精确射击（源文件更改后每次编译敲一次）

            make thesis

   - 全自动火力覆盖（只需要输入一次命令，源文件更改后自动识别更改自动编译）

            latexmk

3. 生成文档（没什么用，因为有文档也基本没人看）

   - 手动狙击（逐行命令输入一轮）

            xelatex hithesis.dtx
            makeindex -s gind.ist -o hithesis.ind hithesis.idx
            makeindex -s gglo.ist -o hithesis.gls hithesis.glo
            xelatex hithesis.dtx
            xelatex hithesis.dtx

   - 半自动精确射击（编译敲一次）

            make doc

### 打印版、电子版

注意，一般情况下，博士论文的打印版要求双面打印，本硕单面。