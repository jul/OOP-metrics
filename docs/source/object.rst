=================================
Designing Metric Oriented Objects
=================================

Premisce
========

I make the following axioms:

- an object has properties;
- properties are axis;
- the purpose of object metrics is to know if another object is close to another one or;
- to know if an object is oriented in the same direction. 

Since an attribute itself is an object, we have to consider the most simple case:

An object made of type of base
==============================

Integers, float, complex
------------------------

The L1 Euclidian distance suffices from value to value. 

Let's see if we have the interval with orientation this way? 

Given a Point A and B with properties x,y,z can we easily find the Euclidean results?::
    >>> from archery.bow import Daikyu
    >>> class Point(Daikyu):
    >>>     def __abs__(self):
    >>>         # L2 distance
    >>>         return sum(map(lambda s:s*s,self.value()))**.5
