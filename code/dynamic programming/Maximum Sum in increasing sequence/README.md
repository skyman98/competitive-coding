

## Maximum Sum in increasing sequence

> In This Question, we have one array as input and our task is to find the max sum in increasing order.

## Method:
![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/6.jpeg)

![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/7.jpeg)


**Code:**

    def maxSumIncreasingSubsequence(arr):
        sz=len(arr)
    	seq=[None for ele in arr]
    	add=[ele for ele in arr]
    	maxid=0
    	for i in range(sz):
    		curr=arr[i]
    		for j in range(i):
    			temp=arr[j]
    			if temp < curr and add[j] + curr >= add[i] :
    				add[i]=add[j] + curr
    				seq[i]=j
    		if add[i] >= add[maxid]:
    			maxid=i
    	ans=[]
    	val=maxid
    	while maxid is not None:
    		ans.append(arr[maxid])
    		maxid=seq[maxid]
    	ans.reverse()
    	return [ add[val], ans]

**Time: O(n^2)**

**Space: O(n)**
