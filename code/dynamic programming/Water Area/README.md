## Water Area

> In this Question, we have one non-negative integer array. This value of the array represents pillar height. Our task is to find how much area of water store in this pillar. for more clarity refer to the below image.
![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/9.jpg)

## method:

> as we see in the image if we have the maximum length of the pillar then we need to travel both sides of it (left and right ). we start with both directions till we get the maximum value. if we found the max value from the left we change the left max value and update the area. same process for right part

 

**Code:**

    def waterArea(arr):
    	if len(arr)<=1:
    		return 0
    	left=0
    	right=len(arr)-1
    	leftmax=arr[left]
    	rightmax=arr[right]
    	area = 0
    	while(left < right) :
    		if arr[left] < arr[right]:
    			left+=1
    			leftmax=max(leftmax,arr[left])
    			area += leftmax - arr[left]
    		else:
    			right-=1
    			rightmax=max(rightmax,arr[right])
    			area += rightmax - arr[right]
    	return area

Time: O(n)
Space: O(1)


