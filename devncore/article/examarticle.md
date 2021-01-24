# How to Create a Article
This document covers the purpose of creating an Article better.

## Use markdown grammar to create a good looking document
> Markdown is a text-based markup language created by John Groover in 2004 and is easy to write and read and convert to HTML. Using a very simple structure of grammar using special symbols and characters, content can be written more quickly and recognized more intuitively on the web. The reason why Markdown has recently begun to gain popularity is because of GitHub (https://github.com). README.md, which records information about GitHub's repository repository, was the first markdown document anyone using GitHub would encounter. As the strength of the simple recording of installation methods, source code descriptions, and issues through markdown is highlighted, it will gradually spread to various places.


## History
In 2002 Aaron Swartz created atx, "the true structured text format". Swartz and John Gruber then worked together to create the Markdown language in 2004,[2][3] with the goal of enabling people "to write using an easy-to-read and easy-to-write plain text format, optionally convert it to structurally valid XHTML (or HTML)".[4]

Its key design goal is readability – that the language be readable as-is, without looking like it has been marked up with tags or formatting instructions,[9] unlike text formatted with a markup language, such as Rich Text Format (RTF) or HTML, which have obvious tags and formatting instructions. To this end, its main inspiration is the existing conventions for marking up plain text in email, though it also draws from earlier markup languages, notably setext, Textile, and reStructuredText.[9]

Gruber wrote a Perl script, Markdown.pl, which converts marked-up text input to valid, well-formed XHTML or HTML and replaces angle brackets '<' '>' and ampersands '&' with their corresponding character entity references. It can take the role of a standalone script, a plugin for Blosxom or a Movable Type, or of a text filter for BBEdit.[4]

## Standardization
Markdown has been characterised by an informal specification[11] and a reference implementation for conversion to HTML. Over time, many Markdown implementations have appeared. People developed these mostly driven by the need for additional features on top of the base syntax—such as tables, footnotes, definition lists (technically HTML description lists), and Markdown inside HTML blocks. The behavior of some of these diverges from the reference implementation. At the same time, a number of ambiguities in the informal specification have attracted attention.[12] These issues spurred the creation of tools such as Babelmark[13][14] to compare the output of various implementations,[15] and an effort by some developers of Markdown parsers for standardisation. However, Gruber has argued that complete standardization would be mistaken: "Different sites (and people) have different needs. No one syntax would make all happy."[16]

In March 2016 two relevant informational Internet RFCs were published:

> RFC 7763 introduced MIME type text/markdown with the original variant.
> RFC 7764 discussed and registered the variants MultiMarkdown, GitHub Flavored Markdown (GFM), Pandoc, CommonMark, and Markdown Extra among others.[17]

## CommonMark
From 2012, a group of people, including Jeff Atwood and John MacFarlane, launched what Atwood characterized as a standardization effort.[20] A community website now aims to "document various tools and resources available to document authors and developers, as well as implementors of the various Markdown implementations".[21] In September 2014, Gruber objected to the usage of "Markdown" in the name of this effort and it was rebranded as a new dialect named CommonMark.[22][23] CommonMark.org published several versions of a specification, reference implementation, and test suite, and "[plans] to announce a finalized 1.0 spec and test suite in 2019."[24] No 1.0 spec has since been released as major issues still remain unsolved.[25] Nonetheless, the following sites and projects have adopted CommonMark: Discourse, GitHub, GitLab, Reddit, Qt, Stack Exchange (Stack Overflow), and Swift.

# Markdown Extra
Markdown Extra is a lightweight markup language based on Markdown implemented in PHP (originally), Python and Ruby.[31] It adds features not available with plain Markdown syntax. Markdown Extra is supported in some content management systems such as, for example, Drupal[32] and TYPO3.[33]

Markdown Extra adds the following features to Markdown:

- Markdown markup inside HTML blocks
- Elements with id/class attribute
- "Fenced code blocks" that span multiple lines of code
- Tables[34]
- Definition lists
- Footnotes
- Abbreviations
