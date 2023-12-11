# CMPS 2200 Assignment 5
## Answers

**Name:** Charlie Landman






- **1a.**
in a d-ary heap, each level can have at most $d^i$ nodes starting from level 0. So, the way to find the maximum depth is when the number of nodes at level h is less than d. ((d^h+1)-1)/d-1 < d.

By solving this inequality, the maximum depth is h = 2- (1/d) +(1/(d^2)) - 1

- **1b.**
work of delete-min = O(d log_d n) where n is the number of nodes in the heap
work of insert = O(log_d n)

- **1c.**
new bound on work : O((|V|d + |E|) log_d |V|)


- **1d.**
d = |V|^epsilon

- **2a.**
$\mathit{APSP}(0,1,2) = -2

$\mathit{APSP}(0,1,1) = -2

$\mathit{APSP}(0,1,0) = -2

$\mathit{APSP}(0,2,2) = -1

$\mathit{APSP}(0,2,1) = -1

$\mathit{APSP}(0,2,0) = 2

$\mathit{APSP}(1,2,2) = 0

$\mathit{APSP}(1,2,1) = 0

$\mathit{APSP}(1,2,0) = 1


- **2b.**
yes, there is a relationship. Because its such a small graph, the 3rd vertex doesn't create any new shortest path. The relationship is $\mathit{APSP}(i,j,2) = min($\mathit{APSP}(i,j,1), $\mathit{APSP}(i,2,1) + $\mathit{APSP}(2,j,1))

- **2c.**
  $\mathit{APSP}(i,j,k)=Min($\mathit{APSP}(i,j,k-1), $\mathit{APSP}(i,k,k-1) + $\mathit{APSP}(k,j,k-1))

- **2d.**

the amount of unique subproblems is n^3. As such, the work is O(n^3)

- **2e.**
Johnson's algorithm's work is O(|V||E|log|E|) and our work is (in terms of vertexs and edges) O(n^2 logn +nE), which means that our algorithm is only more optimal when E is closer in value to n^2.


- **3a.**
A solution to MST isn't garunteed because it doesn't care about the value of the max edge weight. 

- **3b.**
First, we find the best tree using any method available to us using MST.

Then, we look at the edges that were used to create this best tree and keep track of the order they were added.

Starting from the heaviest edge in this best tree, we remove one edge at a time and try to create a new tree without it.

Each time we remove an edge, we use any method to find a new tree without that edge. Repeat this process for each removed edge.

As we create new trees, compare them to the best tree we originally found. If we find a tree with a lower total edge weight than the best tree, we update our "next best tree" to be this one.

Finally, after checking all the removed edges and creating alternative trees, we end up with the tree that has the next lowest total edge weight after the best tree.

- **3c.**
O(E^2 log V)