# Unofficial LMU SLDS BA / MA Thesis Template

You can use this repository as a template for your thesis.
It contains a basic structure and some useful settings.

The template is set up in a way that it should be easy to apply other styles, e.g. if you want to publish your thesis as a paper.

## Structure

The `main.tex` file is the main file of your thesis, but should not be used for writing.
It contains the preamble, front matter, and the `\include` commands for the chapters.
The actual content is written in the files in the `chapters` folder.
Chapters in this folder are numbered with two digits, e.g. `10-introduction.tex`.
This way, you can easily add new chapters without having to renumber all existing chapters.
You should not have to edit the `main.tex` file, except for adding or removing `chapters/` files!

Put files that define "meta-data" in the `definitions` folder. Title, author etc. are in the `definitions/metadata.tex` file, while the `definitions/acronyms.tex` and `definitions/math.tex` files contain frequently used acronyms (using the `glossaries` package) and mathematical symbols.

The `bibliography.bib` file contains the bibliography.
You can add new entries to this file and cite them in your thesis.

The `figures` folder contains all figures.
Make sure to use vector graphics whenever possible.
Note you do not need to specify the `figures` folder when including a figure, as it is set a the default path in the preamble.

The `tables` folder contains all tables.
You can use tools like [Tables Generator](https://www.tablesgenerator.com/) to create tables, or use packages like `pgfplotstable` to read data from `.csv` files (see the [`iris_ranges.tex`](tables/iris_ranges.tex) example).

## Style Recommendations

* Prefix labels according to the type of the label, e.g. `fig:`, `tab:`, `eq:`, `sec:`, `lst:`, `itm:`.
* Use `\cref{}` (`\Cref{}` at beginning of a sentence) for references.
* Use natbib-style `\citet{}`, `\citep{}`, `\citealp{}`, `\citeauthor{}`, `\citeyear{}` for citations, depending on the context.
* Use `\emph{}` for emphasis; do not use `\textit{}` or `\textbf{}`.
* Use `\enquote{}` for quotes.
* Use `\dots{}` for ellipses.
* Use `\ldots{}` for ellipses in math mode.
* Use `\ldots{}` for ranges, e.g. "1--10".

## Packages and Settings

The template uses the `scrbook` document class, which is part of the [KOMA-Script](https://www.ctan.org/pkg/koma-script) bundle. It is based on the `book` class, but provides some additional features and settings.

For bibliography, the template uses [BibLaTeX](https://www.ctan.org/pkg/biblatex) with the [Biber](https://www.ctan.org/pkg/biber) backend, with `natbib` compatibility enabled. This allows you to use the `\citet{}` and `\citep{}` commands. This [cheat sheet](http://tug.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf) provides a good overview of the available commands.

The `glossaries` package is used for the list of abbreviations and the list of mathematical notation. The `glossaries-extra` package is used for the list of symbols. The `glossaries` package is also used for the list of acronyms, but the `acronym` package is used for the acronym definitions. This is because the `glossaries` package does not support the `longtable` package, which is required for the list of acronyms.

The LMU exam regulations for Bachelor and Master theses state that the thesis should be a certain number of pages in 11pt Arial.
You can set this option by changing `fontsize=12pt` to `fontsize=11pt` and uncommenting a few lines at the beginning of the `main.tex` file.
However, this does not look very nice and the long lines make the result hard to read.
Arial / Helvetica is an uncommon font for scientific documents in our field.
This template therefore uses 12pt Computer Modern, which is the default font of LaTeX.

## Compilation

The template uses [latexmk](https://www.ctan.org/pkg/latexmk/) for compilation.
To create a PDF, run `latexmk -pdf main.tex` in the root directory of the repository.
This will create a `main.pdf`.
You can also use `latexmk -pvc -pdf main.tex` to automatically recompile the document when a file is changed, but depending on your editor, this might not work properly.

The `main.pdf` file is ignored by git, so you do not have to worry about accidentally committing it.
To commit a PDF-version of your thesis, it is recommended to rename the `main.pdf` file to something like `thesis.pdf` and commit this file.
`git add -f main.pdf` can also be used, but this will also track the file in the future, which is not recommended.

## License

This template is licensed as [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) ("Public Domain Dedication").
To the extent possible under law, mb706 has waived all copyright and related or neighboring rights to this thesis template.
This means that you can do whatever you want with this template, without having to ask for permission or mention the original author.

Since you may want to make your thesis repo public, but under a different license, you should remove this paragraph after cloning the repository to avoid ambiguity.

## TODO

* style recommendations check
* add examples for tables
* add example listing and algorithm
* use all cleveref references
* use acronyms
* add subfigure example
