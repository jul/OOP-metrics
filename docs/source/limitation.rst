================================================
Known limitations, why it does not always works?
================================================

Imagine you have a speed and you add speed because you want to know
the speed of a bullet fired at **.5*c** in a space ship travelling at 
**.9*c**. 

What happens? 

Well, you have a problem by finding a speed greater than the speed of light
in a fixed referential. 

The big question is: **is the bug located in the composition of the vectors
or located in the norm?**.

We have a very fast answer::
    ### let's compose the speed and see
    >>> bullet.speed= .5 # expressed in ratio of c
    >>> spaceship.speed = .9 # expressed in ratio of c
    >>> spaceship.speed + bullet.speed
    Traceback (most recent call last):
      File "<input>", line 1, in <module>
      Exception: You really except speed greater than the speed of light?

The problem should be solved at composition level. We have left euclidian
geometry, and we know work in a space were transaltion of vector are bound 
by Lorentz transformation. 

So, the limitation is in the substraction/addition?
===================================================

Well not. 

Well, this example not as funny as measuring the distance at which you place
the army in case of a zombie invasion in a square city (looking like a matrix). 

Given a speed of 1 block per hour (zombies are slow), we want to where to post
our valiant anti-zombie task force. We want to be able to test if a given human
will be in zombie range in n hours. 

Given that I am lazy person, I only make a nice draw to illustrate the problem:

.. image:: ./figure.zombie.jpg

And I give the solution. In this case: you change **abs** for any given vector.

Instead of::
    >>> abs = lambda x,y: ( x**2 + y**2 ) ** .5

You write::
    >>> abs = lambda x,y:abs(x) + abs(y)

I am really speaking of zombies only?
=====================================

Well, no. 

If you push hard enough the precision of your computer, your reachable values
are discretized, thus, it is also how your 2D vector will look.

Have you noticed that the stuff I draw are circles. 

These are **squares**. 

Thus the value of **Pi** is changed (when a circle is a square there are odds that pi is not an irrational number anymore), so is the distance logic. 

Most time, you don't care. I guess only 1 out of 100 000 developers will 
be bitten by this problem in their whole life. 

So cool down, it is just an illustration of computers limitation.



