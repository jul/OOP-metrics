===============================
All your bases are belong to us
===============================

A base is a set on uncorrelated dimensions. 

What are uncorrelated dimensions? 

We ain't doing SiFi so let's begin with the first question: 

What is an axis? 
================

An axis is a right a on which you have corrdinates. Every points on the axis
can be compared and have therefore a distance to the origin and between themselves.

Weired Axis: incomplete knowledge and order
-------------------------------------------

It may seems odd, but in computer all day's life, we have axis on which we
have no idea where to place our «points» but for which we can compute the distance. 

The best example that comes in mind are **strings**.

We can have two strings *s1* and *s2* which we cannot plot on axis, we can't always tell if *s1* is greater than *s2*, but we can tell the distance between *s1* and *s2*. 

How is it possible? 

if *s1* is a subset of *s2* we can say *s1 < s2* however if *len(s1) == len(s2)*
and s1 and s2 are made of  different characters we are stuck. That's were we use
`Levenshtein distance`_ 

So to sum up there exists problem for which in computer science we :

- cannot say where a point is located;
- cannot say the direction of a segment on to point of the axis;
- can measure the norm between two points on the axis. 

So given 3 strings A, B, C on the axis of the string we cannot say if *A > B > C*, **but** we can say if **|AB| > |AC| or |AC| > |BC|**

Of course, strings are not really points, they are sequences of points, they are
segments. But what I say, is given we want to measure the distance between two points: **we don't care it behaves just the same**. 

Well, let's call it **geometrical duck typing** : if you can get the absolute
distance between two entities of same type, we have far enough for the purpose 
of comparing. I hear some people jump off their chair: I have the norm, I don't
have the direction. 

Héhé... I know, but I don't need it. 


.. _`Levenshtein distance`: http://en.wikipedia.org/wiki/Levenshtein_distance

Are there any real infinite dimension spaces useful in real life out there? 
===========================================================================

Well, google is mastering the art of projection in multi-dimensional space, so
I dare say yes. 

Text indexation is a natural indefinite dimension problem
---------------------------------------------------------

On this one, I'll work on a simplified problem of the textual indexation geometry. 

What is Google's job:

- the world is full of documents;
- you want all documents relative to a word **Q**.

So in terms of geometry you say that there exist a relationship between a 
documents made of N words Wn to one word Q. Since Wn and Q are of the same type
we call this a projection. Since it can be more or less revelant, we see there
is a logic of measure. 

Why is the word counter problem the most used problem for parallelism (map/reduce)?
-----------------------------------------------------------------------------------

Well, since working on sequence of words might be too hard here is one of the way
people represent text: 

- you tokenize the text in plain string separated by their boundaries;
- you transform each words in its invariant natural form (go, gone, going becomes go(verb));
- you get rid of useless words (articles and maybe preposition);
- you count each invariant form. 

So you have built an incomplete vector of word. 
Each invariant form is a dimension;
Each count is a scalar aka a measure/distance/coordinate on the axis of the invariant form. 

Why is the vector incomplete? Unless you are a dictionnary you use less word in
your text than the whole available words in the language. 

Building the canonical text corresponding to the keyword Q
----------------------------------------------------------

This a secret of fabrication, but it usually begins with human beings tagging
various text the more accurately possible with keywords. Than afterwords, 
with a statisticall analysis, for each invariant form of a word, you'll decide
if the presence of the word is correlated to the keyword. 

Once you have the list of the Words, you know just do a frequential analysis,
and for a given keyword **Q** you have a canonical word counter of invariant form 
**Vq**.

**A keyword Q is now associated with an incomplete vector Vq pointing in a certain direction**


Searching the text the closest to your query
--------------------------------------------

For each **Vti** which represents the Vector of a text **t** expressed as a word counter of its invariant form, 
you:

- you normalize each **Vti**;
- you project each **Vti** on **Vq** with a classical dot product*;
- you give every results of the **Vti** that are the closest to **Vq** given a confidence margin. 

.. note:: **dot product on words**:
   pseudo code::
        let dot be zero
        let normV be zero
        let normQ be zero
        for each wordsi frequency Fv,Fq present in Vti and Vq: 
           multiply frequence of Fv and Fq
           add it to dot
        normV is absolute value of distance from 0 of Vti
        normQ is absolute value of distance from 0 of Vq

        return dot / (normV * normQ)


Now, since Vti and Vq are normalized you have
a scalar *Confidence* called **c** which varies
from 0 to 1 which says how much *Vti* is pointing
in direction *Vq*. It is called a cosine similarity. 

The dot product of Vq and Vti is in fact a projection of Vti on Vq.
If the text Vt triggers the keyword Vq then it means the vector
of the text (Vt) points in the same direction as Vq.

So Vq dot Vt is how much times Vt «speaks» of Vq. By dividing by the 
norm of Vt we make an homothetia that answers another question: if we Vq and Vt
were the same size, what is the ratio of **Vt** represents compared to **Vq**.

The magic in textual indexation is a 60 words can be as relevant as 6000 words
text. A definition of  *serendipity*  (60 words) is has meaningfull has a thesis
on serendipity. But a text of 10 000 words long having once the
keyword vector triggered is useless since S=-K.ln(Omega) you lose informations.



The problem with distance and measures, is that you can
use a lot of other metrics. For instance you can
weight the words with its presence in anything that 
semantically denotes a stress (title, emphasis, URL).

The norm is usually calculated with L2 = sqrt(Sum( (Xi)^2)). But is flawed.



