===========================================
What is a symmetry and why does it matters?
===========================================

.. quote::
    The teacher shows the figure, and the student look at the figure, what an idiot!

The point is you should never believe a teacher :) 

The question asked by symmetry is: given a peculiar way of moving in space constricted by
geometrical operations, if I do operation A then operation B on a given place (topos) then
will the result be the same?


Ex: if I take a sphere in Euclidian geometry and then rotate it by its center of an angle alpha
will the new topos map the other one? 

Yes, then a sphere accetps a symmetry of a rotation of any angle in any direction.

Is it true? 

Well, let's imagine I have a 2D clock in a 2D space. Now I do a mirror symmetry on any diameter, 
the mirrored clock seems to be the same? Let's watch the clock ticking. Buh it is ticking backwards.

Just also try saying that an aquarium opened on one the top can be rotated of 1 quarter towards the ground :)

The first example works only because another implicit symmetry is added, the place of the points don't matter.
It is a permutation symmetry. 

However let's get back to business. So let me assert my own definition of symmetry. 

.. note:: 
    A figure is invariant by its symmetries if it overlaps itself fully given any application of
    any 2 symmetries in any given order. 

    There can be no less of 2 symmetries on a system.
    
    A complete set of symmetries on a problem is called a base. 

    There are as much symmetries in a system there are degrees of liberty.

    The measure of symmetries is called a commutator denoted [ ] 
    Saying that A and B commute is the same as saying
    
    -  [ A, B] = 0
    - or A(B(topos))=B(A(topos))
    - measure of symmetry is [ A, B] = partial(A,B) - partial(B,A)
    
    A and B operates on place, and [A, B] is also an operator.

    A singularity is a place S such as you always have [A,B](S)=S

Hey lad, you are nice, but why should I care of symmetry in computer science?
=============================================================================

Saying that a place Ta is symmetric to a place Tb is the same as saying they are 
to deduce Ta from Tb. 








