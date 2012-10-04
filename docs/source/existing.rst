======================================
Good news, it partially already exists
======================================

I had this idea while @pyconfr listening to Aymeric Augustin presenting
the pits in datetime

Debugging the developer's brain
*******************************

Date time handling whatever the langage is, reveals one of the biggest 
weakness in human brain: 
**not being able to see the difference between a position and an interval**

Of course datetimes are interval of time elapsed since an arbitrary origin. 

It is just the representations that are differents. 

Times and dates are full of caveats: 
- leaping hours in CEST;
- absolute vs local time;
- Time Zone;
- calendar time vs usual time (1 day duration, vs an event occuring the next day);
- and a lot of confusing stuffs ...

For dates implemented as seconds elapsed since 1970 in UTC you can figure 
that the unit of the date is seconds, and the duration is seconds. The only 
difference is the origin. 

Why did we need to abstract datetime so much that we had to introduce the
datetime interval?

Because there is a bug in the perception in the brain of developers
*******************************************************************

I don't know where it is, I only know that datetime is sufficiently well
designed that it lowers the bugs in date handling. They achieve this by 
making believe that datetime and intervals are somewhat different and
raising exception when you try to add a date to a date and 
an interval to an interval. 

I just hate soft science, so I leave to pseudo scientific from a 
psychology/pedagogy department the care to develop this uninteresting part. 

But, I see these datetime problems not as a bug in computers but an awfull
big bug in education. It is probably located near the bug that causes the
the strings/bytes array/unicode/utf8 confusion.

If I tell you I am not sensitive to this bug, you know I lie. I am just 
a little less sensitive to this confusion than average. Still I sometimes too
make mistakes on this topic. 

Conclusion
**********

Since I think there is a bug in the concepts involved my answer will not be coding. 

It is first explaining why it is a fucking easy problem to solve! 

