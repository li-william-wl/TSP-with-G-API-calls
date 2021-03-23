<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
	<meta http-equiv="content-type" content="text/html; charset=utf-8"/>
	<title></title>
	<meta name="generator" content="LibreOffice 6.4.6.2 (Linux)"/>
	<meta name="created" content="2021-03-23T00:44:26.376281327"/>
	<meta name="changed" content="2021-03-23T00:46:19.562900563"/>
</head>
<body lang="en-CA" dir="ltr"><p style="font-variant: normal; font-style: normal; font-weight: normal; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="background: transparent">With
the current state of the world, I try and do my part by staying home
and going out as little as possible. But there are still errands that
need to be run, and food eventually runs out.&nbsp; I try and stack
my errands on the same day, so that I’m not going through my
disposable masks as fast.&nbsp; So while I was out and driving
between my 7 locations for the day, being stuck in traffic offered me
an opportunity to think; is the current order I’m visiting
locations optimal? Was the path I picked minimizing the amount of
time I spent outside. Was it better to visit the out of the way bank
first and leave everything else together? Or try and incorporate the
bank into the middle of the route while I sweep east to west? What if
I incorporate traffic flow into my decision?&nbsp; How would one
determine the best and shortest path between all of these locations?</span></font></font></font></p>
<p align="center" style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; line-height: 138%; text-decoration: none">
<span style="display: inline-block; border: none; padding: 0cm"><span style="background: transparent"><font color="#000000"><img src="blogpost_html_a72ffb1d953ee363.png" name="Image1" align="bottom" width="358" height="359" border="0"/>
</span></span></font></p>
<p align="center" style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; font-style: normal; font-weight: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="1" style="font-size: 8pt"><span style="background: transparent">Ever
want to visit all the grocery stores in the area in one go, but not
sure what the best order is?</span></font></font></font></p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><span style="background: transparent">&nbsp;</span></font></p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; line-height: 138%">
<span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">Upon
reaching home, a quick google search reveals what I’m looking for.
Apparently, this problem is known as the </span></span></span></font></font></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">travelling</span></span></span></font></font></span></font></span><a href="https://en.wikipedia.org/wiki/Travelling_salesman_problem"><span style="font-variant: normal"><font color="#1155cc"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><u><span style="font-weight: normal"><span style="background: transparent">
salesman problem</span></span></u></span></font></font></span></font></span></a><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">.
The </span></span></span></font></font></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">travelling</span></span></span></font></font></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">
salesman problem is a problem about optimization and calculating the
best path. Suppose you have a list of locations you would like to
visit for the day, starting from your home and ending back at home.
You need to visit all of them, but the order does not matter.&nbsp;
Given a list of locations, it is easy to calculate the distance
between any two locations. That also means it is easy to calculate
the exact distance </span></span></span></font></font></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">travelled</span></span></span></font></font></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">
for a given order. But it is not so easy to calculate the best order
among all possible orders to visit; finding the one that minimizes
the distance. That means this problem is not solvable analytically,
and there is no formula we can insert numbers into to get the
solution.</span></span></span></font></font></span></font></span></p>
<p><br/>
<br/>

</p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; font-style: normal; font-weight: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="background: transparent">The
only way to figure out the best solution then, is to try all the
permutations possible and keep track of which one gives the best
results. Fortunately, this is a suitable task for computers, so I
quickly set about programming my version of the travelling salesman.
A list of n locations to visit will have roughly n! Permutation to go
through. I don’t plan to visit more than 10 locations in one day,
but this number can quickly blow up if n gets too large (10!
=3628800).</span></font></font></font></p>
<p><br/>
<br/>

</p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; line-height: 138%">
<span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">First
I need a list of locations, and their travel distance or time between
each locations. Thankfully </span></span></span></font></font></span></font></span><a href="https://developers.google.com/maps/documentation/places/web-service/overview"><span style="font-variant: normal"><font color="#1155cc"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><u><span style="font-weight: normal"><span style="background: transparent">Google
Places API</span></span></u></span></font></font></span></font></span></a><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><span style="background: transparent">
</span></span></font></span><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">provides
the tools I need.&nbsp;</span></span></span></font></font></span></font></span></p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; font-style: normal; font-weight: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="background: transparent">Google
also provides a distance/time between locations API. It’s easy
enough to calculate the flying distance between two locations given
their longitude and latitude, but given we need to drive along roads
and not take direct paths, using google to grab distance / time
locations will be useful. This allows us to populate our own distance
matrix&nbsp;</span></font></font></font></p>
<p><br/>
<br/>

</p>
<p align="center" style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; line-height: 138%; text-decoration: none">
<span style="display: inline-block; border: none; padding: 0cm"><span style="background: transparent"><font color="#000000"><img src="blogpost_html_8f52b2cba0fdab2a.png" name="Image2" align="bottom" width="223" height="97" border="0"/>
</span></span></font></p>
<p align="center" style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; font-style: normal; font-weight: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="1" style="font-size: 8pt"><span style="background: transparent">Example
Distance Matrix. It’s&nbsp; just a lookup table.</span></font></font></font></p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; font-style: normal; font-weight: normal; line-height: 138%; text-decoration: none">
<font color="#000000"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="background: transparent">Now
that we’ve made our distance matrix, it is simple enough to go
through as many permutations as possible, keeping track of the best
results. Going through all of them guarantees we will find a minimum.
But if it’s impossible to go through them all, we should take
certain shortcuts. For example, we should notice places close
together in location should be close together in our list. It makes
no sense to skip something close by just to drive across town, and
then come back for it. We should also take advantage that if we’ve
found a low ordered list, we should try swapping elements in this
list; we hope that 1 or 2 swap tends to change the total distance
less than many swaps, and maybe we can swap into a local min. ORTOOLs
provides a framework that takes these assumptions and more to try aid
in finding the best solutions. But thankfully, 10! Is not a large
number, and even my home computer can go through that list in a
reasonable amount of time</span></font></font></font></p>
<p><br/>
<br/>

</p>
<p align="center" style="margin-top: 0.42cm; margin-bottom: 0.42cm; font-variant: normal; line-height: 138%; text-decoration: none">
<span style="display: inline-block; border: none; padding: 0cm"><span style="background: transparent"><font color="#000000"><img src="blogpost_html_4995bafb34eef9a8.png" name="Image3" align="bottom" width="624" height="267" border="0"/>
</span></span></font></p>
<p><br/>
<br/>

</p>
<p style="margin-top: 0.42cm; margin-bottom: 0.42cm; line-height: 138%">
<span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">And
there we have it. I can go on my next errand run between different
shoppers, certain that I am spending as little time outside as
possible. Check out the full code </span></span></span></font></font></span></font></span><a href="https://github.com/li-william-wl/TSP-with-G-API-calls"><span style="font-variant: normal"><font color="#1155cc"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><u><span style="font-weight: normal"><span style="background: transparent">here</span></span></u></span></font></font></span></font></span></a><span style="font-variant: normal"><font color="#000000"><span style="text-decoration: none"><font face="Arial"><font size="2" style="font-size: 11pt"><span style="font-style: normal"><span style="font-weight: normal"><span style="background: transparent">.</span></span></span></font></font></span></font></span></p>
<p><br/>
<br/>
<br/>

</p>
</body>
</html>
