+++
title = "Dc"
description = ""
date = 2014-11-21T15:08:23Z
aliases = []
[extra]
id = 3232
[taxonomies]
categories = []
tags = []
+++

{{language
|exec=interpreted
|checking=dynamic
|hopl id=1957
}}
{{language programming paradigm|concatenative}}
[[Category:Utility]]

[[wp:dc (computer program)|dc]] is the unix '''d'''esktop '''c'''alculator.

It uses a reverse polish notation and is turing complete.

;See also
* [[:Category:Bc|bc]] - '''b'''asic '''c'''alculator


== Quick reference ==
Commands in [[AT&T dc]]
 number      : push a number (0-9A-F digits, _ negative, . radix point)
 [...]       : push a string
 + - * / % ^ : arithmetic operations: add sub mul div mod pow
 v           : square root
 c           : clear stack
 d           : duplicate top of the stack
 f           : show stack
 p           : print value with a newline, leave it on the stack
 P           : print string, or print number as ASCII string
 sx          : store to register x
 lx          : load from register x
 Sx          : push to register x
 Lx          : pop register x
 1 2 :x      : store x[2] = 1 (x is register)
 2 ;x        : retrieve x[2]
 <x >x =x    : compare top 2 values: if true, then execute register x
 !>x !<x !=x :   (example: 5 2 <A executes register A if 2 < 5)
 !           : shell command
 q           : quit, or break 2 execution levels
 3 Q         : break 3 execution levels
 i           : set input radix from top of stack
 I           : get current input base, push it on stack
 o           : set output radix from top of stack
 O           : get current output base, push it on stack
 k           : set scale factor
 K           : get current scale factor
 x           : execute a string of dc commands
 X           : count decimal digits after decimal point
 z           : count elements on the stack
 Z           : count all decimal digits in number, or characters in string
 ?           : read and execute one line of input
 Y           : debug information

Extensions in both [[GNU dc]] and [[OpenBSD dc]]
 a           : print ASCII character
 n           : print value without a newline
 ~           : divmod: division and remainder
 r           : reverse (swap) the top two elements
 #           : comment

Extension in [[GNU dc]]
 |           : arithmetic - modular exponentiation

Extensions in [[OpenBSD dc]]
 3 J         : break 3 execution levels, then jump to next M
 M           : mark for the J command
 R           : pop and discard top of the stack
 <xey >xey   : comparisons with an else branch: if true,
 =xey !<xey  :   then execute register x
 !>xey !=xey :   else execute register y
 1 2 G       : equality: push 1 if 2 == 1, else push 0
 1 2 (       : less than: push 1 if 2 < 1, else push 0
 3 N         : boolean not: push 1 if 3 == 0, else push 0
