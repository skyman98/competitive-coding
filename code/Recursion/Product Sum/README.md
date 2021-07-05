## Product Sum:

![enter image description here](https://github.com/skyman98/competitive-coding/blob/main/img/productSum.png)

Code :

    def productSum(arr,d=1):
    	add=0
        for ele in arr:
    		if type(ele) is list:
    			add += productSum(ele,d+1)
    		else:
    			add += ele
    	return add*d

