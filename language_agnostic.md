Language Agnostic advice
========================
There are a number of topics that are not specific to any particular programming language.



Excessive use of global state
---------------------------------
Keeping the scope of variable as short as possible is a good idea because it allows you to have
a lower complexity for your code.

Imagine how much more difficultt it would be to repair a flat tire on a car if every time you
had to do it you also had to check the motor and the gearbox.

Excessive use of global variables does essentially the same thing for your code, you
start having to look far away from the immediate code in order to figure out what is happening.
This added complexity makes debugging much harder and will start to cripple your productivity
when the size of the code grows.

A good general guideline is to write code without using any gloabal scope if that is possible.
Only introduce global state if you have no other choice. 
