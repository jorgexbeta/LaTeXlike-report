# LaTeXlike-report
A simple report for Typst with LaTeX style, fully customizable.

## Usage
You can use this template in the Typst web app by clicking "Start from template" on the dashboard and searching for `LaTeXlike-report`.

Alternatively, you can use the CLI to kick this project off using the command

```shell
typst init @preview/LaTeXlike-report
```

Typst will create a new directory with all the files needed to get you started.

## Configuration

The template exports one function `LaTeXlike-report` with the following named parameters:

### Cover Parameters
- `author (str)`: The main author of the document (must be a string)
- `title (content)`: The main title of the report
- `subtitle (content)`: The document's subtitle
- `participants (content)`: List of additional authors (the main author appears first)
- `affiliation (content)`: Institution or academic affiliation
- `year (content)`: Publication year of the document
- `class (content)`: Academic class or subject
- `other (content)`: Additional optional information 
- `date (content)`: Document date (can use #datetime.today().display() for current date)
- `logo (image)`: Institutional logo image (usage: image("path/to/image.svg"))

### Theme and Language Configuration
- `theme-color (color)`: Main theme color (see [color](https://typst.app/docs/reference/visualize/color/) for more information)
- `lang (str)`: Document language ("es" for Spanish, "en" for English, etc)
- `participants-supplement (str)`: Text preceding the authors list (adjusts based on language)

### Font Configuration
- `title-font (str)`: Font used for titles
- `font (str)`: Main document text font
- `font-size (length)`: Main font size (default: 13pt)
- `font-weight (number)`: Font weight (default: 400)

### Mathematics Configuration
- `math-font (str)`: Font for mathematical equations
- `math-weight (number)`: Mathematical font weight
- `math-ref-supplement (str/function)`: Supplement for mathematical references (none, auto, or custom)
- `math-numbering` (see [numbering](https://typst.app/docs/reference/model/numbering/)): Equation numbering style (default: "(1.1)")
** From [equate](https://typst.app/universe/package/equate) package **
- `math-number-mode (str)`: Numbering mode ("label" or "line")
- `math-sub-numbering (boolean)`: Enables sub-equation numbering (true or false)

### Page Style
- `pagebreak-section (boolean)`: Inserts page break after level 1 headings (true or false)
- `show-outline (boolean)`: Shows or hides table of contents (true or false)

### Headers and Footers (from [chic header](https://typst.app/universe/package/chic-hdr) package)
You can add images, text, the number of current page, etc, or put none if you dont want some part of the header or footer.
Some usefull function: `chic-page-number()`, `chic-heading-name()`
- `h-l (content)`: Left header content 
- `h-r (content)`: Right header content
- `h-c (content)`: Center header content 
- `f-l (content)`: Left footer content
- `f-r (content)`: Right footer content
- `f-c (content)`: Center footer content

## Especial Features
### Unnumbered headings
You can use `<nonumber>` at the end of the same line of your heading to toggle to unnumbered headings, similar to `\section*` in LaTeX
```typst
= Unnumbered heading <nonumber>
= <nonumber> Not a unnumbered heading
```
Unnumbered headings wont apear in the outline.
### Custumize outline
You can custumize the outline by disabling the default and then using a show rule and calling the function like [here](https://typst.app/docs/reference/model/outline/).
```typst
#show: LaTeXlike-report.with(
.....
show-outline:false,
..... )
#show outline.entry: it => link(
  it.element.location(),
  it.indented(it.prefix(), it.body()),
) //this is just an example, it can be however you like
#outline()
  ```
