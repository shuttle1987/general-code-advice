Advice for beginners
====================
Getting started with programming is quite difficult because there is a *lot* to
learn but not a whole lot of structure.

This article contains some tips to help you get started.

Learn to effectively search the internet
----------------------------------------
For many beginner problems there is a lot of information available on the intenet
to help you learn.
Being able to efficiently find this information will greatly help you learn what you need to learn.

Get to know where your language documentation is and read it, most of the mainstream
languages have good documentation on the web.


Learn how to ask for help
-------------------------
Being able to effectively ask for help is an extremely important part of learning how to program.
With the rise of many online programming forums and QA sites, being able to ask for
help can be an extremely useful way to improve your programming abilities.

http://sscce.org/

There are many people who like to spend time helping other programmers out, however their
time is limited so more of their focus goes to the better questions.
So it is important to make it as easy for people to help you, increasing the quality of the
question you post will greatly help your chances of getting helped.
Here are some elements of a good question:

* Clearly state what language you are using and what version of the language and libraries.
* All the error output is included verbatim.
* There is enough code to show the problem but no more.
  * Include only the relevant code to the problem at hand.
* All the relevant code is in the question in a *text* form.
  * Good formatting will help you get more answers
  * Don't take screnshots as people will want to be able to copy the code and try
    to run/modify it with minimal effort.

Get familiar with automated feedback tools
------------------------------------------
Being able to get feedback on the code you are writing is a crucial piece of the
puzzle when it comes to learning how to code.
Many languages have various tools to help give you feedback on the quality of your code.
These tend to fall into 2 main categories:

1. The information you get from the compiler/interpreter
2. 3rd party tools

The information you recieve from the compiler/interpreter is usually very important.
Many of the compiled languages have options to emit warnings, learn what these mean
and learn to pay attention to what these messages are telling you.
Learn how to enable all compiler warnings, then treat those warnings seriously.
With C and C++ your program may compile but more often than not a compiler warning will
be indicating a bug.

Finding useful 3rd party code analysis tools can be very helpful.
I am particularly partial to static analysis tools, [there are many such tools in existence](http://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis).

Using these lint tools is *especially* beneficial for dyanmic languages because we do not
have the feedback from the compilation step to help us find bugs.
For Python there is pylint and for Javascript JSlint.

