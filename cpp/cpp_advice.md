Namespaces
==========

using namespace std
--------------------

    using namespace std;

This is usually a code smell, generally speaking the only time you would really want to do this
is when you are making some small throwaway program for testing a concept or making an example (or similar).
In that case the reduction in typing time actually has a positive ROI.
But you don't want to do it in any production code because this pollutes the global
namespace which is something you should try to avoid, any benefit from time saved typing is
immediately wiped out the first time your program breaks because a name conflict.
See [this StackOverflow question](http://stackoverflow.com/questions/1452721/why-is-using-namespace-std-considered-bad-practice) for more info on that.

If the main purpose for doing this is to cut down typing `std::` then you can
selectively bring in just the names you need by doing:

    using std::cout;
    using std::cin;

an so on. This cuts down on typing without the downside of polluting the global namespace.


Parameters
==========

Prefer pass by reference to const
---------------------------------

Say you have a function:

    foo(my_class_t bar){
        //function that doesn't change bar
    }

It's preferable to instead pass this parameter by reference to const like so:

    foo(my_class_t const& bar){
        //function that doesn't change bar
    }

There's 2 main reasons to do this:

  1. You no longer need to make a unnecessary copy of the `bar` for your function
  2. You more clearly state your intent with the code, any change to `bar` will now
     throw an error at compile time. This can prevent undesirable things from happening.


Constructors
============

Prefer initialization list
--------------------------

C++ beginners will sometimes write code like this that uses assignment to initialize members:

    struct point{
        float x, y;
        point(){
            x=0; y=0;
        }
        point(float aX, float aY){
            x = aX; y = aY;
        }
    };
    
However using the [member initializer list](http://en.cppreference.com/w/cpp/language/initializer_list)
is usually a better way of initializing variables with the constructor.

    struct point{
        float x, y;
        point():
            x(0),
            y(0)
        {
        }
        point(float aX, float aY):
            x(aX),
            y(aY)
        {
        }
    }; 

Doing it this way ensures that members get correctly initialized and this format can also
provide the compiler opportunities to optimize the code generated.
For the inbuilt default types `int`, `char`, etc. there is no performance difference but
for user defined types there can be.

See the [c++ FAQ entry](http://www.parashift.com/c++-faq/init-lists.html) for more on this topic.

Standard containers
===================

C-style arrays
--------------
Generally speaking with c++ you don't want to use raw arrays, the standard container
classes are safer and allow you to be more productive.
There's a [c++ FAQ article](http://www.parashift.com/c++-faq/arrays-are-evil.html) that deals with just this, so give that a read.

Random number generation
========================

`rand()` library function
---------------------------

`rand()` is a really bad random number generator, to the point where the standards committee
actually made a [report](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf) about depreciating it.
Additionally `rand()` [gets worse](http://www.lesinskis.com/code_repair_01_rand_problems.html#subtle-problems) when you take the modulus of it (statistically speaking).

We can avoid all these problems by just using the newer c++ [random number library](http://en.cppreference.com/w/cpp/numeric/random) in a manner like this:

    std::default_random_engine generator;
    generator.seed( time(0) );
    std::uniform_int_distribution<int> distribution(0,9);//note the min and max parameters are inclusive here
    while(true)
    {
        std::cout << distribution(generator) << std::endl;
    }

Demonstration here: http://ideone.com/xzgcZy
