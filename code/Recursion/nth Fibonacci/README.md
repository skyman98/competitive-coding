## nth Fibonacci

> We can use recursion and get answer but this will take O(2^n) time.
 
> we use Dynamic approach, and store all value in one memory.
 
> so it will take O(n) time.

**Code:**

    def fib(n,memo={}):
    	if n==1:
    		return 0
    	elif n==2:
    		return 1
    	else:
    		if n in memo.keys():
    			return memo[n]
    		else:
    			memo[n]=fib(n-1,memo) + fib(n-2,memo)
    			return memo[n]
    def getNthFib(n):
        return fib(n)

