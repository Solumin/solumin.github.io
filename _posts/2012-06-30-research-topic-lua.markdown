---
layout: post
title: "Research Topic: Lua"
date: 2012-06-30 20:10
comments: true
categories: 
---

I was considering continuing the "week in review" format for my posts, but I realized that isn't exactly feasible. Frankly, all of my weeks are going to look the same, bar the few interesting events that would deserve their own posts. Instead, I'm just going to do topic posts! Today I'm going to talk about part of my research: The Lua scripting language.

(Note: This is a pretty technical discussion (I think), but I've tried to balance it out by explaining things where I can. Leave a comment and I'll do my best to add needed information.)

<!-- more -->

#What is Lua?#

Lua is an embedded, extending, extensible scripting language. It was created by the Pontifical Catholic University of Rio de Janeiro in Brazil in 1993. In fact, a group called Lablua develops the language at PCU-Rio still! The name "Lua" means "moon" in Portuguese, by the way. It's not an acronym, so don't write "LUA"!

Lua's original purpose was to build basic tools for computer graphics. Since then, it has become an extremely popular tool in the video game industry. The first big game to use it was Grim Fandango, which all of you Double Fine fans should have heard of. Another big name---arguably the biggest---is World of Warcraft, which allows users to create plugins and other content for the game with Lua. The language is commonly used in games because it small, fast, powerful, and portable.

##Embedded##

An embedded language is generally  used in other programs to provide additional functionality. From the Programming in Lua book (1st ed.): "These applications use the Lua-C API to register new functions, to create new types, and to change the behavior of some language operations, configuring Lua for their specific domains." This, I think, is the crux of its usage in video games. A game engine, which provides the basic physics, object manipulation, graphics, etc. needed to actually run a game, is usually written in C because that language is very fast and allows low-level optimization. Those are the exact reasons that make C a pain to use when making the rest of the game! Enter Lua, which can easily integrate with the engine and abstract away those low-level features. It becomes just another function or tool to use. Obviously, other scripting languages could be embedded with the game engine. Lua has the advantage of working very well with C: Not only is it written entirely in ISO C, it has a very simple system or API that interfaces with C. Therefore, Lua is the simplest way to embed scripting in a program.

##Extending##

To be honest, using Lua to extend the power of an application is just another facet of embedding Lua. This focuses more on how the embedded language adds functions, types or behavior to its host program. This could be as simple as rewriting an old function to be cleaner, faster, or more understandable to adding new data types that better represent the data the program works with. Maybe it will be used to allow users to better control how the program works!

For example, say that you have a program that mines data for your company and prints out a report. Since you're a good programmer, you want to design the system so it's easy to configure the program to parse new kinds of data or add a new report format. If it was straight-up C, this would be annoying, difficult, and slow, and it would probably devolve into a mess of printf()s and scanf()s and structs and insanity. With Lua, it would as simple as defining a new configuration file or report template. The program would read these templates, parse them, and print properly-formatted reports. Writing a new configuration file could take only a few minutes! Such is the power of extending languages like Lua.

##Extensible##

This is the flip side of extending: Using other languages to add functionality to Lua. Like all computer languages, Lua has the ability to use modules and libraries to add new functions and types. These are often written in Lua itself, but can easily be written in C. (Other languages may be possible, but I haven't looked into it too much.) This allows yet another way to mix the speed and low-level power of C with the high-level abstractions of Lua. You might extend Lua with C for number-crunching functions, for example.

(Don't ask if you can extend Lua with C while embedding Lua in another C program. I think you would be missing the point if you tried that.)

##Scripting vs. Programming##

I have been known to refer to Lua as both a "scripting language" and a "programming language". Obviously, the former is used to create scripts while the latter is used for programs, but that doesn't answer the question in anything but the trivial sense. Let's ask a related questions: What's the difference between a script and a program? The joke goes that a script is what you give the actors and a program is what you give the audience. Humor aside, that does capture the kernel of the answer.

###Scripts###

Scripts are used to automate small, repetitive tasks. Need to manage your music library? A script can handle it. Need to format a spreadsheet? A script is your answer. Need to sacrifice a goat every new moon or your computer leaks blood and screams Satanic verses? A script could access a lunar clock, feed the goat, and sharpen the dagger. (A priest would also be helpful.) Essentially, scripts are tools that aid in maintaining systems.

The languages used to write scripts tend to be lightweight and interpreted. That is, instead of compiling into an executable file (i.e. a program), another program executes the instructions in the script file on the fly. This allows very rapid development, since you don't need to wait for the program to compile before testing it. Some scripting languages are also "domain specific languages" or DSLs. An example of a DSL is SQL, which is used to access, modify, and otherwise interact with databases. You can't use it for anything else. I don't even think it could function as a calculator! But give it a database and you're set. Use it in another program and you can easily store permanent data that can be used throughout the program. (Yes, SQL is another extending/embedded language!)

This is not to say that scripting languages are simple. Take, for example, Perl. Way back in the day, Perl was a text processing language--in fact, the name "Perl" has been backronymed to "Practical Extraction and Reporting Language". These days, it can be considered either a programming language or a scripting language, but because it is interpreted, I will continue to refer to it as a scripting language for my purposes.

Perl is not simple. I don't mean that in terms of its syntax, which <s>can be</s> *is* complex and archaic, but in terms of its modules and libraries. [CPAN](http://www.cpan.org/), a repository for user-made modules that extend Perl, hosts over 100,000 modules! These range from basic extensions for manipulating Excel spreadsheets to full-blown Object-Oriented Programming systems. Perl can be used for just about anything thanks to these modules.

###Programs###

Programs provide larger, more "important" services to users. (I say "important" because formatting a spreadsheet can be more important than surfing the Internet.) The largest difference may simply be a matter of scale. Scripts tend to do one thing and do it well, or maybe do a few small tasks to accomplish a larger goal. On the other hand, programs may focus on one huge task that has several smaller steps. Take a browser like Chrome, for example. Loading a simple web page involves parsing the URL, performing DNS look ups, fetching content, running embedded scripts, loading dynamic content, tracking cookies, rendering the actual web page--all so you can look at cat pictures! And that's not even talking about managing your bookmarks, extensions and settings, windows, tracking your web history so the "back" button works, encrypting your passwords to give you a bit of convenience, and so on. Programs handle complex activities and have to do it quickly. Programming languages have to meet these demands through fast execution times. The process of compiling allows optimization and faster execution at the price of slower development. Compiling a program turns the human-readable source code into machine code, which is the very low-level language that the computer actually uses when executing instructions. Since the computer is directly executing machine code, these compiled languages are usually much faster than interpreted languages. Some languages, like C and C++, have been around long enough that the tools used to compile them can optimize a program at compile time without human (or programmer) intervention. Programming languages are used to create complex, multi-function programs that offer a wide variety of services and tools for users.

It should be noted that not all programming languages are directly compiled, nor are all of them compiled in machine code for the computer to run. The Ruby and Python programming languages are good examples of the former case. Both have lots of built-in functions and data types that give them the breadth needed for systems programming, but they can also be interpreted for use as scripting languages. Java is an example of the latter case. Java code is compiled into byte code that is executed by a virtual machine, which basically a simulation of a computer. This virtual machine is why Java is touted as the most cross-platform of languages, since a new platform just needs the virtual machine in order to run any Java program. However, these languages are still fast and have the tools necessary to write broad programs.

So how does this all relate to the "scripts are for actors" comment? Consider how the actor's behavior on and off stage (during a performance) is influenced and dictated by the script. What the audience see is a performance on a stage with sets, costumes, music and ligts. What the actors see are the catwalks and ropes to control the scenery, the costume racks and changing rooms, the orchestra sweating in the pit, and people running around trying to make the show run as smoothly as possible--all dictated by the script. Scripting languages manipulate the behind-the-scenes actions in order to present to the user a smooth experience.
It could be argued that the "programs are for the audience" line also applies. After all, most users are not concerned with how a program works. They just want the public interface, which is the program for the play.

(I suppose it also works when discussing embedded languages. The program is all the user sees, while scripts are influencing the background activities.)

###Blurring the Lines###

One final word on "scripting" vs. "programming". Earlier I gave Java's virtual machine as an example of how programming languages can be compiled. How is it then that Lua also has a virtual machine? Yes, Lua code is compiled into byte code and executed on a small, 500-line register-based virtual machine! Is it still a scripting language? Well, yes. It's just a particularly powerful and interesting case, and the virtual machine probably sheds light on why Lua is a fast language.

Another comment regards how much of a difference compiling makes versus interpreting. I direct you to this graph from the [Great Programming Language Shootout](http://shootout.alioth.debian.org/u32/which-programming-languages-are-fastest.php?gpp=on&gcc=on&java=on&lua=on&cint=on&calc=chart). The graph shows four bars: C++, C, Java, Lua, and C INT. Below is a chart detailing the times. C and C++ are traditional compiled languages, Java is a byte code language, Lua is interpreted in byte code, and C INT is a version of C that is run through an interpreter. Looking at the chart, we see that (compiled) C is nearly the fastest language there with a median score of 1.36. (Each score is (execution time) / (fastest execution time)). The slowest time is (interpreted) C, with a median score of ***241.92***! Interpreted C code is 178 times slower than compiled C code. Lua, which is designed to be interpreted, is 8.5 times than C INT faster at its median score. So remember: Compiled vs. interpreted does not automatically make a language slow or fast.

Whew. 2000 words in and I have hardly talked about Lua! The above was supposed to address the bit about Lua being "embedded, extended and extensible." I suppose it's time to move on to "small, fast, powerful and portable."

#All About Lua#

First, I'm going to talk about the basic features of Lua--syntax, variable types, and standard libraries--before moving into "small, fast, powerful, and portable."

## Language Basics ##

Wikipedia describes Lua as a "lightweight multi-paradigm programming language designed as a scripting language." "Lightweight" means either minimalist syntax--few special operators, things like that--or a small memory footprint. Lua arguably leans toward the latter definition, though it does have a rather light syntax. For example, compound operators like "+=" are not present in Lua; instead, the full expression must be used ("a += b" becomes "a = a + b"). Another example of the lighter syntax is the lack of increment and decrement operators:

{% codeblock Basic Lua Syntax %}
a = 2
b = 3
c = a-- * b++
{% endcodeblock %}

In C, the variable c would have the value of 4: `c = (a - 1) * (b + 1) = 1 * 4 = 4`. In Lua, c would have the value of 2 because `--` indicates the start of a comment! The program would ignore everything after the `--`, so the line just says "c = a". (One of the first things to learn about any new language is its comments. In Lua, `--` marks a single-line comment. `--[[` marks the beginning of a block comment and `--]]` ends it. This incorporates a rather nifty feature: `---[[` nullifies the block comment by turning it into a line comment, so you can comment and uncomment whole blocks of code with a single keystroke!)

### Types and Typing ###

Lua has 8 basic built-in types: nil, Boolean, number, string, function, userdata, thread and table. "nil" is used to represent nothing. By that I mean it represents the absence of value. Boolean variables are either true or false; nil is also considered to be "false". Numbers are exactly what it says on the tin: real numbers! They're stored internally as double-precision floating point numbers in most implementations. (Floating-point numbers are a way for computers to store numbers with decimal points. That's a harder task that it may sound, to be honest.) Strings are sequences of characters, like "Hello". There is no single-character type like in C or Java, so 'a' and "a" are equivalent. These are the four most basic types. Function, userdata, thread and table are more complex and, therefore, more interesting.

Variables of type function represent callable blocks of code to which arguments can be passed to achieve a form of modular execution. To be less of a twit, you can store functions as variables. This is a feature called "first-class functions" and lets you do many interesting things. This data type is part of why Lua is called "multi-paradigm." The paradigms in this case are the different programming styles, such as object-oriented or imperative. Object-oriented programming (OOP) refers to representing real-world things in code. For example, you could describe a Car class as a thing with wheels, an engine, and a way to steer. Imperative programming is simply giving a list of instructions to the computer to execute. Some languages are designed with a particular paradigm in mind; for example, Java is rather heavily object oriented, while C is imperative. Multi-paradigm means that a programming language can be used to write a program in different ways using different paradigms. Lua's first-class functions can be passed as arguments to other functions, which is a core part of the Functional Programming paradigm. They can be used in other applications, of course, and are immensely useful for a lot of things.

Userdata is a rather interesting type. It's basically just a chunk of memory that the programmer defines. It's a way of having arbitrary data when using Lua with C. I don't use it much, but userdata is useful when embedding or mixing Lua and C.

Thread is another advanced type. They're involved with coroutines. If that means something to you, good! They aren't like operating system threads, since they can be used on any platform. Threads are more advanced than I would like to cover in this post, and frankly I've never used them before. I'll end this with a quote from the Lua 5.2 Reference Manual: "Lua supports coroutines, also called collaborative multithreading. A coroutine in Lua represents an independent thread of execution. Unlike threads in multithread systems, however, a coroutine only suspends its execution by explicitly calling a yield function." If that sounds interesting to you, check out the [Reference Manual](http://www.lua.org/manual/5.2/manual.html#2.6).

The final basic type is the table type. Tables are the most important and most interesting thing in Lua. Tables are what make Lua stand out as a language. Tables are what make programming in Lua fun and interesting. I love tables. They're so cool.

Tables are the data structure of Lua. To quote the Reference Manual again, tables "can be used to represent ordinary arrays, sequences, symbol tables, sets, records, graphs, trees, etc." Included in that "etc." are things like hashes, dictionaries, and classes. Tables are all-powerful.

You can use normal array indexing to access and store elements in tables, such as `arr[1] = 12`, for example. (Table indices start at 1 instead of 0, by the way.) You can actually use any of the data types as a key, such as functions or other tables. For example, you can do `hash["key"] = value`, which Lua lets you write as `hash.key = value`. Values can also be any type; `commands["help"] = showHelp` (where showHelp is a function) is perfectly valid.

One of my favorite pieces of Lua syntax is how you count the number of elements in an array. Actually, let me pull together an example:

``` lua Table of Squares
squares = {} --create a new table
squares[1] = 1 --assign 1 to the first index
squares.name = "squares" --create the key "name" and assign the value "squares"

function squares:add(x) --create a function to add more values
	self[x] = x*x
end

print(squares[2]) --prints "nil"
squares:add(2) --adds squares[2] = 4
print(squares[2]) --prints 4
print(squares.name) --prints "squares"
print(#squares) --prints 2
```

Note that last line. The `#` operator returns the number of consecutive entries in the table starting at 1. Since we defined `squares[1]` and `squares[2]`, the result is 2. If we hadn't added a value at index 1 (through either `squares[1] = 1` or `squares:add[1]`), then the result would be 0. Any numeric indices less than or equal to 0 are also ignored in the count. Also note the function definition and the function call, where we used `squares:add`. The colon syntax automatically adds "self" as an argument to the function. If we had called `squares.add(2)` (sans colon) then '2' would be passed to the function as the first argument and 'x' would be nil, which would cause an error. It's a useful piece of syntactic sugar that makes implementing functions with tables that much easier.

### Dynamic Typing ###

Lua is a dynamically typed language. That means a variable could start off as a number, then become a string, and then end up as a table, and the interpreter would never complain. However, if you actually do that, you're an idiot and should not be programming. Obviously, there are going to be times when you want to know what type a variable is. Lua has a built in function simply called `type()` that returns a string describing the argument's type. For example, `type(5)` will return the string "number". `type()` is especially useful for "overloading" functions. Let's take our squares example from earlier and modify it a bit.

``` lua Table of Squares 2
squares = {} --create a new table

function squares:add(x)
	if type(x) == "number" then
		self[x] = x*x
	elseif type(x) == "table" then
		for _, v in ipairs(x) do
			self[x] = x*x
		end
	end
end

arr = {1,2,3}
squares:add(arr)
squares:add(4)

print(squares[2]) 	-- Prints '4'
print(squares[4]) 	-- Prints '16'
print(#squares)		-- Prints '4'
```
(Bonus: What's an easy way to improve the new squares:add function?)

The squares table can now add both arrays and numbers! This example actually shows a number of interesting things, such as the syntax for if statements and for loops, plus the venerable ipairs function and the "_, v" convention. Right now, those things are unimportant. I'm going to stop talking about Lua syntax and more about the structure of the language itself now. If you want to learn more, the [Lua 5.2 Reference Manual](http://www.lua.org/manual/5.2/contents.html#contents) is useful, though the [Programming in Lua](http://www.lua.org/pil/#1ed) book may be more helpful. (Do note that freely available PiL is mildly out of date, as it references version 5.0 while Lua is on version 5.2.)

### Standard Libraries ###

Lua comes equipped with 10 standard libraries, each one is available in the C API, too. [Section 6](http://www.lua.org/manual/5.2/manual.html#6) of the Lua Reference Manual discusses these a little more in depth.

**Basic Library**: This is the "catch-all" core library. It provides things like error handling, manipulating the garbage collector, basic output, type checking and conversion, etc. These are the really basic functions that almost all scripts may use.

**Coroutine Library**: Create, manipulate, use, and close coroutines. What more needs to be said?

**Package Library**: This library is used to load modules. Modules, of course, are things like third-party libraries or your own code that adds functionality. The package library provides one function that is absolutely necessary: `require`, which loads in a module. Fortunately, you don't need to use the rest of this library to load packages.

**String Library**: This is the library that provides the string manipulation functions. It has functions for finding substrings or patterns, formatting strings (similar to the *printf functions in C), converting characters to bytes and back again, etc. It's very useful for any application that uses strings, which is most of them.

**Table Library**: The library for adding, removing, sorting, concatenating, and otherwise mangling tables. These are mostly useful for when you're using tables as arrays.

**Mathematical Library**: Here's your repository for trig functions, logs, and other advanced math. You can't do everything with addition and subtraction!

**Bitwise Library**: As previously mentioned, Lua has a minimalistic syntax. The bitwise operators (like `&` or `|`) common to C are not directly useable in Lua. Instead, this nice library has them as functions for you. It provides more than just the basic and/or/not/shift operations, too, such as the "replace" function that replaces a range of bits with a specific value. This library, I imagine, isn't used to much for common scripting applications.

**I/O Library**: The library for advanced I/O. While the basic library has the ever-useful `print` statement for printing to standard out, the I/O Library provides functions for reading and writing input using files and streams. One interesting feature is the ability to read lines of input at a time. It also provides temporary files!

**OS Library**: Sometimes (ok, a lot of the time) you need to talk to the underlying operating system of whatever computer you're using. This library has you covered. It's useful for date and time functions or removing files. You can even use it to execute shell commands.

**Debug Library**: Like coroutines and threads, this is a feature of Lua that I haven't touched. Why? Well, it's scary, complex, and occasionally dangerous. The Debug Library lets you check out the guts of your Lua script. Use it at your own risk.

## Size ##

There are three components to a Lua distribution: The library, the compiler, and the interpreter. The library is the core, where the language is actually implemented. There are approximately 60 files that make up the library. They can be split into two groups: the base and the standard libraries. The base files are the ones that define things like the garbage collector, the virtual machine, and even the basic types. The standard libraries implement the features mentioned in the Standard Libraries section. Together, these two groups implement the full Lua language.

The interpreter uses the Lua library to implement the register-based VM and interactive REPL environment. The interpreter is the primary means for scripting with Lua, as it is used to execute the Lua code. Each script is read in, compiled to the machine code used by the VM, then executed. The REPL (**R**ead **E**valuate **P**rint **L**oop) is used for interactive development. It's the default behavior if you run the interpreter without a script to run. The name really gives it away: The programmer writes a line of Lua code, which is **read** by the interpreter, executed (or **evaluated**, as you are finding out the result of the line of code), and the result is **printed** so the programmer can see what happened or what went went wrong. This whole process is repeated in an infinite **loop** until the programmer is satisfied. This allows the programmer to test snippets of code or write basic proof-of-concepts that can be incorporated into larger scripts.

The compiler also uses the Lua library. Its function is a little more specialized than that of the interpreter, however. The compiler takes a Lua script and converts it to the machine code (called byte code) that the Lua virtual machine uses. (This is the same as the second step that the interpreter performs when executing a scripts, by the way.) Why do this, if Lua is an interpreted language? Well, it gives slight performance boosts when loading (NOT executing) code, it protects the source from user changes (if, say, the application isn't open source), helps perform thorough syntax checks, and can even analyze a file to ensure that it will not break the interpreter. (Due to the halting problem, it can't actually test if the program does anything sensible, of course.) It basically gives a little more streamlining and insurance to the development process.

After seeing the syntax and all the features I've mentioned, you may be wondering how large this "full implementation" is. [Let's enumerate some numbers](http://www.lua.org/about.html):

- Around 20,000 lines of C
- 960 kB of source code (compresses down to 245 kB)
- The fully-compiled interpreter is 182 kB
- The Lua library is 243 kB

These numbers are for a standard distribution (built in Linux) with all the standard libraries included. So realistically, things can only get smaller as you customize the build for your own needs. (luac, the compiler, is much larger. It isn't a necessary part of the implementation or execution process, so its size is of no concern to us.) So what do these numbers mean? **Lua is tiny.**  (If you want, I'll find the numbers for the Ruby and Python libraries so we can compare them further. I'm writing this on Windows at the moment, so my numbers are out-of-date and possibly non-standard. But for now, take my word for it that they are large.)

## Speed ##

The only easy method to measure a programming language's execution speed is to run benchmarks. Fortunately, we have the [ "Great Language Shootout"](http://shootout.alioth.debian.org/) (also known as "The Computer Language Benchmarks Game) to standardize the benchmarks. [This page](http://shootout.alioth.debian.org/u64/lua.php) gives an interactive view of how Lua compares against various languages for various benchmarks on a 64-bit single-core Intel computer running Ubuntu. Comparing several of the languages against Lua illuminates some interesting data:

- Lua often uses less memory, requires less code, and executes in less time than other scripting languages like Python, Ruby, and Perl.
- Lua still uses less memory and less code when compared to programming languages like Java, C++, and Go.
- It even performs well against functional languages like Haskell, Lisp, and Racket

Remember, too, that these are math-heavy scientific benchmarks and may not reliably capture how a language performs in its natural environment. The low development time associated with Lua should also be factored in, especially when considering writing scripts. Either way, we can see that Lua is not only fast, but also uses less resources and requires less code than other computer languages.

## Power ##

Like speed, power is difficult to quantify. We could investigate, perhaps, how *expressive* a language is, or how much one line of code actually says. We could look at the built-in features or compare how easy it may be to implement a particular idea. But do any of these things really explain the "power" of a particular language? I'd say no, not really. They might give us an idea how easy is it to use a language, or how quick one can learn it, or other advantages it may give while developing software, but don't say much about the actual power of a language.

What about more specific metrics, like what we see when actually using the language? We could compare the number of lines of code, but different *individual* programming styles--just two different people, with two different ways they like their curly braces--would be different for even the same language, and different syntaxes would give different results. We could consider the number of characters in a program, but then some languages, such as Perl, have built-in shortcuts and abbreviations that make this metric untrustworthy. What about the number of classes used in a program? That's just silly: Not all languages use classes!

Different langauges, with different paradigms, syntaxes, grammars and philosophies make these sort of comparisons difficult. Maybe we could make some kind of chimeric test that combines all these different metrics. That would be difficult and probably useless in the long run. So how can we quantify the power of a language?

Here's one way that I think helps: How much does the language do for you? Do you have to worry about memory management? Do you have to manage the minutest details of your program? Do you have to constantly be mindful of pit traps and gotchas that arise from the language itself? Does development ever feel like a Sisyphean struggle that will only end when one of you is lying bleeding in the dust of the computer lab's decades-old carpet? Is anything *easy?*

Mondern scripting langauges like Ruby, Python and Lua are much friendlier than, say, C. Ruby and Lua especially stand out for their metaprogramming methods, which let the language handle some of the nitty gritty details. Lua's aforementioned garbage collector will completely handle all memory management for you. You don't even need to *look* at pointers, for crying out loud!

"But," some of you may be saying, "your metric leaves out languages that are obviously powerful, like C! You can't deny their power!" And you're right! C is absolutely a powerful language, but it's not nice and definitely will leave you bleeding on the floor, laughing at you while your blood mingles with the crushed hopes and Mountain Dew spills that stain the carpet. But, in the case of C, that's where the power comes from. You're in absolute control of the system, to the point where you can control the very registers of the processor itself. (And people call it a high-level language still!) It's just also easy to shoot yourself in the foot and take your whole leg off.

So what does that tell us? **Programming Language Power is a multi-dimensional heuristic.** "Niceness" is one axis. "Control" may be another. Syntax and grammar have to count for something, too. After all, languages like Brainfuck are Turing-complete (and therefore able to compute any algorithm or execute any program) but are as expressive and powerful as a catatonic pet rock on the bottom of the ocean. Ruby is more powerful than C++, thanks to a tighter OOP scheme, metaprogramming, and lots of built-in methods for its many built-in data types. C is more powerful than Assembly because it abstracts away some of the truly low-level features, allows logical ordering of a program, hides the implementation from the user, and generally allows for the revered programming best practices. There are many good and powerful languages out there. Don't get caught up saying, "This one, right here, is the best of them all!"

Anyway, what I was trying to get at was that Lua provides plenty of tools, such as the standard libraries and those wonderful built-in tables, to count as a powerful language. Sure, it may not be the best choice for everything, but I find myself using it for many projects in many different fields. It's nice, it abstracts away the low level stuff, and it has metaprogramming. It's powerful.

(Metaprogramming, incidentally, should be the subject of another blog post. I'm not qualified to write it as of now, but one day...)
Right. Where was I?

## Portability ##

I'll come right out and say it: Lua is very portable. First of all, the actual implementation of it is written entirely in ISO C. That means any system with a full implementation of C can build and use Lua. Furthermore, it's a clean subset, so you can actually build Lua in C++ and have it still work with C or C++. Since most operating systems are written in C, Lua is pretty much usable on any system.

Second of all, Lua is OS independent. It doesn't rely on any special operating system features (or "features") to implement the full language. Sure, there are some things that can be optimized or implemented in different ways depending on the OS, but there are always default implementations for those features.

Finally, Lua is highly configurable. There's a single header file called luaconf.h that contains definition after definition of standard Lua features. Don't like one? Redefine it! Some of them are specifically designated to be customized. For example, the default type for numbers in Lua is double-precision floating point, or just '`double`', as I mentioned in the "Types and Typing" section. You can configure those to be regular floats or even just plain integers. This is useful if, for example, your computer can't do floating-point operations, which is the situation for my research with XINU. These changes are well laid-out and commented, so it's very easy to change what you need to make Lua fit your needs.

To quote the [Lua about page](http://www.lua.org/about.html), "Lua runs on all flavors of Unix, Windows, mobile devices (running Android, iOS, BREW, Symbian, Windows Phone), embedded microprocessors (such as ARM and Rabbit, for applications like Lego MindStorms), IBM mainframes, etc." My research relies on this portability, as I am creating an implementation of the language for the Embedded XINU operating system on a MIPS architecture. Lua is truly a portable language.

# Closing Thoughts #

So, there you have it: A semi-coherent explanation of what makes Lua so great. I hope you understand now just what embedded and extending languages do, and why Lua is such as great example of that type of language. It's useful in scripts, it's useful for [games!](https://love2d.org/) When I use Lua, it goes right to my brain.

Bad rhymes aside, I hope you consider using Lua for your next big project, or your next little script, or if you find yourself forgetting to sacrifice that goat, or if you're finally fed up with C bullying you. There are a lot of great resources to help you get started, and I promise that it will be a fun and interesting journey. If you have any questions about Lua, scripting, or any other topic I covered, please comment and I will try to respond!