+++
title = "Sparkling"
description = ""
date = 2015-03-22T05:28:53Z
aliases = []
[extra]
id = 16915
[taxonomies]
categories = []
tags = []
+++

{{stub}}{{language}}

Sparkling is an embeddable, extensible, dynamically and strictly typed, C-like scripting language. Created by Árpád Goretity (a. k. a. H2CO3) in late 2013, the aim of the language is to provide an easy-to-use, easy-to-embed, portable scripting engine suited for various purposes.

== Design and heritage ==

The design, syntax and semantics of Sparkling have been influenced by several popular languages, such as C, Python, Lua and JavaScript (the latter being mostly negatively credited). This implies that parts of the language have a lot in common with these technologies. For example, its syntax should be familiar for someone having coded in C or JavaScript, the strict but dynamic type system resembles that of Python, and the "drop-in" library nature of the implementation was admittedly inspired by Lua.

Quite a few design decisions oppose the architecture of the aforementioned languages, though. For example, in contrast with most popular scripting languages, Sparkling has two numeric types. It operates not only on floating-point numbers, but on integers as well. Operations involving both floating-point and integral operands have well-defined semantics, similar to that in C.

Another rarely seen feature is the obligation to declare each local variable used, and the lack of (implied) global variables. All local variables must be declared before they can be referred to (read or written). Undeclared names are assumed to be globals (for practical reasons, i. e. because of the lack of header files), although global objects cannot be modified (they are always constants). The goal of this behavior is to minimize programmer errors and bugs arising out of forgotten declarations and interfering globals.

== The reference implementation ==

The reference implementation is written in portable C89: "portable" in the sense that it tries to follow the ANSI C International Standard (C89) as strictly as possible. It does not mean, however, that the entire source is compatible with C++. The public API can be used from within a C++ program, though.

Another aspect of portableness or platform-independence is that the Sparkling engine tries to make use of a bunch of convenient libraries in order to improve user experience. For instance, the REPL optionally uses the well-known readline library - if available - in order to provide basic line editing capabilities. Or, on OS X and iOS, the parser and runtime support library conditionally provide Objective-C bindings, so it's possible to call Objective-C methods directly from Sparkling, with proper Objective-C syntax. Neither of these features are required, though, nor do they impose a strong dependency on either libreadline or libobjc. The build system tries to guess if they are available and configures compilation accordingly.

The reference implementation is currently hosted on GitHub, at H2CO3/Sparkling[http://github.com/H2CO3/Sparkling].

== Syntax and semantics ==

Sparkling borrows most of its syntax from C and a tiny bit from JavaScript. Semantics also follow a - hopefully -  "intuitive" or "expected" convention, so that they're easier to grasp, especially for someone who has programmed before in C, C++, JavaScript or a similar language.

The basic "Hello world" program looks like:


```sparkling
print("Hello world!");
```


A somewhat more complex (unnecessarily complex for this purpose) version demonstrates some more language elements:


```sparkling
extern helloWorldString = "Hello, world!";

let printMessage = fn (msg) {
    let numCharsWritten = printf("%s\n", msg);
    stdout.printf("%d characters written\n", numCharsWritten);
};

printMessage(helloWorldString);

return 0;
```


The output of this program is:


```txt

$ spn hello.spn
Hello, world!
14 characters written
$

```



###  Fundamental language features



### = Types =

Sparkling is a dynamically but strictly typed language. Typically, binary operators operate on values of the same type only, which is enforced by runtime checks. Standard library functions type-check their arguments as well. There are 7 types in the language:
* Nil ("nil"): the empty value. It has only one possible value: <tt>nil</tt>. It indicates the absence of any other meaningful value. It is the result of array indexing by a key that is not found, the return value of functions that don't return anything explicitly, the default initial value of local variables, and the value of missing function arguments.
* Boolean ("bool"): Sparkling has a proper Boolean (true/false) type. Conditions of the if statement and loops and logical operators require their condition to evaluate to a Boolean value (otherwise, a runtime error is raised -- there are no implicit conversions to Booleans).
* Number ("number"): either a signed integer (C's <tt>long</tt> type) or a double-precision floating-point number. The only type of implicit conversion in the language is between integers and floating-point numbers (if an arithmetic operator has an integer and a floating-point operand, it will treat both values as floating-point and it will produce a floating-point result as well.)
* String ("string"): a sequence of bytes, which is not necessarily a human-readable string (it can contain arbitrary binary data). When exposed through the C API, a terminating 0 byte is always appended to the end of string. It does not count against the length of the string object, but it makes standard C functions to operate on Sparkling strings easily.
* Array ("array"): Simple integer-indexed array. Arrays are mutable. Arrays are bounds-checked (an out-of-bounds access causes a runtime error).
* Hash tables ("hashmap"): Mutable associative container. The type of its keys and values can be of any type, but indexing by <tt>nil</tt> or by the floating-point <tt>NaN</tt> value is not permitted.
* Function ("function"): in Sparkling, functions are first-class values. They can be passed to functions as arguments and returned by functions. There is a literal syntax for creating - possibly unnamed - function objects. Sparkling has lexical closures, so functions capture variables (by value) from outer scopes. All functions are variadic; it is not an error to call a function with more or less arguments than the number of arguments it is defined with.
* User information objects ("userinfo"): in order to facilitate the creation of third-party extension libraries, Sparkling has a "joker" data type, the user info. User info objects have two subtypes: weak and strong. Weak user info values hold an arbitrary, unmanaged, generic C pointer (<tt>void *</tt>), while strong user info objects contain a managed, reference-counted Sparkling object of an user-defined "class". (The Sparkling API makes it possible for users to define their own classes -- memory-intensive built-in objects like strings and arrays already use this mechanism for managing memory.)

Being a rudimentary feature of reflection, Sparkling supports querying the type of an object at runtime, using the <tt>typeof</tt> operator.


### = Variables =



### = Expressions =



### = Statements =




### = Functions =


A full language tutorial is available in the official documentation[https://github.com/H2CO3/Sparkling/blob/master/doc/tutorial.md].

== The standard library ==

Similarly to most modern languages, the Sparkling distribution comes with a bunch of utility and run-time support functions bundled in various "packages" of the Sparkling standard library. These packages can be loaded separately by the host program (i. e. the native environment that runs the Sparkling interpreter); in the default mode, however, all standard functions are loaded at the beginning of a Sparkling session (represented by an <tt>SpnContext</tt> object, from an API point of view). Library functions are not special in the sense that they are just normal native extension functions. There is one exception, though: standard library functions assume the use of the context API, and as such, they require their user info argument to point to a valid <tt>SpnContext</tt> object. This is done so that these functions can use the error reporting facilities of the virtual machine.

The currently available standard packages are:

* I/O routines (writing/reading to/from standard streams and files)
* String manipulation: searching for and creating substrings, creating formatted strings, etc.
* Array and associative array manipulation, including sorting, searching and functional-style list processing, such as <tt>map()</tt> and <tt>reduce()</tt>
* Floating-point, integral and complex mathematical functions
* Shell and environment access (including system date and time), and access to the Sparkling API itself (e. g. compiling to bytecode, stack traces, etc.)

== Implementation ==

Sparkling is an interpreted language, featuring a simple two-pass compiler and a register-based virtual machine. The compiler consists of a purely recursive descent parser and an almost naive (overwhelmingly non-optimizing) code generator, which directly generates bytecode for the VM. The compiler and the parser communicate using a right-leaning, binary abstract syntax tree (AST). The REPL also contains a disassembler which can convert bytecode into an assembly-like, human-readable textual representation.

Despite the fact that the reference implementation imposes an interpreted nature on the language, there are plans aiming to create a just-in-time (JIT) compiler back-end that produces native executable code (rather than bytecode targeting the VM). The implementation of the REPL also features a "compiler" option (-c), which converts Sparkling source files into bytecode files. The format of the bytecode is not portable, so such an "object file" runs only on the platform/architecture it has been compiled on. This is done like so for simplicity and performance reasons: for example, floating-point and integer constants are stored in the bytecode as they are represented in memory, so that there needn't be any - potentially expensive and/or inconvenient to implement - runtime conversions.

Although the primary goal of Sparkling is to be used as an extension language, there is a separate, stand-alone program that comes with the source as well. It contains an interactive interpreter (REPL, read-eval-print loop), a compiler and a disassembler.

== Performance ==

The reference implementation, being an interpreted language, doesn't have performance comparable to statically-typed, natively compiled or JITed languages. However, its speed is quite decent, and is mostly comparable to that of Lua, which is often considered the fastest interpreted scripting language available.

== Extensibility ==

Users can write and load native extension functions with the aid of the Sparkling C API. Extension functions must be written in C (or in C++ with external C linkage, or any language that supports C linkage and calling conventions), and they must follow a predefined signature, which makes it possible for the Sparkling virtual machine to call such a function. The signature of a native extension function is the following:


```C
int native_ext_fn(SpnValue *retVal, int argc, SpnValue *argv, void *context);
```


Function arguments are passed in an array of Sparkling value (<tt>SpnValue</tt>) objects, and the return value of a function - as seen by a Sparkling script - should be moved into place using a pointer to another <tt>SpnValue</tt>. The (actual, integer) return value of the native function determines whether the virtual machine continues the execution of a program (zero) or raises a runtime exception (non-zero).

The use of compiled, platform-dependent, native dynamic libraries is a work in progress. It is desired that they be added to the library with support for conditional compilation, in the same way libreadline and libobjc is used by the engine. This would mean that on systems which support dynamic loading and expose a C API, users will be able to benefit from the use of pre-compiled libraries, meanwhile on platforms that do not support dynamic code loading, this feature would not impose an irresolvable dependency, so Sparkling could continue to run on those platforms as well, without the ability to load dynamic libraries.

== Debugging ==

Apart from the already mentioned disassembler, the virtual machine provides a basic stack tracing feature, which can be accessed using the C API and, through a standard library function called <tt>backtrace</tt>, from a Sparkling program itself. Efforts are being made to extend the bytecode format with basic debugging information (filename and line numbers). This would make it possible to integrate a native debugger into the REPL and expose a debugger API to the users of the library.
