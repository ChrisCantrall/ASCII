GIT - markdown-syntax.md
DROPBOX FILENAME : markdown syntax refx.md


# EMPHASIS
Markdown treats asterisks (`*`) and underscores (`_`) as indicators of
emphasis. Text wrapped with one `*` or `_` will be wrapped with an
HTML `<em>` tag; double `*`'s or `_`'s will be wrapped with an HTML
`<strong>` tag.

You can use whichever style you prefer; the lone restriction is that
the same character must be used to open and close an emphasis span.

Emphasis can be used in the middle of a word: un*frigging*believable

un*frigging*believable

But if you surround an `*` or `_` with spaces, it'll be treated as a
literal asterisk or underscore.

To produce a literal asterisk or underscore at a position where it
would otherwise be used as an emphasis delimiter, you can backslash
escape it:

\*this text is surrounded by literal asterisks\*


# HEADERS
# This is an H1
## This is an H2
###### This is an H6


# BLOCKQUOTES
Markdown allows you to be lazy and only put the `>` before the first
line of a hard-wrapped paragraph:

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.

Blockquotes can be nested (i.e. a blockquote-in-a-blockquote) by
adding additional levels of `>`:

> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

Blockquotes can contain other Markdown elements, including headers, lists,
and code blocks:

> ## This is a header.
> 
> 1. This is the first list item.
> 2. This is the second list item.
> 
> Here's some example code:
> 
> return shell_exec("echo $input | $markdown_script");


# LISTS
Markdown supports ordered (numbered) and unordered (bulleted) lists.

Unordered lists use asterisks (`*`), pluses (` `), and hyphens (`-`) -- interchangably -- as list markers:

* Red
* Green
* Blue

Ordered lists use numbers followed by periods [start with 1. - sequence doesn't matter]:

1. Bird
2. McHale
3. Parish

List markers typically start at the left margin, but may be indented by
up to three spaces. List markers must be followed by one or more spaces
or a tab.

To make lists look nice, you can wrap items with hanging indents, but if you want to be lazy, you don't have to:

* Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
* Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.

If list items are separated by blank lines, Markdown will wrap the
items in `<p>` tags in the HTML output.

List items may consist of multiple paragraphs. Each subsequent
paragraph in a list item must be indented by either 4 spaces
or one tab. It looks nice if you indent every line of the subsequent
paragraphs, but here again, Markdown will allow you to be
lazy:

* This is a list item with two paragraphs.

This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

* Another item in the same list.

To put a blockquote within a list item, the blockquote's `>`
delimiters need to be indented:

* A list item with a blockquote:

> This is a blockquote
> inside a list item.

To put a code block within a list item, the code block needs
to be indented *twice* -- 8 spaces or two tabs:

* A list item with a code block:

<code goes here>


# CODE
To produce a code block in Markdown, simply indent every line of the
block by at least 4 spaces or 1 tab. 

To indicate a span of code, wrap it with backtick quotes (`` ` ``).
Unlike a pre-formatted code block, a code span indicates code within a
normal paragraph. For example:

Use the `printf()` function.

With a code span, ampersands and angle brackets are encoded as HTML entities automatically, which makes it easy to include example HTML tags. 


# LINKING

## Automatic Links
Markdown supports a shortcut style for creating "automatic" links for URLs and email addresses: simply surround the URL or email address with angle brackets. What this means is that if you want to show the actual text of a URL or email address, and also have it be a clickable link, you can do this:

<http://example.com/>

Automatic links for email addresses work similarly, except that Markdown will also perform a bit of randomized decimal and hex entity-encoding to help obscure your address from address-harvesting spambots.

## Implicit Link Names
The *implicit link name* shortcut allows you to omit the name of the
link, in which case the link text itself is used as the name.
Just use an empty set of square brackets -- e.g., to link the word
"Google" to the google.com web site, you could simply write:

[Google][]

And then define the link:

[Google]: http://google.com/

Because link names may contain spaces, this shortcut even works for
multiple words in the link text:

Visit [Daring Fireball][] for more information.

And then define the link:

[Daring Fireball]: http://daringfireball.net/

Link definitions can be placed anywhere in your Markdown document. I
tend to put them immediately after each paragraph in which they're
used, but if you want, you can put them all at the end of your
document, sort of like footnotes.

## Internal linking

[blockquoting][bq] and multi-paragraph [list items][l] work

[bq]: #blockquote
[l]: #list

## Inline Links
Markdown supports two style of links: *inline* and *reference*. In both styles, the link text is delimited by [square brackets].

To create an inline link, use a set of regular parentheses immediately
after the link text's closing square bracket. Inside the parentheses,
put the URL where you want the link to point, along with an *optional*
title for the link, surrounded in quotes. For example:

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.

## Reference style links
The point of reference-style links is not that they're easier to
write. The point is that with reference-style links, your document
source is vastly more readable.

Reference-style links use a second set of square brackets, inside
which you place a label of your choosing to identify the link:

This is [an example][id] reference-style link.

You can optionally use a space to separate the sets of brackets:

This is [an example] [id] reference-style link.
DO NOT USE - THIS DOES NOT WORK WITH ALL INTERPRETERS

Then, anywhere in the document, you define your link label like this,
on a line by itself:

[id]: http://example.com/ "Optional Title Here"

An itemization of reference style links:

* Square brackets containing the link identifier (optionally
indented from the left margin using up to three spaces);
* followed by a colon;
* followed by one or more spaces (or tabs);
* followed by the URL for the link;
* optionally followed by a title attribute for the link, enclosed
in double or single quotes, or enclosed in parentheses.

The following three link definitions are equivalent:

[foo]: http://example.com/ "Optional Title Here"
[foo]: http://example.com/ 'Optional Title Here'
[foo]: http://example.com/ (Optional Title Here)

**Note:** There is a known bug in Markdown.pl 1.0.1 which prevents
single quotes from being used to delimit link titles.

You can put the title attribute on the next line and use extra spaces
or tabs for padding, which tends to look better with longer URLs:

[id]: http://example.com/longish/path/to/resource/here
"Optional Title Here"

Link definition names may consist of letters, numbers, spaces, and
punctuation -- but they are *not* case sensitive.


# Images
Markdown uses an image syntax that is intended to resemble the syntax
for links, allowing for two styles: *inline* and *reference*.

Inline image syntax looks like this:

![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")

That is:

* An exclamation mark: `!`;
* followed by a set of square brackets, containing the `alt`
attribute text for the image;
* followed by a set of parentheses, containing the URL or path to
the image, and an optional `title` attribute enclosed in double
or single quotes.

Reference-style image syntax looks like this:

![Alt text][id]

Where "id" is the name of a defined image reference. Image references
are defined using syntax identical to link references:

[id]: url/to/image "Optional title attribute"


# ESCAPING CHARACTERS
Markdown allows you to use backslash escapes to generate literal
characters which would otherwise have special meaning in Markdown's
formatting syntax. For example, if you wanted to surround a word
with literal asterisks (instead of an HTML `<em>` tag), you can use
backslashes before the asterisks, like this:

\*literal asterisks\*

Markdown provides backslash escapes for the following characters:

\ backslash
` backtick
* asterisk
_ underscore
{} curly braces
[] square brackets
() parentheses
# hash mark
plus sign
- minus sign (hyphen)
. dot
! exclamation mark

# HORIZONTAL RULES

You can produce a horizontal rule tag (`<hr />`) by placing three or more hyphens, asterisks, or underscores on a line by themselves. If you wish, you may use spaces between the hyphens or asterisks. Each of the following lines will produce a horizontal rule:

* * *

***

*****

- - -

---------------------------------------

# [MULTIMARKDOWN](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide)

## DEFINITION LISTS

MultiMarkdown has support for definition lists using the same syntax used in PHP Markdown Extra. Specifically:

Apple
: Pomaceous fruit of plants of the genus Malus in 
the family Rosaceae.
: An american computer company.

Orange
: The fruit of an evergreen tree of the genus Citrus.

You can have more than one term per definition by placing each term on a separate line. Each definition starts with a colon, and you can have more than one definition per term. You may optionally have a blank line between the last term and the first definition.

Definitions may contain other block level elements, such as lists, blockquotes, or other definition lists.

Unlike PHP Markdown Extra, all definitions are wrapped in `<p>` tags. First, I was unable to get Markdown not to create paragraphs. Second, I didn't see where it mattered - the only difference seems to be aesthetic, and I actually prefer the `<p>` tags in place. Let me know if this is a problem.


## META DATA

### Affiliation

Use this to include an organization that the author is affiliated with, e.g. a university, company, or organization. You can include address information here as well, or use the Address, email, web, and phone metadata fields. You can have more than one line in this field --- use two extra spaces at the end of the line, and a newline character will be used in LaTeX.

### CSS

Used to specify a CSS stylesheet when creating the complete XHTML output.

### Date

Provide a date for the document.

### Format

Set to complete to indicate that a fully-formed XHTML document should be produced. Such a document is ready for processing by an XSLT tool, such as the XSLT files to convert XHTML into LaTeX.

Set to snippet to indicate that no `<head>` or other information should be included. This might be useful for generating (X)HTML output ready for pasting into a weblog, for example.

Note: Some MultiMarkdown tools add this for you (e.g. TextMate using my bundle, and Scrivener.) Duplicating the Format key in these programs should not cause a problem --- let me know if you have trouble.

### Keywords

Provide a list of keywords for the document. I use these to add keywords to PDF's that are produced as well. Keywords can be separated by commas, or placed on separate lines.

### Revision

You can use a string to declare the current version of the document. Displayed on the copyright page when using my memoir XSLT transform.

### Subtitle
Used to provide a subtitle. It ends up in the meta tags, but can be extracted by XSLT for other uses.

### Title

Used to provide the official title of a document. This is set as the `<title>` string within the <head> section of an HTML document, and is also used by other export formats.

### Web
Use this to include the author's web URL. 

### XHTML Header

This is used to include raw XHTML information in the header of a document. You can use this field to add information that will be included in the header of the generated XHTML file. This can be CSS formatting data, or javascript code, or just about anything. I am not responsible for getting that code to work. MultiMarkdown just includes it as is.

Anything included in this field is inserted, unaltered, in the <head> section of the XHTML output. If you do add anything here, the XSLT stylesheet may have to updated to ignore what you added if you want to convert to LaTeX. Let me know what you add, and I can consider updating the XSLT stylesheet to ignore it. Currently it ignores `<style>` sections.

### XHTML XSLT

This is the name of the XSLT file to use to post-process the XHTML file. This can be used to further customize the XHTML output generated by MultiMarkdown. For example, the xhtml-toc.xslt file can add a Table of Contents to the start of XHTML page.

### XMP

This is used to provide a file to be included using xmpincl. Basically, this adds the ability to provide Creative Commons Licensing information in a PDF's metadata. It can also be used for other purposes (beyond the scope of this document.)


## FOOTNOTES

I have added support for footnotes to MultiMarkdown, using the syntax proposed by John Gruber. Note that there is no official support for footnotes yet, so the output format may change, but the input format sounds fairly stable.

To create a footnote, enter something like the following:

Here is some text containing a footnote.[^somesamplefootnote]

[^somesamplefootnote]: Here is the text of the footnote itself.

The footnote itself must be at the start of a line, just like links by reference. If you want a footnote to have multiple paragraphs, lists, etc., then the subsequent paragraphs need an extra tab preceding them. You may have to experiment to get this just right, and please let me know of any issues you find.