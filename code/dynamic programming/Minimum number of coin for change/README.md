

## Minimum number of coin for change

**This is a similar Question to this link.**
[similar Question](https://github.com/skyman98/competitive-coding/blob/main/code/dynamic%20programming/Number%20of%20ways%20to%20make%20change/README.md)

**we just need to find minimum value from all possible ways.**

## Code :



    def minNumberOfCoinsForChange(n, arr):
        ways=[float('inf') for i in range(n+1)]
    	ways[0]=0
    	for coin in arr:
    		for curr in range(1,n+1):
    			if curr >= coin:
    				ways[curr]=min(ways[curr],ways[curr-coin] + 1)
    	if ways[n]==float('inf'):
    		return -1
    	else:
    		return ways[n]

