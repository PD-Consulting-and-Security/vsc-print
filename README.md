> Could I have some feedback please? I find it hard to believe this software is perfect. In the unlikely event that it _is_ perfect please say so in a review so I can feel good about it.

# Visual Studio Code Printing

Code listings are iconic in a sense older than graphical user interfaces. I can't give you dot-matrix on blue-lined 15" fanfold paper, but I _can_ give you line numbers, and something _really_ old school that I always wanted but never saw anywhere in a code listing: double spacing to allow annotation with a pencil.

![Toolbar snap with print icon](https://user-images.githubusercontent.com/5498936/53408273-d853d480-3a09-11e9-8936-d37189dce8c5.PNG)

The print icon on the toolbar prints the document in the active editor.

If you have a text selection that crosses at least one line-break you can right click and choose Print from the context menu to send just the selection to the printer. In the absence of a multi-line selection the entire document is printed.

![context-menu-editor](https://user-images.githubusercontent.com/5498936/53408378-05a08280-3a0a-11e9-8e88-0088089e0d07.png)

Or you can right-click on a file in the file explorer pane and choose Print from the context menu.

![context-menu-file-explorer](https://user-images.githubusercontent.com/5498936/53408376-05a08280-3a0a-11e9-9912-31e869db64d5.png)

## Features

Printing on Mac, Linux and Windows
* Entirely local in operation, is not dependent on cloud services
* Syntax colouring in a selection of named colour schemes
* Optional line numbering
* Adjustable line spacing (1, 1.5, 2)
* Print a selection of code with line numbers matching the editor
* Specify a browser other than your default

## Requirements

You'll need a web browser and access to a printer.

## Extension Settings

This extension contributes the following settings:

* `print.alternateBrowser`: enable/disable an alternate browser
* `print.browserPath`: the path to a web browser
* `print.colourScheme`: the stylesheet used for colouring syntax
* `print.fontSize`: the font size
* `print.formatMarkdown`: render markdown as styled HTML when printing
* `print.lineNumbers`: on, off or inherit (do same as editor)
* `print.lineSpacing`: single, line-and-a-half or double spaced

## Known Issues
An issue has been reported where multiple concurrent copies of VS Code (multi-monitor workaround) experience port collisions. This is currently being investigated.

Tab size is now governed by the editor tab size setting. This exploits the experimental CSS `tab-size` property, which works on Opera, Firefox and Chrome, but **not** Edge. When Edge starts using the Chromium engine this will change.

The list of stylesheets had to be severely shortened to work around a problem with large lists in VS Code. When handling of large lists is improved the full list of 90 stylesheets will be restored. I reported this issue when first releasing VSCode Print, and the VS Code team believes it is corrected in the current Insider build so this should be resolved soon.

Chrome has a tendency to remember too much about printers, paper sizes and margins especially if you abort. If you try another browser and a problem goes away, it's Chrome helping too much and the solution is to load a web page, change your settings and print something, then exit clean.

## Release Notes

Earlier versions occasionally had problems with port collisions causing printing to fail. A manual retry or three always fixed it but this was ugly. Correcting the problem was the primary focus of 0.5.3, and I am pleased to finally remove it from known issues.

Also addressed is [issue #17](https://github.com/PeterWone/vsc-print/issues/17) which moves responsibility for language detection from highlightjs (the library used for syntax colouring) to VS Code, falling back to highlightjs when an incompatible language code is produced.

Microsoft Edge always prompts for permission to close the browser after printing, which can be annoying.
Firefox doesn't prompt, it just plain doesn't close the browser, which is beyond annoying. As a result, Chrome is the recommended browser for printing.

## 0.6.0
- Colour scheme stylesheet setting is no longer presented as a combo-box. Instead, there is a command that presents a file-browse dialog and updates the setting.
- Language detection falls back to highlightjs when VS Code produces an incompatible language identifier.

## 0.5.3

- Tab size respects editor setting.
- Responsibility for language detection moved from highlightjs to VS Code.
