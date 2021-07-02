

## Number of ways to travel graph

> In this Question, we have two integers m and n, our task is to find how many ways possible between start and end start = top left end=bottom right

>  Input: n=2 m=3 
>  output=3

## Method:

> we can solve this problem recursively but the time complexity is 2^(n+m) which is very large.

**Code:**

    def numberOfWaysToTraverseGraph(width, height):
    	if width==1 or height==1:
    		return 1
    	
        return numberOfWaysToTraverseGraph(width-1, height) + numberOfWaysToTraverseGraph(width, height-1)

> so we can optimize this using dynamic programming. we use a memo dictionary as memorization. and store value instead of direct return.

**Code**

    def ways(w,h,memo):
    	val1=str(w)+','+str(h)
    	val2=str(h)+','+str(w)
    	if val1 in memo.keys():
    		return memo[val1]
    	if val2 in memo.keys():
    		return memo[val2]
    	if w==1 or h==1 :
    		return 1
    	memo[val2] = ways(w-1,h,memo)+ways(w,h-1,memo)
    	memo[val1]=memo[val2]
    	return memo[val2]
    	
    def numberOfWaysToTraverseGraph(width, height):
        return ways(width,height,{})


> 
> Here, we use val1 and val2 as key because 2*3 and 3*2 both have same answer.

