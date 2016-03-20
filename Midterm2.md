# Midterm 2 Sample Questions

## Question 2 
Suppose that we are given an instance of the Minimum Spanning Tree Problem on a graph G which has
positive distinct edge costs. Let T be a minimum (cost) spanning tree for G. Now we make a new graph G’
which is almost exactly G, with the only exception that the edge costs are squared. (In other words: each
edge e of G having edge cost c-e appears in G’ as an edge with edge cost c-e2 and there is no other edge in G’).
Question: Must T be still a minimum spanning tree for G’?
Answer: (Yes/No):
Why: (Explain)

## Solution 2
True, squaring the weights of the edges in a weighted graph will not change the minimum spanning tree. Assume the opposite to obtain a contradiction. If the minimum spanning tree changes then at least one edge from the old graph G in the old minimum spanning tree T must be replaced by a new edge in tree T' from the graph G' with squared edge weights. The new edge from G' must have a lower weight than the edge from G.
This implies that there exists some weights C1 and C2 such that C1 < C2 and C12 >= C22. This is a contradiction.</br>
http://www.cs.nyu.edu/courses/spring06/V22.0310-001/hw3.htm

## Question 3
You are supposed to determine whether there is a path of length K or less from a given starting point to
the given end point in a 2D maze. Can this problem solved efficiently? How would you solve this problem? 

## Solution 3
To find a path instead of the shortest path, use any graph traversal (e.g. depth-first or best-first). It won't necessarily be faster, in fact it may check many more nodes than A* on some graphs, so it depends on your data. However, it will be easier to implement and the constant factors will be significantly lower.

To avoid search for a path when there is none, you could create disjoint sets (once after you built the graph) to very quickly check whether two given points are connected. This takes linear space and linear time to build, and lookup takes amortized practically-constant time, but you still need to run your full algorithm at times, as it will only tell you whether there is a path, not where that path goes.</br>
https://www.cs.bu.edu/teaching/alg/maze/
http://stackoverflow.com/questions/15508370/ai-fastest-algorithm-to-find-if-path-exists



