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
