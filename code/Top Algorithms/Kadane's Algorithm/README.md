## Kadane's Algorithm

> This algorithm is nothing but Sum of the Subset problem of Dynamic programming. we have one array of numbers and we need to find one subset which has a maximum value.

## Method 1:

> we can use For loops to solve this problem. In this method, we can use two for loops for range and 3rd loops for adding all elements in that range. this approach takes O(n^3) which is very high in time.

**Code:**

    int kadanesAlgorithm(vector<int> arr) {
      // Write your code here.
    	int ans=INT_MIN;
    	int sz=arr.size();
    	for(int i=0;i<sz;i++){
    		for(int j=i;j<sz;j++){
    			int sum=0;
    			for(int z=i;z<=j;z++){
    				sum=sum+arr[z];
    			}
    			if(sum>ans){
    				ans=sum;
    			}
    		}
    	}
      return ans;
    }

## Method 2:

> when we observe the Problem then we can find that there are some negative numbers that give decrease values, so we can add only some negative numbers which is useful. for that, we can use kadane's algorithm. we can travel all elements of the array, whenever we find the negative number we can check that if the current sunset is positive after adding this negative number then we can keep in answer, otherwise we can discard that number and move to the next subset.

**Code:** 

    #include <vector>
    using namespace std;
    
    int kadanesAlgorithm(vector<int> arr) {
      // Write your code here.
    	int ans=arr[0],curr=arr[0];
    	for(int i=1;i<arr.size();i++){
    		int num=arr[i];
    		curr=max(num,curr+num);
    		ans=max(ans,curr);
    	}
      return ans;
    }

