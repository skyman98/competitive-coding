

## Minimum number of jump

> we have a non-negative integer of the array and our task is to find a minimum number of jumps required to reach the last element of the array.

**input: [ 3 4 2 1 2 3 7 1 1 1 3 ]**
**output: 4 	// 3 -> 4/2 -> 2 -> 7 -> end**

## Method:

> we have initial maximum step=arr[0] so we first go through all step from current position to current+arr[0] position.  select maximum of
 it and repeat same process.

**code:**

    def minNumberOfJumps(arr):
    	sz=len(arr)
    	if sz==1:
    		return 0
    	maxval=arr[0]
    	step=arr[0]
    	jump=0
    	for i in range(1,sz-1):
    		maxval=max(maxval,i+arr[i])
    		step-=1
    		if step==0:
    			step=maxval-i
    			jump+=1
    	return jump+1


Time: O(n)
space: O(1)
