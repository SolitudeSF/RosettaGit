+++
title = "PostScript"
description = ""
date = 2015-08-12T16:01:28Z
aliases = []
[extra]
id = 1920
[taxonomies]
categories = []
tags = []
+++

{{language|PostScript}}
'''PostScript''' is a concatenative dynamically typed language with abundant meta language facilities. It allows definition of new control structures at run time, allows reflection and reification of stack, scopes, and even continuations. With Display PostScript, the language even has facilities for multi-threaded execution. Since the language is based on stack, it is suitable for combinator based programming, and all the higher order combinators (initiated by joy language) is applicable in postscript. The language also allows a form of prototype based object orientated programming using dictionaries. See {{libheader|initlib}} for implementation of higher order combinators.

'''PostScript''' originated as a printer definition language invented by the founders of '''Adobe'''. The language was necessitated by the increasing demands of printing and rendering jobs on the computers of the 1970s. These tasks were therefore pushed to the printers themselves, with the result that printers now had chips and built in interpreters for PostScript. With the growth of printing complexity, some printers ended up having even more powerful processors than the master systems themselves.

Although now almost displaced by the '''Portable Document Format''' (PDF), also developed by Adobe, PostScript's USP lies in it's being a '''Turing complete''' language with support for the basic data types and fundamental structures and concepts of Computer Science. Many interpreters and viewers of PostScript are available, some even for free. Although primarily a language suited for 2D graphics, PostScript is complete as a language and able to handle normal computation tasks.

''(does "USP" mean "unique selling proposition"?)''

==See Also==
*[http://logand.com/sw/wps/index.html WPS - PostScript interpreter written in JavaScript.]
*[http://code.google.com/p/postcanvas/ postcanvas - Open-source PostScript interpreter written in JavaScript.]
*[http://pages.cs.wisc.edu/~ghost/ Ghostscript opensource postscript interpreter with a lot of extensions. ]
*[http://code.google.com/p/xpost/downloads/detail?name=monterey86.pdf Owen Densmore, Object-Oriented Programming in NeWS, describes the use of dictionaries for implementing single- and multiple-inheritance.]

{{Language programming paradigm|Concatenative}}
