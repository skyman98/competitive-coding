

## Minimum Height Trees

> A tree is an undirected graph in which any two vertices are connected by _exactly_ one path. In other words, any connected graph without simple cycles is a tree.
 
> Given a tree of n nodes labeled from 0 to n - 1, and an array of n - 1 edges where edges[i] = [ai, bi] indicates that there is an undirected edge between the two nodes ai and bi in the tree, you can choose any node of the tree as the root. When you select a node x as the root, the result tree has height h. Among all possible rooted trees, those with minimum height (i.e. min(h)) are called **minimum height trees** (MHTs).
 
> Return _a list of all_ **_MHTs'_** _root labels_. You can return the answer in **any order**.
  
> The **height** of a rooted tree is the number of edges on the longest downward path between the root and a leaf.

 
> **Constraints:**
 
> -   1 <= n <= 2 * 104
> -   edges.length == n - 1
> -   0 <= ai, bi < n
> -   ai != bi
> -   All the pairs (ai, bi) are distinct.
> -   The given input is **guaranteed** to be a tree and there will be **no repeated** edges.

## Method :

> as we know that we need to take all nodes as root and after that, we need to find the minimum height of all trees and return all minimum height root node values.
 
> This approach Quite lengthy so we need to optimize it. 
 First, we know that degree of a leaf node is 1. so we apply this logic to our problem. we can create a graph from given data and we just remove all leaf nodes that have degree 1. so after that we have another small graph, repeat the same process until we get 2 or fewer no. of nodes.

  

**Code :**

    class Solution:
    
    def findMinHeightTrees(self, n: int, arr: List[List[int]]) -> List[int]:
    
    if n<=2 :
    
    return [i for i in range(n)]
    
    graph=[set() for i in range(n)]
    
    for i,j in arr:
    
    graph[i].add(j)
    
    graph[j].add(i)
    
    leaf=[]
    
    for i in range(n):
    
    if len(graph[i])==1:
    
    leaf.append(i)
    
    available_node=n
    
    while available_node>2:
    
    available_node-=len(leaf)
    
    new_leaf=[]
    
    while leaf:
    
    temp_leaf=leaf.pop()
    
    temp_g = graph[temp_leaf].pop()
    
    graph[temp_g].remove(temp_leaf)
    
    if len(graph[temp_g])==1:
    
    new_leaf.append(temp_g)
    
    leaf=new_leaf
    
    return leaf

  

  

**This Approach Take O(V) Time and O(V) Space.**
