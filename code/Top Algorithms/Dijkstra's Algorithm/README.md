

## Dijkstra's Algorithm

> This is the most popular algorithm in dynamic programming. In this Question, we have one list of list that contains pairs (destination, distance). and one integer value that is the start of the traveling point.
 
> size of the list denotes the no of a node in the graph, for each graph, there are several pair which denotes connection to other node and also the distance between them.

> so, our task is to find the minimum distance from the START node to all other nodes starting with a minimum distance.

**Input : 
{ "start": 0, 
 "edges": [ [ [1, 7] ], [ [2, 6], [3, 20], [4, 3] ], [ [3, 14] ], [ [4, 2] ], [], [] ] 
}**

**Output : [0, 7, 13, 27, 10, -1]** 
**here starting node is 0 so first distance is 0.**

## Method :

> as we know that if we have less no. of nodes then we can directly use brute force to solve this type of question, but if we have thousands of nodes then it's difficult to solve this problem.
 
> So we can solve using Dijkstra's Algorithm.  so first we can create a visited list that stores value for visited data. So we can use While( visited < size ) this loop takes O(v). In this loop, we can get the first minimum node from starting node. that will also require O(v) time. after this we can update distance for a node that will outgoing link from current node that will take time O(E) here we can have E edge and all edge can travel only one time.
  So total time complexity is O( V^2 + E ) and Space complexity O(V)

**Basic Code :
 	Arrays= [ 0 ,7 , inf , inf ,inf , inf ]
	visited={} 
	While( len(visited) < size of node ) :  => O(V)
		find node with min value :	=> O(V)
			for each edge in list of connections:	=> O(E)
				*update distance***

***Code :*** 

    def get_min_vertex(distance,visited):
    	curr=float("inf")
    	vertex= -1
    	
    	for inx,dis in enumerate(distance):
    		if inx in visited:
    			continue
    		if dis <= curr:
    			vertex=inx
    			curr=dis
    	return vertex,curr
    	
    	
    def dijkstrasAlgorithm(start, edge):
        # Write your code here.
    	sz=len(edge)
    	visited=set()
    	min_dis=[float("inf") for _ in range(sz)]
    	min_dis[start]=0
    	
    	while len(visited) != sz:
    		
    		vertex , curr = get_min_vertex(min_dis,visited)
    		
    		if curr == float("inf"):
    			break
    		visited.add(vertex)
    		
    		for ele in edge[vertex]:
    			desti,dis_val = ele
    			
    			if desti in visited:
    				continue
    			
    			new_dis = curr + dis_val
    			
    			curr1=min_dis[desti]
    			if new_dis < curr1:
    				min_dis[desti]=new_dis
        
    	for i in range(sz):
    		if min_dis[i]==float("inf"):
    			min_dis[i]=-1
    	
    	return min_dis

## Can we optimize the Above method?

> The answer is yes,  How? in the second step, finding a minimum value takes O(n) time when we use Arrays as Data Structure, but if we use Heap then it will be reduced to log(n) so we can get better time complexity. this approach takes time O( (V + E) * log(V) )

**Basic Code :
 	Heap creation => min HEAP()
	visited={} 
	While( len(visited) < size of node ) :  => O(V)
		find node with min value :	=> O(log(V))
			for each edge in list of connections:	=> O(E)
				*update distance***

