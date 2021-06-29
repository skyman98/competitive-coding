

## Topological Sort

> In This Question, we have two lists jobs and deps. In Jobs, we have no. of nodes in topological sort. In deps, we have dependencies pair [x,y] (y depend on x ) (x complete if and only if when y completed )
 
> Input: Jobs: [ 1 , 2 ,3 ,4 ] Deps: [ [1,2] [1,3] [3,2] [4,2] [4,3] ] A
> Diagram of this input is :
![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/1.jpeg)

## Method :

> we first travel one node whose dependency is zero. In the above case, we have two nodes whose dependency is zero (1 and 4 ) we can take any of this, so we choose 1. when we visited node 1 then we need to remove its dependency from the graph so we can get it as below. we repeat this process till we get all nodes visited. 
> ![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/2.jpeg)

 
 
 **is there all condition covered?** 
> No, suppose we have a graph like below then we have some blocking mechanism like a deadlock. 
 ![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/3.jpeg)
> In This case, we have a Cycle that means we have detected dead state so we need to break our algorithm, we run the above algorithm till we get ( dependency == zero ) if not then we return an empty list;
 
> So how we can implement the above logic ??
 
> we can create two lists (graph, graph2 ) graph => store key-value pair where the key is node value and values are node values, where key depend on those node values. Graph2 => store key-value pair where the key is node value and values are node values who depend on this key

**Code :**

    def topologicalSort(jobs, deps):
        graph={}
    	graph2={}
    	ans=[]
    	n=0
    	sz=len(jobs)
    	for ele in jobs:
    		graph[ele]=[]
    		graph2[ele]=[]
    	for ele in deps:
    			graph[ele[1]].append(ele[0])
    			graph2[ele[0]].append(ele[1])
    	
    	while n<sz:
    		temp=min(graph, key=graph.get)
    		if(len(graph[temp])!=0):
    			return []
    		
    		for ele in graph2[temp]:
    			graph[ele].remove(temp)
    		del graph2[temp]
    		del graph[temp]
    		n+=1
    		ans.append(temp)
        return ans



