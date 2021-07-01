

## Max Subset-sum with No adjacent

> In this Que, we have one non-negative integer array. we need to find the maximum sum of subset elements with no adjacent. 
> 
> input : [75, 105, 120, 75, 90, 135]
>  output : 	330		 // 75+120+135

**Code :**

    def maxSubsetSumNoAdjacent(arr):
        sz=len(arr)
    	if sz==0:
    		return 0
    	elif sz==1:
    		return arr[0]
    	last=arr[0]
    	first=max(arr[0],arr[1])
    	for i in range(2,sz):
    		curr=max(first,last+arr[i])
    		last=first
    		first=curr
    	return first

**Time:O(n)**
**Space:O(1)****
