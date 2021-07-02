

## Levenshtein distance algorithm

> We have 2 strings as input, our task is to find the edit distance of these strings. 

> input : 
>  str1=" abc " 
>  str2=" yabd " 

>  output: 2

## Method :

> we create the m*n matrix and update the value in this matrix using the Levenshtein distance algorithm.

![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/8.png)

**Code:**

    def levenshteinDistance(str1, str2):
        lev=[ [ x for x in range(len(str1) + 1)] for y in range(len(str2)+1)]
    	sz1=len(str1)
    	sz2=len(str2)
    	for i in range(1,sz2+1):
    		lev[i][0]=1 + lev[i-1][0]
    	for i in range(1,sz2+1):
    		for j in range(1,sz1+1):
    			if str2[i-1]==str1[j-1]:
    				lev[i][j]=lev[i-1][j-1]
    			else:
    				lev[i][j]=1 + min(lev[i-1][j],lev[i][j-1],lev[i-1][j-1])
    	return lev[-1][-1]


**Time: O(m*n)**
**Space: O(m*n)**
