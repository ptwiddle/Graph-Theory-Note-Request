---
layout: page
title: Graphs on Surfaces
permalink: /Surfaces/
---


This section is devoted to drawing graphs on surfaces; we will cover planar graphs and Kuratowski's algorithm, drawing graphs on other surfaces, and Euler's theorem and applications.  As an introduction, we begin with the [Three utilities problem](https://en.wikipedia.org/wiki/Three_utilities_problem) (which apparently none of you had seen before).


An Old Chestnut 
====

Alice, Bob and Carol, each have a house, and each want to connect themselves to the power plant, the sewer plant, and the gas plant by independent underground lines.  Is it possible to do it so that none of these lines cross over each other?

In class, I tried to draw a solution, and came up with a drawing very like the following, stolen from [this site about the problem](http://www.science4all.org/article/eulers-formula-and-the-utilities-problem/):

![Attempt at solving the three utilities problem](../The-Utilities-Problem-Bad-Solution.png)

However, this just shows one attempt at connecting them up fails; it seems very hard to prove that no such attempt could succeed, as there are lots of ways you could try to draw it.  However, later in this lecture we will show that it is impossible.  But first


A notational interlude:
-----

In the graph we are trying to draw in the Three Utilities Problem, we have two different types of vertices: the houses, and the utility factories.  The graph only has edges between vertices of one type and vertices of the other type.  Similar graphs occur frequently, and so we make the following definition:




We have typically viewed graphs as drawings in the plane, with the vertices as dots and the edges as lines between them.  Different choices of drawings of them same graph can look very different (as we saw with the Petersen graph).   One thing that is convenient is to have drawings where the edges never cross (we might wonder if the crossing is a vertex).  We are naturally then led to the following definition:


Definition
====

A graph is *planar* if it can be drawn in the plane ($$\mathbb{R}^2$$) so that none of the edges cross.



Definition
=====

A graph is *bipartite* if its vertices can $$V(\Gamma)$$ and can be separated into two sets, $$U$$ and $$W$$, so that any edge of goes between a vertex of $$U$$ and a vertex of $$W$$.  

The very first picture on the [wikipedia entry](https://en.wikipedia.org/wiki/Bipartite_graph) is the picture you should have in your head.


Example
====

The 4 cycle $$C_4$$ is bipartite, while the 3 or 5 cycles are not.


A special case is when every vertex of $$U$$ and is connected to every vertex of $$W$$ -- i.e., the graph has many edges as it can while still being simple and bipartite.  

Definition
=====

The complete bipartite graph $$K_{m,n}$$ has $$m+n$$ vertices, split into a set $$U$$ with $$m$$ vertices and $$W$$ with $$n$$ vertices.  For every $$u\in U$$ and $$w\in W, K_{m,n}$$ has exactly one edge.




Back to the puzzle: 
==

Returning back to the Utilities Problem, it should be fairly clear that it is equivalent to the following question: Is $$K_{3,3}$$ is planar?   Our next goal is to prove that it is not.


A tiny bit of topology
-----

Since we're trying to draw it in the plane, we are secretly starting to do a little bit of topology.  This is not a module on topology, and we will do as little as we can get away with, but it may help to highlight slightly where we use a little.  In particular, the main idea of the proof will use some form of the [Jordan Curve Theorem](https://en.wikipedia.org/wiki/Jordan_curve_theorem), which basically says that if we draw a simple closed curve (i.e., a circle) in the plane, it cuts it into two pieces, an inside and an outside.  This certainly sounds intuitively obvious, and would go without question to anyone besides a mathematician -- think about some of the nasty curves you encountered in Analysis!  


Main idea of the proof
===

The problem with trying to show a graph is nonplanar is that it seems at first glance that there are tons of possible ways to try to draw it in the plane, and so the proof would have a huge number of different cases, and it would be tricky to make sure you'd covered them all.  The main idea of the proof is to use the Jordan curve theorem as a way to eliminate a lot of cases and organize the remaining ones.  This idea is widely applicable, and in previous versions of the course was referred to as the "planarity algorithm", although we will not formalise it to the level of an algorithm.

The idea is the following: suppose that a graph $$\Gamma$$ was planar, and consider some closed walk $$W$$ in $$\Gamma$$ that doesn't repeat any vertices.  Then if we draw $$\Gamma$$ in the plane, then $$W$$ will be a circle, and so by the Jordan curve theorem every vertex or edge not in $$W$$ must either be on the inside or outisde of $$W$$.  One can then do a case-by-case analysis placing each vertex or edge inside or outside.  

Obviously, the fewer vertices and edges that aren't contained in $$W$$, the fewer cases our proof will have, and so in the best case )and the only ones we will consider) we take $$W$$ to be a Hamiltonian cycle.  


Proof that $$K_{3,3}$$ isn't Planar
====

Let the vertices $$a,b,c$$ be coloured red and vertices $$x,y,z$$ be coloured blue.  The path $$a-x-b-y-c-z-a$$ is a Hamiltonian cycle, that we draw as a circle in the plane, as shown below:

<a href="http://presheaf.com/?d=d1f3c3z5i342j3s47402p5e1l6h1k2f2i"><img src="http://presheaf.com/cache/d1f3c3z5i342j3s47402p5e1l6h1k2f2i.png" title="click to go to presheaf.com for editing"/></a>

This contains 6 of the 9 edges of $$K_{3,3}$$; we need to add the edges $$a-y, b-z$$ and $$c-x$$.  The edge $$a-y$$ could be drawn inside the circle or outside, suppose we draw it inside, as shown below, with the added edge dashed.

<a href="http://presheaf.com/?d=d6p443t5v3w101e1r2g1u1x156y6870"><img src="http://presheaf.com/cache/d6p443t5v3w101e1r2g1u1x156y6870.png" title="click to go to presheaf.com for editing"/></a>

Then on the inside of the circle, $$x$$ and $$c$$ are on different sides of the line $$a-y$$, and so the edge connecting them must go outside the circle.  The added edge could go around the right of the circle, as shown below here:

<a href="http://presheaf.com/?d=d2s4y614j59131z1j4ul375e2s1r6l4g"><img src="http://presheaf.com/cache/d2s4y614j59131z1j4ul375e2s1r6l4g.png" title="click to go to presheaf.com for editing"/></a>


or around the left, as shown here:

<a href="http://presheaf.com/?d=d4i6r67d2b5z2u3p6ao1g42453q176z"><img src="http://presheaf.com/cache/d4i6r67d2b5z2u3p6ao1g42453q176z.png" title="click to go to presheaf.com for editing"/></a>


But now $$b$$ and $$z$$ are different sides of $$a-y$$ inside the circle, and on different sides of $$c-x$$ outside the circle, and so cannot be connected without making two edges cross.

If we had began by drawing $$a-y$$ outside the circle, then we would have had to draw $$c-x$$ inside the circle, and had the same problem with being able to draw the last line; as shown here:

<a href="http://presheaf.com/?d=d1015p1r712k18714i5l9282s1n621d"><img src="http://presheaf.com/cache/d1015p1r712k18714i5l9282s1n621d.png" title="click to go to presheaf.com for editing"/></a>

An unnecessary case and steoreographic projection
======

In the proof as presented, we do two cases that seem essentially identical -- namely, whether the first edge $$a-y$$ was drawn inside the circle or outside the circle.  In a good proof you don't want to consider more cases than necessary, so it's worth stopping to see if these cases are really "the same" or not.

At first glance, the inside and outside of the circle seem to appear very different: the inside has finite area, while the outside has infinite area.  However, here's a slightly different situation where the inside and outside are obviously interchangable: replace $$\R^2$$ with the sphere $$S^2$$, and draw the circle as the equator.  Then the "inside" is the northern hemisphere, and the "outside" is the southern hemisphere, and obviously we can just do a reflection to interchange them.

It seems like a huge leap to replace the plane with the sphere, but the sphere is really just the plane with one additional point!  Put another way, suppose we could draw $$\Gamma$$ on the sphere.  Our drawing would miss at least point, and if we cut open the sphere at that one point we could stretch the sphere out and lay it flat on the plane, giving a drawing of $$\Gamma$$ on the plane.

That sounded vague, but one way it can be made precise is the following: through [stereographic projection](https://en.wikipedia.org/wiki/Stereographic_projection), which the wikipedia page makes look complicated, but is really just this picture:

![Stolen stereographic projection picture](../stereographicprojection.jpg)

Draw the sphere as the unit sphere centerred at the origin, so the North pole is the point $$N=(0,0,1)$$.  Then, for any point $$Z\neq N$$ on the sphere, there is a unique line through $$N$$ and $$Z$$.  That line will meet the $$xy$$ plane in a unique point $$z$$.  Similarly, given any point $$z$$ in the $$xy$$ plane, the line through $$z$$ and $$N$$ will meet the sphere in one other point $$Z$$.  This gives a bijection between points on the plane, and points on there sphere (except for the north pole).

If discussion above we slightly lacking, there are lots of [fun videos](https://www.youtube.com/watch?v=6JgGKViQzbc) showing (variations of) stereographic projection on youtube.  I mentioned in particular [Henry Segerman's videos](https://www.youtube.com/watch?v=VX-0Laeczgk) that illustrated this using shadows and 3-d printed spheres.

Back to planar graphs
-------

If that digression into topology seemed long and pointless, the upshot is that if we're trying to prove a Hamiltonian graph is nonplanar, we can treat the inside and the outside of the circle as equivalent, and so when we try to add the very first edge we may as well put it inside.  This gives us one less choice, and so makes our proofs about half as long!  We will use this trick to show that:

The complete graph $$K_5$$ isn't planar
====


The proof is similar, in that we begin by picking a Hamiltonian cycle, say, $$a-b-c-d-e-a$$, and drawing this as a cirlce in the plane, and then try to add the remaining edges.  $$K_5$$ has $$5\cdot 4/2=10$$ edges, and 5 are contained in the cycle, so we have 5 more edges to add -- $$a-c, a-d, b-d,b-e$$ and $$c-e$$.

Since the inside and outside of the circle are equivalent, we will assume the first edge $$a-c$$ is drawn *inside* the circle, giving us the following picture:

  <a href="http://presheaf.com/?d=dq3e1p4v556ry3y6sf702oq317343"><img src="http://presheaf.com/cache/dq3e1p4v556ry3y6sf702oq317343.png" title="click to go to presheaf.com for editing"/></a>

It may be tempting to next consider the edge $$a-d$$, but this could be drawn either inside or outside the circle, and so we'd have to start considering cases.  We get a shorter, cleaner proof if we now move on to the vertex $$b$$.

  The vertex $$b$$ is separated from $$d$$ and $$e$$ on the inside of the circle by the line $$ac$$, and hence the edges $$b-e$$ and $$b-d$$ must be drawn on the outside of the circle.  These edges separate $$a$$ from $$d$$ on the outside of the circle, and so this must be drawn inside, giving the following picture:

<a href="http://presheaf.com/?d=d5f4c451j4lgx3zy171b161j6f52i"><img src="http://presheaf.com/cache/d5f4c451j4lgx3zy171b161j6f52i.png" title="click to go to presheaf.com for editing"/></a>

But now we cannot add the final $$c-e$$, as $$c$$ and $$e$$ are separated from each other on both the outside and the inside of the circle.$$\square$$

Generalization: The planarity algorithm for Hamiltonian Graphs
====

The arguments we made to show $$K_{3,3}$$ and $$K_5$$ aren't planar can be adapted to easily give a criterion for whether or not *any* Hamiltonian graph is planar or not.

Suppose $$G$$ is Hamiltonian, and choose a Hamiltonian cycle $$C$$;  If $$G$$ is planar, then $$C$$ will be drawn as a circle, and every other edge must either lie entirely inside or outside the graph.  Now if we pick two edges $$e=ab$$ and $$f=xy$$ that are not part of the cycle, two things can happen depending on the ordering of $$a,b,x,y$$ along the circle:

1. If the vertices of $$e$$ and $$f$$ do not interlace (e.g. $$abxy, yxab, xbay$$), or if they share a vertex (e.g. $$x=a$$); then $$e$$ and $$f$$ may both be drawn inside or outside the circle without crossing.
2. If the vertices of $$e$$ and $$f$$ do interlace (e.g. $$axby, xayb, yaxb$$), then if $$e$$ and $$f$$ are drawn both inside or both outside the circle, they most cross.

So, to see if the whether or not $$G$$ is Hamiltonian, we must look at all the edges that aren't in $$C$$, and see if we can split them into two sets, one to be drawn inside, and one to be drawn outside, so that it can be done without crossing.  It turns out there's a slick way to do this.

Definition: Crossing graph
====

Let $$G$$ be a Hamiltonian graph and $$C$$ and Hamiltonian cycle in $$G$$.  The *crossing graph* of $$G$$ and $$C$$, denoted Cross($$G, C$$), has vertices the edges of $$G$$ that aren't in the cycle, and an edge between two vertices $$p$$ and $$q$$ if the vertices of the corresponding edges interleave, that is, $$p$$ and $$q$$ are adjacent if they cannot be drawn on the same side of the cycle $$C$$ without crossing.

The Planarity Algorithm for Hamiltonian graphs
====
Suppose $$G$$ is Hamiltonian, with $$C$$ a Hamiltonian cycle.  Then $$G$$ is planar if and only if Cross($$G, C$$) is bipartite.

Proof:
===

$$G$$ is bipartite if and only if we can split the edges not in $$C$$ into two sets, inside and outside, so that we can draw each set entirely inside or outside $$C$$ without crossing.  But two edges cross if and only if their corresponding vertices in Cross($$G, C$$) are adjacent.  So trying to draw the edges of $$G$$ without crossing is exactly trying to

Example:
====

One can check that Cross($$K_{3,3}$$) will be a three cycle for any choice of Hamiltonian cycle, and Cross($$K_5$$) will be a five cycle; neither of which is Hamiltonian.


Example:
===

Consider the graph $$H$$ shown in the following picture:

![A planar graph H](../PlanarH.svg)

It's obviously Hamiltonian with cycle $$abcxyza$$, and its crossing graph with respect to this cycle is the following:

![the crossing graph of H](../CrossH.svg)

For example, in $$H$$ the edge $$ax$$ crosses the three edges $$cy, cz$$ and $$bz$$, and so in Cross($$H$$), the vertex $$ax$$ is adjacent to those vertices.  

It is clear from the picture that Cross($$H, abcxyza$$) is bipartite, for instance, we may colour $$ax, bx$$ and $$ay$$ red, and the other three vertices blue.  But this tells us how to draw the graph of $$H$$ in the plane -- we draw all the red vertices inside the cycle, and the blue vertices outside the cycle, giving the following:

![A planar drawing of H](../HdrawnPlanar.svg)


Last session we proved that the graphs $$K_{3,3}$$ and $$K_5$$ are not planar.  We now discuss Kuratowski's theorem, which states that, in a well defined sense, having a $$K_{3,3}$$ or a $$K_5$$ are the *only* obstruction to being non-planar.

 We begin with some two simple observations.

Observation 1
=====

If $$H$$ is a subgraph of $$G$$, and $$H$$ is not planar, then $$G$$ is not planar.

Proof
====

If we could draw $$G$$ in the plane, it would produce a drawing of $$H$$ in the plane, a contradiction.  $$\square$$

As an immediate corrolary, we see that $$K_n$$ is not planar for $$n\geq 5$$, as all such complete graphs contain $$K_5$$ as a subgraph; similarly, $$K_{m,n}$$ are not planar, with $$m,n\geq 3$$.

Our second observation is the following: suppose we took a graph $$\Gamma$$, and made a new graph $$\Gamma^\prime$$ by adding one vertex of degree 2 in the middle of one of the edges of $$\Gamma$$.  Then drawing $$\Gamma^\prime$$ is basically the same as drawing $$\Gamma$$, and then sticking an extra dot on an edge.  Hence, $$\Gamma^\prime$$ will be planar if and only if $$\Gamma$$ was.  



We now make this precise:

Definition
======



We say that $$\Gamma^\prime$$ is a subdivision of $$\Gamma$$ if it is obtained from $$\Gamma$$ by repeatedly choosing an edge $$e$$ and splitting it into two by adding a new vertex, as in the following picture: 

![Splitting/Joining an edge](../TeXpictures/split.png)


Observation 2
=====
Suppose that $$\Gamma^\prime$$ is a subdivision of $$\Gamma$$.  Then $$\Gamma^\prime$$ is planar if and only if $$\Gamma$$ is.


Example
=====
The following graph $$G$$ is nonplanar, since it is obtained from $$K_{3,3}$$ by subdividing a single edge.

![K33 Subdivision](../TeXpictures/K33homeo.png)


Putting together the two lemmas, we see that if $$G$$ has a subgraph $$H$$, so that $$H$$ is a subdivision of a non-planar graph (like $$K_5$$ or $$K_{3,3}$$), then we $$G$$ isn't planar.  We illustrate this now in an exmaple.

Example: The Petersen graph is not planar
=====

![PetersenSubgraph](../TeXpictures/PetersenNonPlanar.png)

The subgraph drawn with thick edges (containing all but two of the edges in the Petersen graph) is homeorphic to $$K_{3,3}$$.  we have drawn three vertices blue and three vertices red to highlight the vertices of $$K_{3,3}$$.  The nonhighlighted edges are in the subgraph, but they are the ones that are forgetten to show that the highlighted graph is homeomorphic to $$K_{3,3}$$.


Kuratowski's Theorem
========

A graph $$G$$ is nonplanar if and only if it contains a subgraph homeomorphic to $$K_5$$ or $$K_{3,3}$$.



Our two observations, together with this morning's result that $$K_{3,3}$$ and $$K_5$$ are nonplanar, prove the "if" direction.  The "only if" direction is much harder, and we will not prove it.

However, we will only use the "only if" direction implicitly.  Using the "only if" direction explicitly would amount to prove that some graph was planar by showing it had no subgraphs that were subdivisions of $$K_5$$ or $$K_{3,3}$$, which we would be quite laborious.  We have a much easier way to prove that a graph *is* planar: drawing it in the plane.

We will however, use the "only if" direction implicitly in the following way.  Suppose we have a graph $$G$$, and we want to determine if $$G$$ is planar or not.  We can try to prove it is planar by trying to draw it in the plane, and we can try to prove it is not planar by finding a subgraph of $$G$$ that is homeomorphic to either $$K_{3,3}$$ or $$K_5$$.  The "only if" direction of Kuratowski's theorem tells us that one or the other of these attempts will *always* work.  Thus, we have a practical method to determine whether or not a graph is planar or not -- try to draw it in the plane.  If you find this difficult, and begin to expect that it isn't possible, start looking for a subgraph homeomorphic to either $$K_5$$ or $$K_{3,3}$$, which would prove it can't be drawn on the plane.


Graphs on other surfaces
-------------

We now transition to drawing graphs on other surfaces.  In lecture, we had some <a href="http://slides.com/pauljohnson/deck-2#/">slides providing pictures</a> for the beginning of this discussion; a few, but not all, of those images are in the body of these notes now.

Trying to draw graphs on surfaces can be fun, but it seems like a rather unmotivated question to consider, so we began with motivating it by videogames.  Many videogames (pacman, asteroids, overhead RPGs like the early Final Fantasy games) take place on a rectangle screen:

![Videogame map](../Slides/Pictures/chronostatic.gif)

To avoid making the world have an "edge", the result will often happen: if a character moves off the right of the screen it will reappear at the edge of the left screen, and similarly if a character moves off the top of the screen, it reappears on the corresponding place on the bottom of the screen.  

This set-up is used to simulate the surface of a planet.  However, if one traces through the result of these identifications, one sees that the surface is a torus:

![map folding](../Slides/Pictures/chronofolding.gif)





Definition
=====

A "video-game graph" is one that "locally looks like" a part of graph paper.

Motivating Question
=======

If videogame designers were more clever, could they put a finite videogame graph on the sphere?  Can you prove that it isn't possible?



Drawing graphs on the torus
------

If we wanted to draw a graph on the sphere, we could do this physically by taking a balloon and a felt pen, but it would be a little awkward to turn in or mark homeworks this way.  Luckily, we saw last time that, using stereographic projection, drawing a graph on the sphere is equivalent to being able to draw it on the plane.

Similarly, we could draw graphs on torus by getting donuts, and writing on them with icing sugar.  But again, this is rather impractical, and we'd like a way to represent drawing a graph on a torus that is conveniently done on a piece of paper.  

The videogame / paper-folding discussion shows us how to do this.  We draw a square to represent the torus.  On the top and bottom border we draw one arrow in the same direction, to signify that these edges will be identified (this is how the paper was folded, or what a character does in the videogame).  We do similar with the side borders, with two arrows.  

Then we can draw the graph in the square, with the following added options -- if a drawn edge reaches the left (right) border, it continues at the same spot on the right (left) border, and similarly with the top/bottom borders.  


Example
====

$$K_5$$ and $$K_6$$ cannot be drawn on the plane, but they can be drawn on the torus as follows:

![K5 and K6 on the torus](../TeXpictures/K5K6torus.png)

The graph on the left shows $$K_5$$ on the torus.  The picture on the right has the same drawing of $$K_5$$ in black, but in red has added an extra vertex and 5 extra edges incident to it to make a $$K_6$$.  There are appear to be 4 red vertices, at each corner of the square, but since all the corners get identified by the folding, they correspond to the same point of the torus. 


Challenge
=====

Draw $$K_7$$ on the torus.  

It turns out that $$K_8$$ cannot be drawn on the torus; we will prove this later.


What comes next?
-------
What other surfaces other than the sphere and torus are possible?  One possibility is just adding  "more holes"; this produces the "donut with $$g$$ holes", more formally known as the "suface of genus $$g$$".

You won't have to work with surfaces of higher genus, but it is worth knowing that this is an active area of research and investigation.  It turns out (try to prove it!  It's not hard...) that given any finite graph $$\Gamma$$, there is some $$g$$ so that $$\Gamma$$ can be drawn on a surface of genus $$g$$ without the edges crossing.  The *genus* of a graph $$\Gamma$$ is defined to be the lowest $$G$$ such that this can be done.

Nonorientable Surfaces
=======

Although you won't have to work with surfaces of higher genus, you will have to be able to work with a couple of other surfaces.  We will end this lecture by introducing the Mobius band:

Unorientable surfaces
-----

In this half of the lecture, we introduce the real projective plane, the simplest closed compact unorientable surface.  

Before we do that, it is easiest to review an unorientable surface with boundary that may be more familiar: the Mobius band.

The Mobius band
===

Suppose one has a strip of paper and glues the opposite edges together in the natural way -- this makes a cylinder.

If instead, one glued the ends together with half a twist, one would get the Mobius band:

![mobius band glue](../Slides/Pictures/mobiusglue.jpg)

The mobius band is not the same topological space as the cylinder.  One way to see this is that it is *unorientable* -- there is not a consistent notion of left and right on the Mobius band.  If you start at one point on the Mobius band, and travel along it until you jump across the other side of the identification, you will eventually return to where you started.  However, your left and right will have been interchanged!  This is seen in the following pictures, [stolen from this blog post](https://haggisthesheep.wordpress.com/2009/06/15/mobius-strips/):

![courtesy haggisthesheep.blogspot.com](../Slides/Pictures/mobiusunorientable.jpg)

The creature started out, his right hand was blue, but when he returns from his trip around the mobius band it is now his left hand that is blue!

Dual graphs
-----------


In the examples at the very beginning of the course, we got a graph from a drawing on the sphere: the Risk board, or more generally, any map.

The countries (or counties or states or whatever region we are working with) are the vertices, and two countries are adjacent if they share a border.

This is different from how we have been thinking about drawing graphs on surfaces -- for us, the places where more than two countries meet would be the vertices, and the borders would again be edges.  But both of these graphs are coming from the same drawing on the sphere, and so must be related somehow; the concept of *dual graphs* makes this precise.

Definition
=====

Let $$\Gamma$$ be drawn on a surface $$S$$.  The connected components of $$S\setminus\Gamma$$ -- i.e., the pieces we would have if we cut $$S$$ along $$\Gamma$$ -- are called *faces*


Note: by the Jordan curve theorem, on a sphere, each face will just be a disk.  However, this need not be true on a regular surface -- for instance, we can get a cylinder as a connected region on the Torus, and the Mobius band as a connected region on the projective plane.

Definition
=====

Let $$\Gamma$$ be drawn on a surface $$S$$, with vertices $$v$$.  The *dual graph* of $$\Gamma, S$$ is the graph with a vertex for each face of $$\Gamma, S$$, and an edge for each edge of $$e\in E(\Gamma)$$, that connects the two faces that $$e$$ separates.

It is not hard to see that the faces of the dual graph are the vertices of the original graph, and hence that the dual of the dual graph of $$\Gamma$$ is the original graph $$\Gamma$$ back.

Euler's Theorem
======

Let \\(\Gamma\\) be a graph drawn on the sphere, and suppose that $$\Gamma$$ has $$v$$ vertices, $$e$$ edges, and $$f$$ faces.  Then $$v-e+f=2$$.

Proof idea: 
=====



One way to prove it is the following: pick an edge $$e$$ on $$\Gamma$$.  If we delete an edge from $$\Gamma$$, we will (usually) merge two faces into one, and thus have one less edge and one less face; this does not change $$v-e+f$$, and gives us a simpler graph where we know $$v-e+f=2$$ by induction.

The only case where deleting the edge $$e$$ doesn't merge two faces into one is when both sides of the edges are actually the same face; in this case, removing $$e$$ disconnects the graph $$\Gamma$$.  One can compute inductively from the two pieces, or perhaps more simply, simply contract the edge $$e$$ in this case, leaving the number of faces unchanged, and reducing the number of edges and vertices by one; again, this doesn't chave $$v-e+f$$, and will give us a simpler graph where we know $$v-e+f=2$$ by induction.

Applications of Euler characteristic
------

Euler's theorem can be very useful in proving results about graphs on the sphere.  It's a bit awkward to use by itself -- it contains three variables, $$v, e$$ and $$f$$, so it is most useful when we already know some relations between these variables.  This may be best illustrated by our motivating example:


Theorem
====

It is impossible to draw a sphere with a videogame graph.

Proof
====

Recall that in a videogame graph, every vertex had degree 4, and each face was a square.

Suppose that we had such a graph drawn on the sphere; Euler's theorem gives us $$v-e+f=2$$; we need to use our other knowledge about the graph to get a contradiction.

How can we use that every vertex has degree 4?  The handshaking lemma!  Since every vertex has degree 4, the sum of the degrees of the vertices is just $$4v$$.  So the Handshaking Lemma just says $$4v=2e$$, and hence $$e=2v$$.

How can we use that every face has four sides?  We can do something just like the handshaking lemma, and count the number of times a face meets an edge.  On the one hand, each edge meets two faces, and so there are $$2e$$ places that an edge meets a face.  On the other hand, each face meets four edges, and so we see there are $$4f$$ times a face meets an edge, and so we have that $$2e=4f$$, or $$e=2f$$.

Putting $$e=2v$$ and $$e=2f$$ together, we see that $$f=v$$, and so $$v-e+f=v-2v+v=0$$, which is a direct contradiction of Euler's Formula $$,\quad \square$$


It's worth noting that "handshaking between edges and faces" actually *is* the handshaking lemma for the dual graph.

To generalize this, we note that we have three sources of relationships between $$v, e$$ and $$f$$ for a planar graph:

1. Euler's Formula
2. Handshaking between vertices and edges
3. Handshaking between edges and faces

These three relations can work together to prove a lot.  We give one more example now -- another proof that $$K_5$$ and $$K_{3,3}$$ aren't planar.  Yet another example can be found on the last homework set -- figuring out how many pentagons a football has.


Application: $$K_5$$ and $$K_{3,3}$$ aren't planar
=====

Let's try to give another proof that $$K_5$$ and $$K_{3,3}$$ aren't planar using Euler's formula.

First, let's show $$K_5$$ isn't planar.  We know explicitly that $$K_5$$ has 5 vertices and 10 edges, so if it were drawn on the sphere we would have

$$2=v-e+f=5-10+f=f-5$$

and so it would have to have 7 faces.  To get a contradiction, we need another way to get information about how many faces the drawing would have, which we can do via handshaking.  $$K_5$$ has no multiple edges or loops, and so the smallest number of edges a face could have is 3.  Thus, handshaking gives us

$$2e=\sum_{f \text{ face} } d(f)\geq \sum_f 3=3f$$
i.e., $$2e\geq 3f$$.  But we know $$e=10$$ and $$f=7$$, so we have a contradiction.

The argument for $$K_{3,3}$$ is similar; we know it has 6 vertices and 9 edges, so if it were drawn on the plane it would need to have 5 faces.  $$K_{3,3}$$ is simple, so again we have that each face has at least three sides, but this isn't strong enough for our purposes.  But, since $$K_{3,3}$$ is bipartite, it can't have any cycles of length three (or any odd number for that matter).  Thus, every face of any drawing of $$K_{3,3}$$ must have at least 4 sides.  Handshaking between faces and edges then gives $$2e\geq 4f$$, but there are 9 edges and 5 faces, a contradiction.  $$\square$$

Application: Footballs have 12 pentagons.
====
On a football, every vertex is trivalent, but there are two types of faces, pentagons and hexagons.  Let $$P$$ be the number of pentagons, and $$H$$ the number of hexagons.  Then $$f=P+H$$, so Euler's theorem gives $$V-E+P+H=2$$.

Using handshaking between vertices and edges gives $$3V=2E$$, and using handshaking between faces and edges gives $$5P+6H=2E$$.  Thus, we see $$6V-6E=-2E=-5P-6H$$, where the first equality is vertex-edge handshaking and the second vertex-face.  Multiplying Euler's theorem by 6 gives $$6V-6H+6P+6H=12$$, and substituting in our deduction from handshaking gives $$P=12$$.


Generalization: Euler characteristic and the beginnings of topology
-------

This is more just general mathematical culture than something you would see on the exam.

We have seen for that graphs drawn on the sphere, we have $$v-e+f=2$$.  Given that we've discussed drawing graphs on other surfaces, it becomes a natural question to ask if there's a similar relation for $$v-e+f$$ if we have a graph $$\Gamma$$ drawn on a different surface $$S$$.  You have to be a little bit more careful in defining what a face is: since the Jordan Curve Theorem fails for surfaces that aren't the sphere, it is not the case that every component of $$S\setminus \Gamma$$ will be a disk.

However, if we require that $$S$$ is drawn on the surface in such a way so that every "face" is actually a disk, then it turns out that $$v-e+f=\chi(S)$$, where $$\chi(S)$$ is some number, called the *Euler characteristic*, that depends *only* on the surface $$S$$, and not on the graph.

As an example, we saw that video game graphs always had $$v-e+f=0$$, and the natural way we got to make video game graphs were all living on the torus; the torus has euler characteristic 0.
