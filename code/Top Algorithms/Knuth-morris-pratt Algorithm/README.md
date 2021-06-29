

## Knuth-morris-pratt Algorithm

> In this Question, we have one String  First and one substring Second as input. Our task is to check whether this substring second is a Substring of the string first or not.

## Method:

> when we see this Question, we start solving this problem with two for loops and check every point. But when we have a very large string then find substring is a difficult task, this method takes Time O(N * M ),
 N=length of origin string M=length of Substring.
 
> So how we can optimize this thing ????  when we use the above method, every time we check all characters of the string we don't find any pattern in this string. if we find any pattern in this string then our task is easy.
 
> first, we create one array that stores information about the pattern of a substring. we take two-pointer j=0 and i=1 that indicates the index of an array whose size is equal to substring and default values are -1.


![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/4.jpeg)


**Code:**

    def gen_pattern(subarr,sz):
    	pattern=[-1 for i in subarr]
    	i=1
    	j=0
    	while i < sz:
    		if subarr[i] == subarr[j]:
    			pattern[i]=j
    			i+=1
    			j+=1
    		elif j>0:
    			j=pattern[j-1]+1
    		else:
    			i+=1
    	return pattern
    
    def knuthMorrisPrattAlgorithm(arr, subarr):
        szarr=len(arr)
    	szsubarr=len(subarr)
    	pattern=gen_pattern(subarr,szsubarr)
    	i=0
    	j=0
    	while i<szarr :
    		if arr[i]==subarr[j]:
    			i+=1
    			j+=1
    			if j==szsubarr:
    				return True
    		elif j>0:
    			j=pattern[j-1]+1
    		else:
    			i+=1
        return False


**Time: O( n + m )
Space: O( m )**





