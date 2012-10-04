===========================================
Precise and exacts results are not the same
===========================================

A precise result of π is *3.141592653589793*, an exact result is
*3.14 +- .005*, the truth is both these results are not safe for use (but I
keep the development for a later chapter).

Precision is impressive, but in the real world, no results are perfectly measured. 
An exact result is something that is safe to work with because it gives you a 
range of confidence. A precise result is a good enough result, but it may 
bit you later. 

If you have a value of π and you would check it in a programming language you
would not write::

    if pi == 3.141592653589793:
        print("yes this is pi")


but as with any floats you'd write::

    epsilon=10**-10
    if abs(pi - 3.1415926535) < epsilon:
        print("I am sufficiently close enough to pi")


Let's think of more concrete problems
=====================================

The «almost equal» a priori version
***********************************

Imagine you are a policeman searching a criminal or a marketer fitting
a profile. 
Your database is so large, and -humans changing their biometrics during life-
you know that your very nice 10 digit precision metrics are false. 

You already know that even though you have the good size, weigth, eye colour,
and other metrics, exact matches done with the equal operator will fail. 

What you desire is something like::
    
    profile=Human(
        # in IS units 
        sex= 42, # 
        size=2.1,
        weight=69.12343234,
        eye_color=rgb(00,200,20),
        ...
    )
    accetable_variation=Human(
        sex=0,
        size=-.1, # the criminal is more than 20 years old, (s)he cannot grow
        weigth= interval(+10, -20),
        eye_color=0.01,
        ...
    ).incertitude()


    for suspect in database:
        interval = abs(suspect - profile)
        if interval > accetable_variation:
            continue
        # abs is the norm for the complex so why not 
        # try to be consistent?
        distance = abs(interval)
        print( 
            "%f%% match %r found " % ( 
                100 * (1.0-( abs(distance)/abs(profile) )),
                profile
            )
        )
        
An alternate notation might be::
    
    for suspect in dabatabe
        if not suspect ~= profile given accetable_variation:
            # where ~= would be the almost equal operator
            # given would be a reserved key word
            continue
        print "%r is a %f far from profile" % ( 
            suspect,
            abs(suspect - profile)
        )


.. warning:: 
    yes I totally assume my devilish non sensical confusing choice of 
    ~= close to =~ that is regexp match operator in Perl.

    But it is far less horrible than my initial choice of [ ] operator
    for denoting the interval of confidence (now **given**). 

    And, yes I agree no people in their right mind would choose this notation.

    However, I already know I won't need this notation. But I do take
    the right to have fun.
    

Computer lie!
*************

Just ask a computer what he thinks of::
    >>> .1 * .1
    0.010000000000000002

Well, it is no big deal. As long a you don't chain operations, where errors 
will propagate. It is cool as long as your problem is not sensitive to initial
conditions. 

Just remember banking, trading, commercial fees are computed with this flaw. 

Sometimes you wish you have the exact results when a human being's life 
relies on it.


Conclusion
**********

As I know how to do it, and since it is possible I propose to think of an
almost equal operator
