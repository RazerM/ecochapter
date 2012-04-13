#Why would I use `ecochapter`?

If you want to use the `\chapter`, `\section` and `\sub...section` commands in LaTeX, but find they use too much space, `ecochapter` is for you!

#Installation
Simply download ecochapter.sty to same directory as your `*.tex` file and include it in your LaTeX document

```latex
\usepackage{ecochapter}
```

The commands are as follows:

```latex
\echapter*+[ToC Title]{Title}
%	*			optional;	Prevent numbering
%	+			optional;	Do not put chapter heading on new page.
%	[ToC Title]	optional;	Name to use in Table of Contents.
%	{Title}		mandatory;	Chapter title.

\esection*+[ToC Title]{Title},
\esubsection*+[ToC Title]{Title},
\esubsubsection*+[ToC Title]{Title},
%	*			optional;	Prevent numbering
%	+			optional;	No vertical space above section
%	[ToC Title]	optional;	Name to use in ToC
%	{Title}		mandatory;	Title

\eappendix+[ToC Title]{Title}
%	+			optional;	Do not start new page.
%	[ToC Title]	optional;	Name to use in Table of Contents.
%	{Title}		mandatory;	Appendix title.
```

#Simple usage
The only parameter you need for each command is the title,

```latex
\echapter{Title} % Display a numbered chapter on a fresh page
\esection{Title} % Display numbered section with default spacing
```

That seems simple enough, right?

#Other parameters
##I don't need numbers
The asterisk simply produces a heading without numbering,

```latex
\echapter*{Title} % Display non-numbered chapter on a fresh page
\esection*{Title} % Display non-numbered section with default spacing
```

##What's that plus used for?
The plus character is key to saving space with `ecochapter`. It has two possible meanings.

* `\echapter`, `\eappendix`

    These commands give themselves a new page by default. Use `+` to prevent them from doing so.
* `\esection`, `\esubsection`, `\esubsubsection`

    The section commands are often used directly after another heading command. When this is the case, use `+` to claim back some of the space normally reserved for separating a heading from normal text. **See examples 1 and 2 below**

###Example 1
This is the wrong way to format your document. It results in a large gap between **Chapter** and **Section**.

```latex
\echapter{Chapter}
\esection{Section} 
```

###Example 2
This is the correct usage of `+`; to **format successive headings correctly**.

```latex
\echapter{Chapter}
\esection+{Section} 
```

Usage of `+` is the same for `\esection` followed by `\esubsection` and so on.

#Appendices
`\eappendix` is **not** a direct replacement for `\appendix`, which does something entirely different in LaTeX.

`\appendix` has no parameters and simply resets the numbering used by `\chapter`, `\section` and so on so that all headings following the `\appendix` command are numbered differently. This numbering change also affects `ecochapter`!

An example:

```latex
\chapter{Introduction} % Outputs "Chapter 1 \ Introduction"
...
\chapter{Theory} % Outputs "Chapter 2 \ Theory"
...

\appendix
\chapter{Data} % Outputs "Appendix A \ Data"
```

Same example using `ecochapter`:

```latex
\echapter{Introduction} % Outputs "1 Introduction"
...
\echapter{Theory} % Outputs "2 Theory"
...

\appendix
\echapter{Data} % Outputs "A Data"
```

It is not clear in the second case that "A Data" is an appendix. There are two solutions to this problem

1.  Use `\echapter` commands in document, but revert to `\chapter` in the appendix (after using `\appendix` command).

    This has the problem of the appendix layout and spacing being inconsistent with earlier headings created by `ecochapter`.
2.  Use '\eappendix' command for appendices.

    This has the advantage of being consistent with the document layout. It uses it's own numbering (A,B,...) so the use of `\appendix` beforehand is not needed.
