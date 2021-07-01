

## Number of ways to make change

> In this Que, we have one integer array that represents different coin values and one target value. Our task is to find how many ways we can make target value using given coins. also, we have an infinite number of coins for each value.

**sample:**

> coin: [ 1 , 5 ]
>  n= 6 
>   output: 2  => (1 * 5 + 1 *1 ) and (6*1 )

## Method :

> let's try to create all numbers from 0 to n using all different coin
![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/5.jpeg)
> 
> now if we choose 2, so we directly update 2 to n. below 2 is not possible using coin2. when we have n=4 and coin=2 then we have the following possibility  :  [ 1+1+2, 2+2, 1+1+1+1 ] so we have 3 ways.

 
**how these 3 ways come??**

> we have already 1 way which is ( 1+1+1+1)  now we have coin value 2, so how many ways we can create 4 using coin 2 => (2+2) in this case we also have one condition that how many ways we can create 2 using coin 1 and 2 => (1+1, 2) we can say that we create 4 using 3 ways.

**if you have still doubt please refer to the below code that will give you a clear idea.** 

## code:

    def numberOfWaysToMakeChange(n, denoms):
    	way=[0 for ele in range(n+1)]
    	way[0]=1
    	for coin in denoms:
    		for curr in range(1,n+1):
    			if coin <= curr:
    				way[curr]+=way[curr-coin]
    	return way[n]

**Space: O(n)**
**Time: O(n*m)**
**n=target value and m=no. of given coin**

