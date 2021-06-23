

## Smallest Difference

> In this Question, we have two arrays and Our task is to find the smallest difference pair from both arrays.

## Method:

> this problem looks very simple but actually, it is not. first, 

> we sort both arrays, after that, we set two index pointer that point elements of both arrays. if the addition of this pointer is smaller then we increase those array pointer whose element is minimum.
 
> if it is equal to zero then direct return those pointer values.

**Code:** 

    def smallestDifference(arr1, arr2):
        arr1.sort()
    	arr2.sort()
    	inx1=0
    	inx2=0
    	ans=[0,0]
    	diff=float("inf")
    	temp=float("inf")
    	while inx1<len(arr1) and inx2<len(arr2):
    		num1=arr1[inx1]
    		num2=arr2[inx2]
    		if num1<num2:
    			temp=num2-num1
    			inx1+=1
    		elif num1>num2:
    			temp=num1-num2
    			inx2+=1
    		else:
    			return [num1,num2]
    		if temp < diff :
    			diff=temp
    			ans=[num1,num2]
    	return ans

**Time :O(N logN + M logM )
Space:O(1)**
