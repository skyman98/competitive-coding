

## Three number sum

> In this Question, we have one array and one target value. our task is to find all possible 3 ints from an array whose sum is equal to the target value.

## Method :

> if we can use 3 for loops then we have all possible parts of the array but this method takes O(n^3) time which is Quite a lengthy process.

**So CAN WE SOLVE THIS PROBLEM IN O(N^2) TIME?**

> yes, we can do this.

>  first, we travel all nodes one by one, during this we can set one left and one right pointer that is move according to condition.  first, we have one element, we have one left and right pointer, so all overtime is O(n^2).

**Code :**

    def threeNumberSum(arr, target):
        # Write your code here.
    	arr.sort()
    	ans=[]
    	sz=len(arr)
    	for i in range(sz-2):
    		left=i+1
    		right=sz-1
    		while left < right :
    			temp=arr[i]+arr[left]+arr[right]
    			if temp < target :
    				left+=1
    			elif temp > target :
    				right-=1
    			else:
    				ans.append([arr[i],arr[left],arr[right]])
    				left+=1
    				right-=1
        return ans


