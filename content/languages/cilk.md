+++
title = "Cilk"
description = ""
date = 2011-03-02T02:55:31Z
aliases = []
[extra]
id = 9307
[taxonomies]
categories = []
tags = []
+++

{{wikipedia|Cilk}}

<!-- Contents of this box needs verifying! The box was copied from Category:C. -- Erik Siers, 1 March '11 -->
{{language|Cilk
|exec=machine
|site=http://supertech.csail.mit.edu/cilk/
|gc=no
|safety=unsafe
|parampass=both
|checking=static
|compat=nominative
|express=explicit
|strength=weak
|tags=cilk
|altsite=http://www.cilk.com/}}
[[derived from::C| ]]

'''Cilk''' (pronounced ''silk'') is a general-purpose programming language designed for multithreaded [[wp:parallel computing|parallel computing]].

The Cilk language has been developed since 1994 at the [[wp:Massachusetts Institute of Technology|MIT Laboratory for Computer Science]]. It is based on [[:Category:C|ANSI C]], with the addition of a handful of Cilk-specific keywords. When the Cilk keywords are removed from Cilk source code, the result is a valid C program, called the ''serial elision'' (or ''C elision'') of the full Cilk program. Cilk is a faithful extension of C and the serial elision of any Cilk program is always a valid serial implementation in C of the semantics of the parallel Cilk program.

==See also==
*[http://supertech.csail.mit.edu/cilk/ Cilk page at MIT]
*[[wp:Cilk|Cilk on Wikipedia]]
