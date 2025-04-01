# Documentation Styling and Best Practices
As of the 2025 season, the programming team believes that greatly increasing and improving documentation of code, the design process, and the build process is necessary. This document aims to outline some general best practices, tools and guidelines for styling. This page is currently incomplete, and more contributions are welcome.

## Outline
- [Documentation Styling and Best Practices](#documentation-styling-and-best-practices)
	- [Outline](#outline)
	- [Understanding the Markdown Format](#understanding-the-markdown-format)
	- [Tooling](#tooling)
		- [Docs for Programmers](#docs-for-programmers)
		- [Docs for Non-Programmers](#docs-for-non-programmers)
	- [File Naming Conventions](#file-naming-conventions)
	- [General Formatting](#general-formatting)
	- [Sectional Formatting](#sectional-formatting)
	- [Submitting Documentation and Signatures](#submitting-documentation-and-signatures)

## Understanding the Markdown Format
Before you begin editing and writing documentation, you should understand the general Markdown format, and how to write it. Markdown files are essentially text documents, which contain special syntax that gets turned into a nice looking page. The formatting syntax is fairly simple and easy to grasp, so with a little practice it shouldn't be too hard to learn. To familiarize yourself with the syntax, you should first try opening files in just a plain text editor, instead of a nice Markdown editor which will be discussed below. You might notice the use of hashes (#) which denote headers, and maybe the use of a link, which consist of a pair of opening square brackets [] containing the link text, and a pair of parentheses () directly to it's right, which contains the link. These are just a couple features that Markdown has that make writing documentation far easier. Keep digging through Markdown files and exploring, and you'll quickly discover many of the other syntax features. There are many of these features, and several flavors of Markdown with different features. If you still have questions, or want more advanced features in your documentation, refer to [The Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/) or the [GitHub Syntax Guide](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax), although some of the GitHub Flavored Markdown-specific features may not work on these docs.

## Tooling
Before you write any Markdown, you probably want a decent text editor that can render Markdown and give you decent hints while you write it. There are two perspectives for this problem, the programming angle and the non-programming angle. Both will be discussed.

### Docs for Programmers
When writing documentation, you will probably find it easiest to write alongside your code. For this reason, this documentation repository supports (and encourages) the use of Visual Studio Code to edit documentation. The repository already contains the necessary VSCode workspace with recommended Extensions that make editing Markdown more simple. This by default incorporates a Spell-Checker, advanced Markdown tools and syntax highlighting, and a better preview window. This greatly increases the ease-of-use of VSCode for text editing and preview. It also minimized the amount of applications open on a system, which may be necessary for devices such as the shared programming laptops.

### Docs for Non-Programmers
Although Visual Studio Code is recommended for editing and maintaining documentation, it is also possible (and easier, to an extent) to use [Obsidian](https://obsidian.md). Obsidian is a straightforward, dedicated Markdown editor with a diverse set of plugins and customization. This repository also contains several plugins and pre-configured options that make working with Obsidian more pleasant for the end user. The drawback to using Obsidian is that the configuration for the web-side of things is hidden and can't be edited. This means that in your pull request (See [#Submitting Documentation and Signatures](#submitting-documentation-and-signatures)), either a programmer will have to make the changes for you, or you'll need to manually edit the files in your own code editor or notepad. This isn't a big problem but it can inhibit the workflow of writing quick documentation. 

## File Naming Conventions
As is with programming, writing documentation also requires a convention to keep things organized. When creating a new file, the name should be considered based on the intended topic. File names should be all lowercase, with hyphens to replace spaces. The file name should be descriptive while remaining relatively short ($20\leq$ characters), ending in a `.md` file extension. These should be placed into an existing folder, or a new folder with a short but descriptive name. These restrictions are in place because of the way that the website is built from Markdown (see [Programming/Administration](/docs//programming/administration.md) for more information).

## General Formatting
There is generally a clean set of rules for writing effective documentation in Markdown, starting with headers. As mentioned before, a Markdown header is made with a hash (#), but multiple can be used to create smaller header text, just as a higher `<h>` tag creates a smaller header. In any given document, you only want a single header that uses one hash, with the rest of the headers using 2 or 3 hashes (or more if necessary). When dividing a document up, you will likely want a header to separate main ideas, and potentially sub-headers for smaller ideas. For *italicizing* text, place it between `*asterisks*`, and for **bolding** it use `**double asterisks**`. As mentioned before, links can be made with `[Square brackets containing text](https://and-a-link-in.parantheses)`. These can be used across an entire document to provide useful information. Similarly, lists can be used in Markdown to create outlines of what is covered in a given page, which is highly recommended and can be seen at the top of this document. A list can be formatted with hyphens, where 
```
- This is a top-level list item
	- This is a secondary item
	- [And this is a list item with a link](https://pascalrr.gay)
```
By providing a table of contents formatted as a markdown list, your document becomes vastly more accessible and easier to understand or jump to a specific section. If you are using the recommended extensions for maintainers of these docs in VSCode, you can automatically generate a Table of Contents with 'Markdown All in One'. For convenience, this can also be set to a key-bind. To add an image, the syntax follows the format of the link `![but with a leading exclamation mark](https://iamanimageurl.com/image.png)` When embedding images into a given document, you **must** add an alternative text inside of the square brackets, as this provides critical accessibility information to insure that our docs can be used by anyone. 

## Sectional Formatting
When formatting individual sections, you may want more fine grained control over what is within that section. For this, there are many other tricks such as incorporating HTML elements and custom style, or things such as data tables. If you want to make a section thats hidden, for example, you can use the html `<details>` tag. As Markdown is just rendered into HTML, this works just fine, allowing you to have
<details>
	<summary>A hidden section of text</summary>
	Which can be done like this

	<details>
		<summary>With the dropdown label here</summary>
		And your content here!
	</details>

</details>
<br>

This is very useful for something that doesn't need to be visible at all times, like [hiding different OS options](/docs/programming/pipenv.md#setting-up-pipenv). There are also other useful sectional syntax, such as tables which can be used to organize information. When inserting a table, insure that the width of the table is consistent. For example,
| Column 1      | Column 2    |
| -----------   | ----------- |
| Line 2        | Line 2      |
| A bigger section on line 3 | Which makes the table not align|

These tables are useful for having different figures to show information in a section. A table can be used by inserting a basic structure, with the following being an example of the table above:
```
| Column 1      | Column 2    |
| -----------   | ----------- |
| Line 2        | Line 2      |
| A bigger section on line 3 | Which makes the table not align|
```


## Submitting Documentation and Signatures
As with all files modified and added through Git, documentation files will contain your username and email address. These details, as well as the time you edited the document, may be added to the bottom of each page in the documentation. This is just meant to show who to ask for information on a specific set of documentation, as well as for records keeping. When submitting documentation, you should first create a new branch and move your changes to that branch. This will allow you to create a pull request with your changes, that can be added after review if needed. Once you have created your pull request, it can be merged in to the main documentation and will be publicly available. For more information on Git, especially for non-programmers, refer to [the Git Usage Documentation](/docs/standards/git-usage).