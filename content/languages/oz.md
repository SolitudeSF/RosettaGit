+++
title = "Oz"
description = ""
date = 2019-02-13T19:06:54Z
aliases = []
[extra]
id = 2769
[taxonomies]
categories = []
tags = []
+++

{{language|Oz
|site=https://mozart.github.io/
|checking=dynamic
|gc=yes
|LCT=yes
|strength=strong
|express=implicit
|safety=safe
|compat=structural
|parampass=reference}}Oz is a multi-[[:Category:Programming Paradigms|paradigm]] language that is designed for advanced, [[concurrent programming|concurrent]], networked, soft real-time, and reactive applications. Oz provides the salient features of [[object-oriented programming]] including state, abstract data types, objects, classes, and inheritance. It provides the salient features of [[functional programming]] including compositional syntax, first-class procedures/functions, and lexical scoping. It provides the salient features of logic programming and constraint programming including logic variables, constraints, disjunction constructs, and programmable search mechanisms. It allows users to dynamically create any number of sequential [[threads]]. The threads are dataflow threads in the sense that a thread executing an operation will suspend until all operands needed have a well-defined value.[[#Citation|[1]]]
{{language programming paradigm|Logic_Programming}}
{{language programming paradigm|functional}}
{{language programming paradigm|Object-oriented}}

The [[Mozart/Oz|Mozart]] Programming System is the primary implementation of Oz. It is released with an [[open source]] license by the Mozart Consortium. Mozart has been ported to different flavors of [[Unix]], FreeBSD, [[Linux]], [[Microsoft]] [[Windows]], and [[Mac OS X]].[[#Citation|[2]]]

==How to execute the examples on Rosetta Code==
All examples that start with <code>declare</code> can be used directly in the Emacs-based IDE, without a separate compilation step. Just copy the source code to the <code>Oz</code> buffer and select the menu item "Oz&rarr;Feed Buffer".

Some examples are functor definitions and must be compiled. The compiler is invoked with a command such as: <code>ozc -c filename.oz</code>, and then executed with the command, <code>ozengine filename.ozf</code>. This [https://stackoverflow.com/a/29207029/371304 Stack Overflow answer] shows an example of the boilerplate to transform code written for the Emacs IDE to code that can run directly on the Mozart VM.

==Citation==
#[https://mozart.github.io/mozart-v1/doc-1.4.0/tutorial/index.html Tutorial of Oz]
#[[wp:Oz_%28programming_language%29|Wikipedia:Oz (programming language)]]
