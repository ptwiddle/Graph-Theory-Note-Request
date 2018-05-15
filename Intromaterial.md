---
layout: page
title: Introduction
permalink: /Introduction/
---

Graphs
---

Graphs usually (but not always) are thought of showing how things are set of things are connected together.

Definition of a graph
===

A *graph* \\(\Gamma\\) consists of: 

- a set \\(V(\Gamma)\\) of vertices 
- a set \\(E(\Gamma)\\) of edges 

Each edge either connects two vertices of \\(V(\Gamma)\\) together, or connects a vertex to itself.

Examples
===

See the slides for many picture examples, but here are some common examples:

-  cities as vertices and roads connecting them as edges
- people as vertices and an edge between two people if they know each other
- atoms in a molecule as vertices, with an edge between them if they are connected by a covalent bond
- countries on a map as vertices, and shared borders as edges


A few more definitions
===

There are two features of graphs that are sometimes convenient to not allow.  

A *loop* is an edge that connects a vertex to itself, and a *multiple edge* is when there is more than one edge connecting the same two vertices.  A graph without these features is called *simple*.  

We say two vertices are *adjacent* if there is an edge between them.

The *degree* or *valency* of a vertex in a simple graph is the number of vertices it is adjacent to.

A first question
----

Suppose you are at a party with six other people, so that there are seven people total at the party.  Is it possible that everybody knows exactly three other people at the party?

To translate this into graph theory, we make the people vertices, and put an edge between two people if they know each other.  We are then asking if a graph exists with seven vertices, where each vertex has degree three.

It turns out that this is not possible; one way to prove this would be doing a case by case analysis of trying to make such a graph, but such proofs are usually long, messy, and not particularly enlightening.  

Instead, we argued as follows: suppose that everyone at the party shook hands with the people they knew, but not with the people they don't know.  How many handshakes would occur?

It is immediate from the definition that the number of handshakes would be the number of edges in the graph.  But we could also count the number of handshakes in another way: each person is going to shake hands three times, so people will be involved in handshakes 3*7=21 times.  But since each handshake involves two people, this should be twice the number of handshakes.  From this reasoning, we see there should be 21/2=10.5 edges in the graph, which is absurd, and so we see that such a party is not possible.

The argument given above easily generalizes to give

Euler's handshaking lemma:
====
The sum of the degrees of the vertices of a graph is twice the number of edges of the graph:

$$\sum_{v\in V(\Gamma)}d(v)=2|E(\Gamma)|$$

Proof:
===
Each edge has two ends; each end contributes 1 to the degree of one vertex, and hence to the sum of all the degrees.  \\(\square\\)

Graph theory in Chemistry
----

In organic chemistry, atoms are joined together by covalent bonds; we represent this in a graph with the atoms as vertices and the edges representing the bonds.  The location of the element on the periodic table determines the valency of the vertices corresponding to that element:
 
- Hydrogen (H) and Fluorine (F) have degree 1
- Oxygen (O) and Sulfur (S) have degree 2 
- Nitrogen (N) and Phosphorous (P) have degree 3 
- Carbon (C) has degree 4 

Usually, most of the atoms involved are carbon and hydrogen.  Carbon atoms are not labelled with a C, but just left blank, while hydrogen atoms are left off completely.  One can then complete the full structure of the molecule using the valency of each vertex.

Graphs coming from organic chemistry do not have to be simple -- sometimes there are double bonds, where a pair of carbon atoms have two edges between them.

Definition: degree sequence
====
The *degree sequence* of a graph is just the list (with multiplicity) of the degrees of all the vertices.  

So, knowing the chemical composition of a molecule determines the degree sequence of its corresponding graph.  However, it is possible that the same set of atoms may be put together into a molecule in more than one different ways.  In terms of graphs, this corresponds to "different" graphs that have the same degree sequence.



Instant Insanity
---

A concrete, nontrivial application of graph theory is as a tool to solve the puzzle ``instant insanity'', known sometimes as the four cubes problem.

Basic setup
===

In this puzzle, one is given four cubes.  Each face of each cube is painted one of four different colours: blue, green, red or yellow.  The goal is to line the four cubes up in a row, so that along the four long edges (front, top, back, bottom) each of the four colours appears eactly once.

Depending on how the cubes are coloured, this may be not be possible, or there may be many such possibilities.  In the original instant insanity, there is exactly one solution.  I have made a <a href="https://www.youtube.com/watch?v=GsbhRfjaaN8">video</a> that explains how to use graph theory to show the solution to the original onstant insanity.

There are many variations on Instant Insanity, discussion of which can be found, for [here](http://www.cs.brandeis.edu/~storer/JimPuzzles/ZPAGES/zzzInstantInsanity.html) and [here](http://www.jaapsch.net/puzzles/insanity.htm).  There's also [a commercial](https://www.youtube.com/watch?v=CQ2gHSKZBEw) for the game. 


An impossible example
---

In lecture, I walked through proving that the following example has no solutions.  The work was done on the board and not in the slides, but I will present the work here.

The four cubes in question are:

<image src="../Slides/Pictures/ImpossibleCubes.png"></image>

Enter graph theory
===

We will now construct a graph that encodes the important part of the structure of the cubes. 

The vertices of the graph will be the four colors, B, G, R and Y.  We will put an edge between two colors each time they appear as opposite faces on a cube, and we will label that edge with a number 1-4 denoting which cube the two opposite faces appear.  So from the first cube, there will be a loop at B, and edge between G and R, and an edge between Y and R.

The graph corresponding to the four cubes above is the following:

<image src="../Slides/Pictures/InstantInsanityImpossibleGraph.JPG"></image>


Proving our cubes were impossible
===

How does this graph help us study the solutions of the Instanity Insanity puzzle?  Suppose we had an arrangement of the cubes that was a solution.  Then, from each cube, pick the edge representing the colors facing front and back on that cube.  These four edges are a subgraph of our original graph, with one edge of each label, since we picked one edge from each cube.  Furthermore, since we assumed the arrangement of cubes was a solution of instant insanity, each color appears once on the front face and once on the back.  In terms of our subgraph, this translates into asking that each vertex has degree two.  

We got another subgraph satisfying these two properties by looking at the faces on the top and bottom for each cube and taking the corresponding edges.  Furthermore, these two subgraphs do not have any edges in common.

Thus, given a solution to the instant insanity problem, we found a pair of subgraphs $$S_1, S_2$$ satisfying:

1. Each subgraph $$S_i$$ has one edge with each label 1,2,3,4
2. Every vertex of $$S_i$$ has degree 2
3. No edge of the original graph is used in both $$S_1$$ and $$S_2$$

As an exercise, one can check that given a pair of subgraphs satisfying 1-3, one can produce a solution to the instant insanity puzzle.

Thus, to show the set of cubes we are currently examining does not have a solution, we need to show that the graph does not have two subgraphs satisfying properties 1-3.

To do, this, we catalog all graphs satisfying properties 1-2.  If every vertex has degree 2, either 

1. Every vertex has a loop
2. There is one vertex with a loop, and the rest are in a triangle
3. There are two vertices with loops and a double edge between the other two vertices
4. There are two pairs of double edges
5. All the vertices live in one four cycle

A subgraphs of type 1 is not possible, because G and R do not have loops.

For subgraphs of type 2, the only triangle is G-R-Y, and B does have loops.  The edge between Y-G must be labeled 3, which means the loop at B must be labeled 1.  This means the edge between G and R must be labeled 4 and the edge between Y and R must be 2, giving the following subgraph:

<a href="http://www.presheaf.com/?d=d4oj3rb54s1o455d3y411052m3sm"><img src="http://presheaf.com/cache/d4oj3rb54s1o455d3y411052m3sm.png" title="click to go to presheaf.com for editing"/></a>

For type 3, the only option is to have loops at B and Y and a double edge between G and R.  We see the loop at Y must be labeled 2, one of the edges between G and R must be 4, and the loop at B and the other edge between G and R can switch between 1 and 3, giving two possibilities:

<a href="http://www.presheaf.com/?d=d4q2c25256yh02f391k2uwf95r4x"><img src="http://presheaf.com/cache/d4q2c25256yh02f391k2uwf95r4x.png" title="click to go to presheaf.com for editing"/></a>

and

<a href="http://www.presheaf.com/?d=d1x1h4f1nv494b64t68504rc12nd"><img src="http://presheaf.com/cache/d1x1h4f1nv494b64t68504rc12nd.png" title="click to go to presheaf.com for editing"/></a>


For subgraphs of type 4, the only option would be to have a double edge between B and G and another between Y and R; however, none of these edges are labeled 3 and this option is not possible.

Finally, subgraphs of type 5 cannot happen because B is only adjacent to G and to itself; to be in a four cycle it would have two be adjacent to two vertices that aren't itself.

This gives three different possibilities for the subgraphs $$S_i$$ that satisfy properties 1 and 2.  However, all three possibilities contain the the edge labeled 4 between G and R; hence we cannot choice two of them with disjoint edges, and the instant insanity puzzle with these cubes does not have a solution.




Isomorphisms: When are two graphs "the same"?
-----

It is possible to draw the same graph in the plane in many different ways -- e.g., the pentagon and the five sided star are two different ways of drawing $$C_5$$.  

If two graphs are "the same" in this way, we say they are *isomorphic*.

Definition
====

An *isomorphism* $$\varphi:G\to H$$ of simple graphs is a bijection $$\varphi:V(G)\to V(H)$$ that preserves the number of edges between vertices.  That is, if $$v,w\in V(G)$$, then the number of edges between $$v$$ and $$w$$ in $$G$$ is equal to the number of edges between $$\varphi(v)$$ and $$\varphi(w)$$ in $$H$$.


Example
====

This animated gif shows several graphs isomorphic to the Petersen graph, and demonstrates that they are isomorphic:

<image src="../Slides/Pictures/PetersenIsomorphismAnimated.gif"></image>

Graph isomorphism problem
---

The *graph isomorphism problem* is to decide whether or not two given graphs $$G, H$$ are isomorphic.  

General discussion for mathematical cultural literacy
===

The isomorphism problem is of fundamental importance to theoretical computer science. Apart from its practical applications, the exact difficulty of the problem is unknown.  Clearly, if the graphs are isomorphic, this fact can be easily demonstrated and checked, which means the Graph Isomorphism is in NP.  

Most problems in NP are known either to be easy (solvable in polynomial time, P), or at least as difficult as any other problem in NP (NP complete).  This is not true of the Graph Isomorphism problem.   In November of last year, Laszlo Babai announced a quasipolynomial-time algorithm for the graph isomorphism problem -- you can read about this work in [this great popular science article](https://www.quantamagazine.org/20151214-graph-isomorphism-algorithm/).

What you have to be able to do
====

Although solving the graph isomorphism problem for general graphs is quite difficult, doing it for small graphs by hand is not too bad and is something you must be able to do for the exam.

If the two graphs are actually isomorphic, you have to actually write down an explicit isomorphism $$\varphi:G\to H$$ should be given.  

 If they are not isomorphic, you have to prove that they are not isomorphic.  Usually this is done by giving an *obstruction* -- something that is different between the two graphs.  One easy example is that isomorphic graphs have to have the same number of edges and vertices.  

Another, only slightly more advanced invariant is the degree sequence of a graph that we saw last lecture in our discussion of chemistry.

If $$\varphi:G \to H$$ is an isomorphism of graphs, than we must have $$d(\varphi(v))=d(v)$$ for all vertices $$v$$, and so the degree sequence must be preserved.  However, just because two graphs have the same degree sequences does not mean they are isomorphic.

