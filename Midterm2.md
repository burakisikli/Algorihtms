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
Yes, to find a path instead of the shortest path, use any graph traversal (e.g. depth-first or best-first). It won't necessarily be faster, in fact it may check many more nodes than A* on some graphs, so it depends on your data. However, it will be easier to implement and the constant factors will be significantly lower.

To avoid search for a path when there is none, you could create disjoint sets (once after you built the graph) to very quickly check whether two given points are connected. This takes linear space and linear time to build, and lookup takes amortized practically-constant time, but you still need to run your full algorithm at times, as it will only tell you whether there is a path, not where that path goes.</br>
https://www.cs.bu.edu/teaching/alg/maze/</br>
http://stackoverflow.com/questions/15508370/ai-fastest-algorithm-to-find-if-path-exists

## Question 4
You are given problem X defined below.
Problem X: Given a sequence of N numbers: a1, a2, . . . , aN , what is the length of the Longest nondecreasing
Subsequence? Note that a subsequence is different from substring and need not be consecutive.
Example: The length of the longest non-decreasing subsequence of [1,8, 6, 7, 9, 1] is 4; because, as we scan the
list from left to right we can pick numbers that obey the non-decreasing constraint to make the subsequence
[1,6,7,9] and there is no longer subsequence that obeys the non-decreasing constraint.
Answer the following considering this definition: Let S[j] as the length of the longest non-decreasing subsequence which ends in aj.

## Solution 4
Se LIS.c

Dynamic programming Vazirani, page 170</br>
for j = 1, 2, . . . , n:
L(j) = 1 + max{L(i) : (i, j) ∈ E}
return maxj L(j)

https://www.hackerrank.com/challenges/longest-increasing-subsequent</br>
http://www.geeksforgeeks.org/construction-of-longest-monotonically-increasing-subsequence-n-log-n/</br>

## Question 5
Design a Dynamic Programming algorithm to solve the Maximum Sum Problem defined below,
and write the final solution as an O(n) iterative i.e. non-recursive pseudo-code.
Maximum Sum Problem: Given a sequence of n numbers: a1, a2, . . . , an , what is the maximum you can
obtain from a consecutive sum ai, ai+1...
Example: If the numbers are 2,4,-5,7,-3,8,-2 the answer is 12 (because of 7,-3,8).
(Note. Some numbers may be negative otherwise ...)
a) [1 pts] What is the brute force solution? Write a pseudo code (or Java code) to solve it and give its running
time.
b) [2pts] Design the DP algoritm.
Hint. Let Opt[k] denote the maximum that can be obtained by a consecutive subsequence sum that ends
exactly at index k. Then express Opt[k] recursively as we did in the class. 

## Solution 5
a) To find the subarray with the largest sum, we can easily come up with a brute force solution. That is, use three for loops to traverse through the array and compute the sum of each subarray. Each time we get a sum, we will update current maximum sum if the new sum is greater. So let Sum[i..j] be the sum of the ith element all through the jth element (0 <= i <= j < n). To traverse through all possible Sum[i..j], the time complexity would be O(N^3):

// This code fragment was a quote from Beauty of Programming
int MaxSum(int* A, int n)
{
    int maximum = -INF;
    int sum = 0;
    for (int i = 0; i < n; i++)
    {
        for (int j = i; j < n; j++)
        {
            for (int k = i; k <= j; k++)
            {
                sum += A[k];
            }
            if (sum > maximum)
                maximum = sum;
            sum = 0; // reset it to 0, or sum would be the sum of all subarrays.
        }
    }
    return maximum;
}

b) Let’s instead focus on computing OPT0
(n): the optimal sum of a subarray ending at A[n].
Consider whether A[n] is in the optimal solution:
– if so, then OPT(n) = OPT(n − 1) + A[n]
– if not, then OPT(n) = 0 (sum of the empty array)
Thus, we have a relation 
OPT(n) = max{OPT(n − 1) + A[n], 0}.

Max-Subarray-Sum(A, n)
16 opt ← 0, opt0 ← 0
17 for i ← 1 to n
18 do opt0 ← max{0, opt0 + A[i]}
19 opt ← max{opt, opt0}
20 return opt

https://courses.cs.washington.edu/courses/cse421/11su/slides/06dp-kevinz.pdf</br>
http://www.geeksforgeeks.org/largest-sum-contiguous-subarray/</br>
http://www.cse.ust.hk/~dekai/271/notes/L02/L02.pdf</br>
https://github.com/julycoding/The-Art-Of-Programming-By-July/blob/master/ebook/en/07.0.md
