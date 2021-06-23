

## Longest Peak

> In this Question, we have one array and we need to find the longest peak value if it is not then return 0. 
 
> Peak: the peak is nothing but ( - + - ) which means we have one point and its adjustable elements are strictly less than that elements.
 

## Method :

> first, we find one peak point in the array. after that, we can increase its length from both directions and we get the length of it. from all peak lengths, we return maximum length.
 
> see Code you will get a better idea about it :)

**Code :**

    def longestPeak(arr):
        # Write your code here.
    	longdistance=0
    	inx=1
    	sz=len(arr)
    	while inx < sz-1:
    		ispeak = arr[inx-1] < arr[inx] and arr[inx+1] < arr[inx]
    		
    		if not ispeak:
    			inx+=1
    			continue
    		left=inx-2
    		while left >= 0 and arr[left] < arr[left+1]:
    			left-=1
    		right=inx+2
    		while right < sz  and arr[right-1] > arr[right]:
    			right+=1
    		temp=right-left-1
    		#print(temp)
    		if temp > longdistance:
    			longdistance=temp
    		inx=right
    		
        return longdistance

****Time : O(n)
Space :O(1)****



