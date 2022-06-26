Yes, it's in English. The fellow who translates is busy with his studies. If you want to help, raise an issue on the repo. The quickest way to translate is to use a machine translator, proofread side by side with the source document, and make corrections when you think it's wrong or clumsy in the target language.

# Print extension

[Marketplace page](https://marketplace.visualstudio.com/items?itemName=pdconsec.vscode-print)

[English version](https://github.com/PeterWone/vsc-print) by Peter Wone

[ENGLISH](README.md) | [FRANCAISE](README.fra.md) | [DEUTSCH](README.deu.md) | [ESPAGNOLE](README.esp.md) | [中文CHINESE](README.zho.md) | [Add a language](how-to-add-a-language.md)

## Markdown and source code, styled for print

* Print source code
* Print Markdown fully rendered

Source code gets line numbers and syntax colouring. Markdown is rendered with VS Code's preview rendering pipeline &mdash; many Markdown extensions work with printing.

## Platform independent printing

Print-jobs are rendered as styled HTML and served from an embedded webserver. When you print, your local web browser is launched to load the print-job and give you printing options like page orientation and margin size. So if you have a local browser that can print, and VS Code can launch it, you're in business. Known user platforms include Windows, Linux and OSX. 

### Troubleshooting on first launch

Print worked for thirty thousand people out of the box, but sometimes local settings and permissions can spoil the fun. Here are the problems we've seen so far. If something else is wrong, or you have an improvement idea, we invite you to log an issue on the GitHub repository.

#### Nothing seems to happen

If you try to print and nothing happens, restart VS Code. If it still doesn't work, your system may have a configuration or permission problem that won't let the browser launch. The default Firefox browser on Ubuntu gives trouble out of the box. Install Chromium (or Chrome, Edge, Brave...) and make it the default browser. If you don't want to make Chromium the default browser, read the manual for details of how to use a specific browser for printing and use Chromium to print.

#### Browser launches but no page loads

Your system settings are likely interfering with the embedded webserver. Aggressively locked-down network settings can do this. It's probably permissions. Whoever interfered with networking permissions should troubleshoot this.

#### Browser launches and shows an error message instead of a print-job

Examine the error message. Generally it's some sort of permission denied on aggressively locked down systems.

## Classic user experience

![Toolbar snap with print icon](https://user-images.githubusercontent.com/5498936/53408273-d853d480-3a09-11e9-8936-d37189dce8c5.PNG)

The print icon on the toolbar prints the document in the active editor.

If you have a text selection that crosses at least one line-break you can right click and choose `Print` from the context menu to send just the selection to the printer. In the absence of a multi-line selection the entire document is printed. You can control the position of `Print` in this menu, or remove it altogether.

![context-menu-editor](https://user-images.githubusercontent.com/5498936/53408378-05a08280-3a0a-11e9-8e88-0088089e0d07.png)

Or you can right-click on a file in the file explorer pane and choose Print from the context menu.

![context-menu-file-explorer](https://user-images.githubusercontent.com/5498936/53408376-05a08280-3a0a-11e9-9912-31e869db64d5.png)

## Features

Printing on Mac, Linux and Windows

* Entirely local in operation, no dependence on cloud services (third party Markdown extensions may introduce remote dependencies)
* Syntax colouring in a wide range of familiar colour schemes 
* Optional line numbering
* Adjustable line spacing (1, 1.5, 2)
* Print a selection of code with line numbers matching the editor
* Specify a browser other than your default
* Markdown documents are rendered when you print them (or not, there's a setting)
* Works with Microsoft remote host extensions for SSH, WSL and Docker containers

## Requirements

You'll need a web browser and access to a printer.

This extension is tested with Windows 10 with current builds of Chrome, Edge and Firefox.
I can't test on a Mac because I don't own one. Likewise I don't have any systems running Windows XP, 7 or 8.
If you use an untested combination then report bugs with test documents and snaps of failed outcomes.

## Extension Settings

VS Code Printing is highly configurable. Settings can be modified by going to Code > Preferences > Settings > Extensions > Printing.

**A detailed breakdown of these settings can be found in [the manual](https://github.com/PeterWone/vsc-print/blob/master/manual.md).**

## Choice of browser

The browser used will affect your experience.  

### Recommended for printing

Any Chromium derived browser should be fine. The following are known to work well.
* Brave
* Chromium
* Chrome
* Edge

### Not recommended for printing

* Firefox doesn't close the browser after printing completes.
* Edge Classic is no longer supported.
* Internet Explorer is not supported.

## Known Issues

### Markdown extensions and remoting

To use Print with a remote host you must install it **on the remote host**. 

To get the benefit of a Markdown extension when printing a document from a remote host, the Markdown extension must be built with an `extensionKind` of `workspace` _and_ it must be installed to the remote host. Most such extensions are not built for `workspace` but can be trivially fixed by the author. Raise an issue on the repo of the extension you want. 

Chrome may retain your printer, paper size and margin selections between print jobs.

Some Chrome command line options cause errors to be reported, even though printing succeeds. 

### Spaces in paths

On Windows you can't supply command-line options on the alternate browser path because we automatically put quotes around your path in case of spaces in file or folder names. (On other platforms auto-quoting is not done and you must manually escape spaces in file and folder names.) Work around this by creating a batch file in the same directory as the browser executable and use this to specify the options you require. For the browser path, supply the path to the batch file. Don't forget to pass through the URL parameter.

### Interference from Chrome plugins

Some Chrome plugins interfere with print job styling. While it is possible to suppress plugins with `--disable-plugins` this doesn't work when there is already a running instance of Chrome. The `--incognito` switch suppresses plugins when there is a running instance, but has its own problems.

For better results burn some disk space and install another browser such as Chromium, and use this for printing. You may be able to achieve a similar result without needing two browsers by using profiles on Edge.

### Indirect Internet dependencies

The Math+Markdown extension (installs the KaTeX plugin) requires an internet connection for stylesheets and fonts. You must also configure a stylesheet reference. Details are in the manual.

## Release Notes

### 0.9.15

- Fixed issue 98 - print Markdown rendered from unsaved files
- Added instructions on modifying Markdown plugin extensions to allow them to work with remote hosts.

### 0.9.14

- Emergency bugfix for printing unsaved files
- Emergency bugfix for printing files with Azure Uris that are not backed by a complete filesystem

### 0.9.13

- Emergency bugfix for printing a selection

### 0.9.12

- Emergency bugfix for resolution of local resources referenced by Markdown

### 0.9.11

- Total rewrite of file management in support of remote file systems
- Glob brace expressions can be nested
- Exclusion is forced for
  - `**/*.{exe,dll,pdb,pdf,hex,bin,png,jpg,jpeg,gif,bmp}` 
  - `{bin,obj}`
- Change to licence terms refusing licence to persons who fail to read the manual or seek assistance on by raising an issue on the GitHub repository


### See changelog for complete history.
