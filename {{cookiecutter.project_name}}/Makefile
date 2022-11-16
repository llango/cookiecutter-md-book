# 呈现最终的PDF输出文件
# -----------------------------

# 重要文件名
OUT_FILE = {{cookiecutter.output_filename}}
TEX_FILE = template.tex
BIB_FILE = biblio.bib
HIGHLIGHT_FILE = highlight.theme

# 主项目目录
SRC_DIR = src
TEX_DIR = tex
FIG_DIR = fig
STY_DIR = sty
BIB_DIR = bib
OUT_DIR = out

.PHONY: format pdf

FILES=`cat toctree.txt`

pdf:
	@mkdir -p $(OUT_DIR)
	pandoc                        				\
	  --from         markdown     				\
	  --to           latex        				\
	  --out          $(OUT_DIR)/$(OUT_FILE) 		\
	  --template     $(TEX_DIR)/$(TEX_FILE) 		\
	  --pdf-engine   xelatex      				\
	  --resource-path=.:$(FIG_DIR)				\
	  --highlight-style $(STY_DIR)/$(HIGHLIGHT_FILE)	\
	  --bibliography $(BIB_DIR)/$(BIB_FILE) 		\
	  $(FILES)

format:
	@echo "格式化文件..."
	latexindent cover.tex -s -o cover.tex -y="defaultIndent: '  '"
	@echo "删除日志文件..."
	rm -f indent.log
	@echo "完成!"

clean:
	@echo "清除输出文件..."
	rm -rf $(OUT_DIR)
	@echo "完成!"

