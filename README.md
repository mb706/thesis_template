# Unofficial LMU SLDS BA / MA Thesis Template

You can use this repository as a template for your thesis.
It contains a basic structure and some useful settings.

The template is set up in a way that it should be easy to apply other styles later, e.g. if you want to publish your thesis as a paper.

## General Advice

This template not only sets up LaTeX in a way that it produces a reasonably pretty thesis.
It also suggests a structure and gives some advice about how and what to write at what point in the thesis.

There are, of course, many ways to structure a thesis, and this template only makes one particular suggestion.
You may have to re-order a few chapters, or split or merge a few of them, according to your taste and according to the particular thing you are writing about.

Particular alternative possibilities are:

* Split up "Background", "Related Work", or "Methods" into different first level chapters and use the names of concrete methods, instead of "Background", "Methods" etc., as main chapter headings.
* If doing multiple experiments that differ in major ways: Instead of having "Experiments", "Results" chapters, make one "Experiments" chapter with sections for each experiment with experiment and results combined

The format suggested here, however, is particularly well suited when you plan to publish the thesis as a paper later.
I also think that the advice in the template about *what* to put *where* in the thesis is sound, and that even when merging or splitting chapters, you should try to adhere to it in principle.
This includes points about not presenting previously unmentioned experimental results in the "discussion" or "conclusion", or about separating the descriptions of aspects that are intrinsic to your method ("Methods") and the description of particular choices made in your experiments ("Experiments").

### Your Target Audience

When writing a scientific paper, you are writing to inform other scientists that are relatively familiar with the subject matter.
This is different for a thesis, where your goal is at least partially to show that you understand the subject matter at hand.
You will therefore have to describe some things in somewhat more detail than what you find in scientific papers.

As your target audience, try to imagine your classmates who study the same subject as you do, but who have not done the reading that you have done for your particular thesis project.
Are they able to understand the reasoning in your thesis?
Would they be able to implement your algorithms (to a reasonable degree of faithfulness), given how you describe it in your text?
Would they understand why you draw the conclusions that you do, from your experimental results?

What is particularly relevant here is that you will need to describe and explain existing results, algorithms, libraries etc. that you make use of to a greater detail than you otherwise would:
Unlike scientific papers, one should be able to understand your thesis without having to read through referenced material.
This does not mean including every detail, but relevant information that is necessary to understand your thesis should be given.

## Structure

The `main.tex` file is the main file of your thesis, but should not be used for writing.
It contains the preamble, front matter, and the `\include` commands for the chapters.
The actual content is written in the files in the `chapters` folder.
Chapters in this folder are numbered with two digits, e.g. `10-introduction.tex`.
This way, you can easily add or remove chapters without having to renumber all existing chapters.
You should not have to edit the `main.tex` file, except for adding or removing `chapters/` files!

Put files that define "meta-data" in the `definitions` folder.
Title, author etc. are in the `definitions/metadata.tex` file, while the `definitions/acronyms.tex` and `definitions/math.tex` files contain frequently used acronyms (using the `glossaries` package; see comments in `definitions/acronyms.tex` about how to use it) and mathematical symbols.

The `bibliography.bib` file contains the bibliography.
You can add new entries to this file and cite them in your thesis.
You do not necessarily need to remove entries from the `.bib`-file that you are not using.
LaTeX only puts entries in your bibliogrpahy that are actually referenced.

The `figures` folder should contain all figures.
Make sure to use vector graphics whenever possible.
Note you do not need to specify the `figures` folder when including a figure, as it is set a the default path in the preamble.

The `tables` folder contains all tables.
You can use tools like [Tables Generator](https://www.tablesgenerator.com/) to create tables, or use packages like `pgfplotstable` to read data from `.csv` files (see the [`iris_ranges.tex`](tables/iris_ranges.tex) example).

## Style Recommendations

* Use "title case" (i.e. capitalization of most words) for titles of chapters and sections, but use normal sentence case for subsections and lower ranking headings. 
* Prefix labels according to the type of the label, e.g. `fig:`, `tab:`, `eq:`, `sec:`, `lst:`, `itm:`.
* Use `\cref{}` (`\Cref{}` at beginning of a sentence) for references.
* Use a tilde (`~`) to insert "non-breaking space", i.e. spaces that should not be broken over a line.
  E.g. write `method~X` to avoid having the `X` slip to the new line.
  This would also be necessary when referencing figures etc., e.g. `See Figure~\ref{fig:results}`, but the `\cref` command already takes care of this, so just use `See \cref{fig:results}`.
* Use backslash-space after periods that end abbreviations like i.i.d., e.g., i.e., and so on.
  Otherwise, LaTeX thinks it is a sentence-ending period and produces a larger space than the space between words in normal sentences.
  Example: `The main assumption here is that error terms are i.i.d.\ normally distributed`.
  This should not be used if the period is *actually* ending a sentence, e.g. often after `etc.`, or if a comma follows right after the period without a space.
* It is a good idea to start a new line after every sentence.
  This makes tracking changes easer (particularly when using `git`), and also gives good visual feedback on wheter your sentences are generally too long or too short.
* Use natbib-style `\citet{}`, `\citep{}`, `\citealp{}`, `\citeauthor{}`, `\citeyear{}` for citations, depending on the context.
* Use `\emph{}` for emphasis; do not use `\textit{}` or `\textbf{}`.
* Use `\enquote{}` for quotes.
* Use `\dots{}` for ellipses in text, and `\ldots{}` for ellipses in math mode.
* Use hyphens (minus-sign, `-`) inside words ("well-known method").
* Use em-dashes (tripple-minus, `---`) for parenthetical sentences.
  There should be no spaces around em-dashes: `This result---although not conclusive---suggests that...`.
  Use em-dashes sparingly. 
* Use en-dashes (double-minus, `--`) for numeric ranges in text, e.g. "1--10", and `\ldots{}` for ranges in math mode.
* Always use math-mode when referring to variables, i.e. write `$x$` instead of just `x` when referring to a variable *x*.

## Packages and Settings

The template uses the `scrbook` document class, which is part of the [KOMA-Script](https://www.ctan.org/pkg/koma-script) bundle.
It is based on the `book` class, but provides some additional features and settings.

For bibliography, the template uses [BibLaTeX](https://www.ctan.org/pkg/biblatex) with the [Biber](https://www.ctan.org/pkg/biber) backend, with `natbib` compatibility enabled.
This allows you to use the `\citet{}` and `\citep{}` commands.
This [cheat sheet](http://tug.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf) provides a good overview of the available commands.

The `glossaries` package is used for the list of abbreviations.

The LMU exam regulations for Bachelor and Master theses state that the thesis should be a certain number of pages in 11pt Arial.
You can set this option by changing `fontsize=12pt` to `fontsize=11pt` and uncommenting a few lines at the beginning of the `main.tex` file.
However, this does not look very nice and the long lines make the result hard to read.
Arial / Helvetica is an uncommon font for scientific documents in our field.
This template therefore uses 12pt Computer Modern, which is the default font of LaTeX.

## Compilation

(If you are using overleaf, you can ignore this section.)

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
This means that you can do whatever you want with this template, without having to ask for permission or mentioning the original author.

Since you may want to make your thesis repo public under a different license, *you should remove this paragraph after cloning the repository to avoid ambiguity*.

## TODO

* style recommendations check
* add examples for tables
* add example listing and algorithm
* use all cleveref references
* use acronyms
* add subfigure example
