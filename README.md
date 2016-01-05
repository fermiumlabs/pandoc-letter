# A simple letter template for Pandoc

This template allows you to write letters in Markdown and convert them to nice looking PDFs using [Pandoc][] and [LaTeX][]. It's basically just a copy of Pandoc's [default LaTeX template][latex-template], slightly modified to accept arguments used in the LaTeX letter class, including:

* opening
* closing
* address
* return-address
* postscript
* enclosures list
* carbon-copy list

All of which can be specified in a YAML metadata block. For example:

```yaml
---
author: Aaron
opening: To whom it may concern,
closing: Sincerely,
address:
- 123 Street Rd
- Chicago, IL
return-address:
- My Home
- 456 Road St.
- New York, NY
...
```

Note that each address component should start with a hyphen. The provided example letter can be compiled with the following command:

```shell
pandoc --template=template-letter.tex example/letter.md -o example/letter.pdf
```

You can see the PDF output [here](https://github.com/aaronwolen/pandoc-letter/blob/master/example/letter.pdf).

## Features

The following can be set either as variables when executing `pandoc` or added to the YAML metadata.

`address`
:   Name and address of the recipient; takes a list for a multi-line address.

`author`
:   Writer of the letter; can take a list for a multi-line signature.

`blockquote`
:   Changes style of block quotations to match [bootstrap][].

`cc`
:   Recipients to be carbon-copied; can take a list for multiple recipients.

`closing`
:   Text for the complementary close.

`closing-indentation`
:   Amount for closing signature block to be intended from left margin.

`date`
:   Custom date (current date will be automatically inserted if not specified).

`encl`
:   List of enclosures.

`letterhead`
:   Image file to be used as letterhead (requires the [wallpaper][] package), applied only to the first page.

`opening`
:   Text for the salutation.

`ps`
:   Text to be added at the end of the letter as a postscript.

`return-address`
:   Address of the sender: takes a list to allow a multi-line address.

`signature`
:   Image file for a signature.

`signature-before`, `signature-after`
:   Allows adjustment of vertical space surrounding signature.

[Pandoc]: http://pandoc.org
[LaTeX]: http://www.latex-project.org/
[latex-template]: https://github.com/jgm/pandoc-templates/blob/master/default.latex
[bootstrap]: http://getbootstrap.com/css/#type-blockquotes
[wallpaper]: https://www.ctan.org/pkg/wallpaper