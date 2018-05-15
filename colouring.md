---
layout: page
title: Colouring Graphs
permalink: /Colouring/
---

The last topic we will cover is coulouring graphs.  There will be three elements to this -- chromatic number, chromatic index, and chromatic polynomials.


Chromatic number
-----

When colouring maps, often the different regions (countries, counties, states) are given different colours, with the idea that adjance regions should have different colours so the boundaries can be easily seen.  For instance, in this map of Britain and Ireland each county is coloured one five colours (red, yellow, green, brown and purple), with counties that border on each other having different colours.

![Map of British Counties](../TeXpictures/BritishCounties.png)

Definition: Chromatic number
====

The *chromatic number*, denoted $$\chi(\Gamma)$$, of a graph $$\Gamma$$ is the least number of colours needed to colour the vertices of $$\Gamma$$ so that adjacent vertices are given different colours.

The study of chromatic numbers began with trying to colour maps as described above: it was conjectured in the 1800's that any map drawn on the sphere could be coloured with only four colours.  This does not have much practical application: note, for instance, that the map of Britain above uses five colours.   This conjecture was not proven for more than a hundred years, and is now known as the [four colour theorem](https://en.wikipedia.org/wiki/Four_color_theorem).


Theorem (Appel and Haken, 1976)
===
Any planar graph $$G$$ can be coloured with four colours; i.e., $$\chi(G)\leq 4$$.

The proof of the four colours theorem is enormous, taking hundreds of pages as well as computer calculations.  It was the first major theorem to rely heavily on computer calculations, and was very controversial at the time because it raised philosophical questions about what mathematics is for.  We often say we just want to prove things, but if proof involves checking thousands of cases using a computer than what use is it, really?  What we really want is *human understanding*, and a proof is one way of doing that.

The original proof of the four colour theorem has been simplified some, but it still huge.  It has also been *formalized*, i.e., written in a special computer language that checks that each step follows logical from the previous one and no steps are skipped.  


Example: Complete graph
====

The complete graph $$K_n$$ has chromatic number $$\chi(K_n)=n$$.  Since evevery vertex is adjacent to every other vertex, no two vertices can have the same colour. $$\square$$

Notation warning
====
Not that we used $$\chi$$ earlier to denote the Euler characteristic, but there we talked about the Euler characteristic of a surface, $$\chi(S)$$, where we talk about chromatic number of a graph, and so it should be clear what $$\chi$$ means from whether its input is a surface or a graph, but this should be unnecessary as words and context in the problem should make which meaning of $$\chi$$ is being used.

Example: Cube and octahedron
====

Another potential source of confusion is when graphs are drawn on surfaces.  In the map discussion above, we were trying to colour the faces of the graph, where in the definition of chromatic number we are colouring the vertices of the graph.  If there is a graph on a surface, the colouring we are trying to do should be made clear from context, but we'd like to highlight that these two viewpoints are related by the notion of the dual graph of a graph on a surface -- colouring the faces of a graph $$\Gamma$$ on a surface $$S$$ is equivalent to colouring the vertices of its dual graph.

For example, let $$C$$ denote the cube graph.  What's $$\chi(C)$$?  The cube has an edge, and so it takes at least two colours to colour.  On the other hand, it is easy to see that two colours suffice, as in the following drawing:

![A colouring of the cube](../TeXpictures/CubeColouring.gif)

If we want to colour the *faces* of the cube, however, we quickly see that we are going to need at least three colours: pick any vertex, and look at the three faces that touch that vertex; they will all be touching each other, and thus will need to be different colours.  

On the other hand, we can describe a colouring of the faces of the cube that takes only three colours -- colour each face and the face directly opposite it the same colour.

Example: Bipartite graphs
====
We have already discussed one example of chromatic number, in bipartite graphs.  A graph has chromatic number 1 if and only if it has no edges.  A graph with at least one edge that has chromatic number two is bipartite; in particular, we see that the cube had chromatic number 2 because it is bipartite, whereas the octahedron has triangles and hence had higher chromatic number.



Example: the cycle $$C_n$$
====
When $$n$$ is even, $$C_n$$ is bipartite, and so can be coloured with two colours, just alternating colours as we pass through the cycle.  

if $$n$$ is odd, $$C_n$$ is not bipartite, and so we will need at least three colours to colour the vertices.  It is easy to see that three is enough -- just alternate with two colours until we get to the very last vertex of the cycle, which we can make the third colour.



Upper bounds on $$\chi(G)$$
------

Definition
====
We use $$\Delta(G)$$ to denote the maximum degree of $$G$$, i.e., the highest degree of any vertex.

Theorem
====
$$\chi(G)\leq \Delta(G)+1$$

Proof
====

The basic idea is to just colour the vertices one by one -- when we go to colour a vertex, it touches at most $$\Delta(G)$$ vertices that are already coloured, and we just give it a colour that isn't one of those.  If we have $$\Delta(G)+1$$ colours available this is always possible.

To prove this more formally, we use induction on the number of vertices.  It is clear that any graph with 0 or 1 vertex can be coloured with 1 colour.  

Suppose now that we have fixed an interger $$m$$, and we know that every graph with $$\Delta(G)\leq m$$ and with less than $$k$$ vertices can be coloured with at most $$m+1$$ colours.  We want to show that any graph $$\Gamma$$ with $$k$$ vertices can be coloured with at most $$m+1$$ vertices.  

Pick any vertex $$v$$ of $$\Gamma$$ and remove it.  The resulting graph $$\Gamma\setminus v$$ has $$k-1$$ vertices and so by the inductive hypothesis can be coloured with at most $$m+1$$ colours.  Now, we need to colour $$v$$.  But $$v$$ is adjacent to at most $$m$$ vertices of $$\Gamma$$, so at least one of $$m+1$$ colours does not appear at a vertex adjacent to $$v$$ -- colouring $$v$$ this colour does what we need.


The 5 Colour Theorem
===

Although the 4 colour theorem is extremely difficult to prove, weaker bounds are easy.  The six colour theorem can be derived from Euler's theorem and induction, and with a little more work the 5 colour theorem can be proved.


Chromatic index: Edge colouring
----


Similarly to trying to colour the vertices of $$G$$, we could try to colour the edges, with the desire that edges that share a vertex have different colours.

Definition
====

The *chromatic index* of $$G$$, denoted $$\chi^\prime(G)$$, is the least number of colours necessary to colour the edges of $$G$$ so that any two edges that share a vertex have different colours.


To determine the chromatic index of a graph one first obtains an upper bound by actually colouring the edges.  Then one shows a lower bound by proving that less colours can't be used.  This can be done by analyzing what happens if we try to use less colours, or sometimes by a count of the number of edges and how many can be in a given group.


Example: $$K_4$$ 
===

Let's find $$\chi^\prime(K_4)$$.  Picking any vertex $$v$$, there are three edges incident to $$v$$, and none of these edges can have the same colour (as they all meet at $$v$$).  Hence, we have $$\chi^\prime(K_4)\geq 3$$.

On the other hand, it is easy to colour the edges of $$K_4$$ with three colours, as seen below, and so $$\chi^\prime(K_4)\leq 3$$, and hence $$\chi^\prime(K_4)=3$$.



Example: $$K_5$$.
===

Now, let's move on to $$K_5$$.  Again, looking at any vertex we see all the edges adjacent to that vertex must be different colours, and so we have $$\chi^\prime(K_5)\geq 4$$.   Let's try to colour the edges of $$K_5$$ with 4 colours.


Suppose we coloured the four edges adjacent to the top vertex blue, green, red and purple, from left to right, and now look at the bottom edge.  It is adjacent to edges coloured green and red, and so must be blue or purple.  By symmetry, it's equivalent to colour it either colour, so let's suppose it's blue, giving us the following picture:

![First step of showing you can't colour K_5 with 4 colours](../TeXpictures/K5EdgeColouring1.png)

Now the edge on the right is adjacent to edges coloured red, blue and purple, and so must be green.  But now we have a problem -- consider the edges labeled $$x$$ and $$y$$ in the next drawing:

![Second](../TeXpictures/K5EdgeColouring2.png)

Both edges share vertices with edges coloured green, blue, and purple, and hence each would need to be coloured red.  But they also share a vertex with each other, and so cannot both be coloured red.  So we see $$\chi^\prime(K_5)\geq 5$$.  

On the other hand, it is easy to colour the edges of $$K_5$$ with 5 colours:  colour each edge in the outside pentagon a different colour.  For each edge in the outside pentagon there will be a unique edge in the inside star that does meet that edge (the one "parallel" to it) -- draw that edge the same colour.  That results in the following colouring:

![5 colouring](../TeXpictures/K5EdgeColouring3.png)





We saw the last lecture that the chromatic number of a graph had an upper bound of $$\Delta(G)+1$$; it turns out that this holds for the chromatic index as well, although the proof is more difficult and we will skip it:

Vizing's Theorem
====

Let $$G$$ be a simple graph with largest vertex degree $$\Delta(G)$$.  Then 

$$\Delta(G)\leq \chi^\prime(G)\leq \Delta(G)+1$$

Proof
===

The lower bound is trivial -- let $$v$$ be the vertex with degree $$\Delta$$.  The $$\Delta$$ edges adjacent to $$v$$ all need different colours.  Upper bound is harder.


Application: Chromatic number and chromatic index
====

We now give application of chromatic number and chromatic index of the same graph. 

Suppose there are six friends, Alice, Bob, Charlie, Dora, Elizabeth and Frank, and there is the following graph between then:

<table>
<tr> <td>A</td> <td></td><td></td><td></td><td></td><td></td></tr>
<tr> <td>x</td><td>B</td><td></td><td></td><td></td><td></td></tr>
<tr><td>x</td><td></td><td>C</td><td></td><td></td><td></td></tr>
<tr><td></td><td>x</td><td>x</td><td>D</td><td></td><td></td></tr>
<tr><td>x</td><td></td><td>x</td><td></td><td>E</td><td></td></tr>
<tr><td></td><td>x</td><td></td><td>x</td><td>x</td><td>F</td></tr>
</table>

which translates into the following graph:

![graph of the table](../TeXpictures/ChromaticNumberVsIndex.png)

Here are two word problems, one of which relates to the chromatic number, and another relates to the chromatic index of $$G$$

1. The friends want to divide into groups, but the xs indicate people who currently annoy each other.  What's the least number of groups the friends can divide into groups so that no group contains two people who annoy each other.
2. The friends want to hold a snooker tournament, with everyone playing three matches; the xs indicate pairs of friends who will play against each other.  If multiple matches can be played each day, but each person can only be involved in one match a day, how many days are necessary to hold the tournament?


The first case concerns the chromatic number -- each group of people will be the people who have the same colour, and we don't want vertices with an edge between them to have the same colour.  

The second case concerns the chromatic index -- the edges are the games that are being played, and all edges that are the same colour will be played on the same day.

To end today, let us quickly compute the chromatic number and chromatic index of the graph $$G$$ above.  To compute the chromatic number, we observe that the graph contains a triangle, and so the chromatic number is at least 3.  But it is easy to colour the vertices with three colours -- for instance, colour A and D red, colour C and F blue, and colur E and B green.  So $$\chi(G)=3$$.

To compute $$\chi^\prime(G)$$, since A has degree three we have $$\chi^\prime(G)\geq 3$$.  On the other hand, it is easy to colour the edges with three colours -- for instance, colour AB, CE and DF red, colour AE, CD and BF blue, and colour AC, BD and EF green.  So $$\chi^\prime(G)=3$$ as well.




Chromatic polynomial
----

Instead of just asking whether the vertices of a graph can be coloured using $$k$$ colours, one could try to *count* how many different ways the graph can be coloured using that many colours.

Definition
====

Let $$G$$ be a simple graph and let $$k$$ be a positive integer.  The *chromatic polynomial*, written $$P_G(k)$$ counts the number of ways to colour the vertices of $$G$$ with $$k$$ colours


Example: The complete graph
====

Suppose we want to colour the complete graph $$K_n$$ with $$k$$ colours.  We colour the vertices one by one.  For the first vertex, we can choose any of the $$k$$ colours.  For the second vertex, we can choose any colour except the one used in the first vertex, and so we have $$k-1$$ choices.  For the third vertex, we must pick a new colour, and hence have $$k-2$$ choices.  Continuing in this manner, we see for the last vertex we will have $$k-(n-1)$$ choices.  Thus, we see that

$$P_{K_n}(k)=k\cdot (k-1)\cdot (k-2)\cdots (k-(n-1))$$


Relation to Chromatic Number
====

Recall the chromatic number $$\chi(G)$$ is the least number $$k$$ so that $$G$$ can be coloured with $$k$$ colours.  If $$G$$ can't be coloured with $$k$$ colours, then there are 0 colourings of $$G$$ with $$k$$ colourings, and so $$P_G(k)=0$$.  If $$G$$ *can* be coloured with $$k$$ colourings, then there is at least one such colouring, and so $$P_G(k)>0$$.  Thus, we see that the chromatic polynomial $$P_G(k)$$ determines the chromatic number $$\chi(G)$$.

Lemma
=====
The chromatic number $$\chi(G)$$ is the least number $$k$$ so that $$P_G(k)\neq 0$$.



For certain graphs, one can calculate the chromatic polynomial just by starting at a vertex, and attempting to colour nearby vertices.  We illustrate this now for a couple of graphs, and also show how for more complicated graphs this method becomes more complicated.

Example: The path graph $$P_n$$
====

Recall the path graph $$P_n$$ consisted of $$n$$ vertices, with vertex $$v_i$$ adjacent to vertices $$v_{i\pm 1}$$.

Starting at the end vertex $$v_1$$, there are $$k$$ possible colours we can colour it.  Moving onto vertex $$v_2$$, it can't be the same colour as $$v_1$$, but otherwise could be any colour, and so there are $$k-1$$ possible colours.  

Similarly, $$v_3$$ can be any colour except that of $$v_2$$, and similarly for each vertex, and so we see $$P_{P_n}=k(k-1)^{n-1}$$.$$\quad\square$$


Note that the above argument holds for any tree, and so all trees have the same chromatic polynomial.


Example 
===
![Not quite K_4](../TeXpictures/GraphGLecture20.png)

Consider the graph $$G$$ above.  Vertex $$1$$ has $$k$$ possibilities, then vertex 2 is adjacent to vertex 1, and so has $$k-1$$ possibilities.  Vertex 3 is adjacent to 1 and 2, which are known to be different colours, and so has $$k-2$$ possibilties.  Similarly, vertex 4 is adjacent to 2 and 3, which are adjacent and hence have different colours, and so vertex 4 has $$k-2$$ possibilities as well, and so $$P_G(k)=k(k-1)(k-2)^2$$

Example: $$C_4$$
====

![The cycle graph C_4](../TeXpictures/c4.png)

Now consider the graph $$C_4$$, as shown above.  Vertex $$1$$ can be any of $$k$$ colours, and vertex 2 has $$k-1$$ possibilities -- any colour except the one used for vertex $$1$$.  Moving to vertex 4, we see it is just adjacent to $$1$$ as well, and so has $$k-1$$ possibilities as well.

It becomes more difficult when we try to colour vertex 3.  It is adjacent to vertices 2 and 4, and so cannot be the same colour as either of these.  However, vertices 2 and 4 are not adjacent, and so we don't know whether they have the same colour or not.  If vertices 2 and 4, have the same colour there are $$k-1$$ possibilities for vertex 3, while if vertices 2 and 4 have different colours, there are only $$k-2$$ possibilties.  Thus, we must count how many possibilities are in each of these cases.

If we want vertices 2 and 4 to have the same colour, we can first colour vertex 1 in $$k$$ different ways, and then pick any of the remaining $$k-1$$ colours for vertices $$2$$ and $$4$$.  Then, to complete this to a colouring of $$C_4$$, with have to colour $$v_3$$, which can be any of the $$k-1$$ colours that aren't the colour $$v_2$$ and $$v_4$$ are coloured.  Thus, the case where $$v_2$$ and $$v_4$$ have the same colour has $$k(k-1)^2$$ possibilities.

If we want vertices 2 and 4 to have different colours, then we can first colour $$v_1$$ any of $$k$$ colours, colour $$v_2$$ any of $$k-1$$ colours.  Now, when we go to colour vertex 4 it can't be the same colour as vertex 1 since they are adjacent, and it can't be the same colour as vertex 2 by our supposition.  Vertices $$v_1$$ and $$v_2$$ have different colours, and so this leaves $$k-2$$ possibilities for $$v_4$$.  Thus there are $$k(k-1)(k-2)$$ possibilities to colour vertices 1, 2 and 4 so that 2 and 4 have different colours, and then there are $$k-2$$ possibilities left for vertex 3, giving $$k(k-1)(k-2)^2$$ ways to colour $$C_4$$ so that vertices 2 and 4 have different colours.  

Adding the two cases together, this gives 

$$P_{C_4}(k)=k(k-1)^2+k(k-1)(k-2)^2=k(k-1)[k-1+(k-2)^2]=k(k-1)(k^2-3k+3)\quad\square$$


For larger graphs, sometimes the colouring method we used above will work well, while for others the type of case by case analysis we needed for $$C_4$$ will explode and make it intractible.  To prove that $$P_G(k)$$ is a polynomial, we will need a general method to deal with it.  





Deletion Contraction
----

Consider an edge $$e$$ in a graph $$\Gamma$$.  There are two new graphs we can make -- we can delete the edge $$e$$, getting a graph $$\Gamma\setminus e$$, that has the same vertex set and one less edge.

We can also *contract* $$e$$ -- that is, shrink it to a point.  Doing this may create multiple edges -- for instance, if we contract an edge in the triangle $$C_3$$, we get two vertices connected by two edges, which we will call $$C_2$$.  These extra edges will not matter for the chromatic polynomial, so if we have multiple edges we will delete the extra copies.  This simplification is necessary, because if we contracted one of the edges of $$C_2$$, we would get a loop, which can't be coloured at all!  

The resulting graph $$\Gamma/e$$ has one less vertex (the two vertices adjacent to $$e$$ have been identified to one) and at least one less edge (the one contracted), but possibly more (if we had to delete some multiple edges).


We want to prove:

Lemma
===

$$P_{\Gamma\setminus e}(k)=P_{\Gamma}(k)+P_{\Gamma/e}$$

Proof
====

Suppose the edge $$e$$ connects vertices $$v$$ and $$w$$.

Consider a colouring of the graph $$\Gamma\setminus e$$.  Then, either the vertices $$v$$ and $$w$$ have the same colour or they have different colours.  If they have different colours, then this colouring is a valid colouring of $$\Gamma$$ itself.

It may happen, however, that $$v$$ and $$w$$ have the same colour.  Such a colouring does not give a colouring of $$\Gamma$$.  However, it does give a colouring of $$\Gamma / e$$, and furthermore any colouring of $$\Gamma / e$$ gives a colouring of $$\Gamma\setminus e$$ where $$v$$ and $$w$$ are the same colour.  $$\square$$

If we rewrite the statement of the lemma as 
$$P_\Gamma(k)=P_{\Gamma\setminus e} (k)-P{\Gamma/e}(k)$$
then we get a recursive way to calculate chromatic functions, as the graphs $$\Gamma\setminus e$$ and $$\Gamma/e$$ each have less edges than $$\Gamma$$. 

We will use this recursive equation to prove that the chromatic polynomial is in fact a polynomial.  As is usual in proofs using a recursion, the proof will use induction.  It is fun for a last proof for the course because it is a double induction, on the number of vertices AND the numebr of edges.


Lemma
===
Let $$\Gamma$$ be a graph with $$n$$ vertices and $$m$$ edges.  The function $$P_\Gamma(k)$$ is a polynomial of degree $$n$$, with leading coefficent $$x^n$$ and second order term $$-mx^{m-1}$$, that is:

$$P_\Gamma(x)=x^n-mx^{n-1}+\dots$$ 

where the dots are lower oder terms.

Proof
===

We use induction on $$m$$ and $$n$$.  As a base case, the empty graph $$E_n$$ has $$P_{E_n}=k^n$$, which holds.

Now suppose that $$\Gamma$$ is a graph with $$n$$ vertices and $$m$$ edges, and we have proven the lemma for all graphs with less than $$n$$ vertices, and for all graphs with $$n$$ vertices but $$j<m$$ edges.  Picking any edge $$e$$ of $$\Gamma$$ and applying deletion-contraction, we have:

$$P_{\Gamma}(x)=P_{\Gamma\setminus e}(x)-P_{\Gamma/e}(x)$$.

By the inductive hypothesis, both the terms on the right hand side are polynomials, so $$P_{\Gamma}(k)$$ is a polynomial.  We have $$P_{\Gamma\setminus e}(k)=x^n-(m-1)x^{n-1}+\cdots$$ and $$P_{\Gamma/e}(k)=x^{n-1}+\cdots$$, so the statements about the degree, leading coefficient, and second coefficient all follow.


Gluing Formula
====

If $$\Gamma$$ is made from two graphs $$\Gamma_1$$ and $$\Gamma_2$$ that only share a vertex or edge in common, then there are "gluing" formulas that express the chromatic polynomial of $$\Gamma$$ nicely in terms of those of $$\Gamma_1$$ and $$\Gamma_2$$.

Theorem:
====
Let $$\Gamma$$ be the union of two subgraphs $$\Gamma_1$$ and $$\Gamma_2$$, with their intersection a single vertex: $$\Gamma_1\cap\Gamma_2=v$$.  Then
$$\chi_\Gamma(k)=\frac{1}{k}\chi_{\Gamma_1}(k)\chi_{\Gamma_2}(k)$$

Proof:
===
There are $$\chi_{\Gamma_1}(k)$$ ways to colour $$\Gamma_1$$ with $$k$$ colours.  To extend this to all of $$\Gamma$$ we need to colour $$\Gamma_2$$, with the proviso that the colour of $$v$$ was fixed for us.  But each of the $$k$$ colours is essentially interchangable; there are as many colourings of $$\Gamma_2$$ where $$v$$ is red, as there are where $$v$$ is blue, as there are when $$v$$ is any colour, hence this is $$1/k$$ of the total.

AS we have $$\chi_{\Gamma_1}(k)$$ ways to colour $$\Gamma_1$$, and then $$\frac{1}{k}\chi_{\Gamma_2}(k)$$ ways to extend the colouring to all of $$\Gamma$$, we have the result. $$\square$$

Theorem:
====
Let $$\Gamma$$ be the union of two subgraphs $$\Gamma_1$$ and $$\Gamma_2$$, with their intersection a single edge $$e$$ between $$v$$ and $$w$$: $$\Gamma_1\cap\Gamma_2=e$$.  Then
$$\chi_\Gamma(k)=\frac{1}{(k)(k-1)}\chi_{\Gamma_1}(k)\chi_{\Gamma_2}(k)$$

Proof:
===
There are $$\chi_{\Gamma_1}(k)$$ ways to colour $$\Gamma_1$$ with $$k$$ colours.  To extend this to all of $$\Gamma$$ we need to colour $$\Gamma_2$$, with the proviso that the colours of $$v$$ and $$w$$ were fixed for us.  Since $$v$$ and $$w$$ were adjacent, they're two different colours.  But each of the pairs of colours are interchangable; there are as many colourings of $$\Gamma_2$$ where $$v$$ and $$w$$ are any pair of two different colours.  Since there are $$k(k-1)$$ ways to colour $$v$$ and $$w$$, the number of ways where $$v$$ and $$w$$ have any given colouring must be $$1/[k(k-1)]$$ of the total.

AS we have $$\chi_{\Gamma_1}(k)$$ ways to colour $$\Gamma_1$$, and then $$\frac{1}{k(k-1)}\chi_{\Gamma_2}(k)$$ ways to extend the colouring to all of $$\Gamma$$, we have the result. $$\square$$