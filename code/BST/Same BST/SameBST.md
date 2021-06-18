**

## Same BSTs
**In this question we have two BSTs, we need to find that these two BSTs are the same or not?**
**BST1=[10,15,8,12,94,81,5,2,11]**
**BST2=[10,8,5,15,2,12,11,94,81]**
*so, if the order is different then also BSTs are the same as the above case.*
**Basic condition:**

 - both BSTsmust be the same size
 - both BSTs have the same element  at the root position
 - if both BSTs size is zero then return true.

**Method 1:**

>first, we check the basic condition and then split these BSTs into two parts ( smaller than root and greater than root ).
after that, we use recursion to solve this problem.

> In this method,  time complexity is O(n^2) and Space complexity 
is O(n^2)

    #include <vector>
    
    using namespace std;
    
    vector<int> partofVector(vector<int> arr,int temp); //temp=0 left part, temp=1 right part
    bool sameBsts(vector<int> arr1, vector<int> arr2) {
      // Write your code here.
    	if(arr1.size()!=arr2.size()){
    		return false;
    	}
    	if(arr1.size()==0){
    		return true;
    	}
    	if(arr1[0]!=arr2[0]){
    		return false;
    	}
    	vector<int> left1=partofVector(arr1,0);
    	vector<int> right1=partofVector(arr1,1);
    	vector<int> left2=partofVector(arr2,0);
    	vector<int> right2=partofVector(arr2,1);
      return sameBsts(left1,left2) && sameBsts(right1,right2);
    }
    
    vector<int> partofVector(vector<int> arr,int temp){
    	vector<int> part={};
    	if(temp){
    		for(int i=0;i<arr.size()-1;i++){
    			if(arr[i+1]>=arr[0])
    				part.push_back(arr[i+1]);
    		}
    	}
    	else{
    		for(int i=0;i<arr.size()-1;i++){
    			if(arr[i+1]<arr[0])
    				part.push_back(arr[i+1]);
    		}
    	}
    	return part;
    }

   **Method 2 :**

   

> first, we check the basic condition and then we find the index of the first minimum and first maximum elements from both BSTs.
at this both index(at min and max) , both elements (in BST1 and BST2) are must be same. and we recursively call this method till the depth of the tree
> 
>  In this method,  time complexity is O(n^2) and Space complexity 
is O(d) d=depth of the tree

    #include <vector>
    #include <bits/stdc++.h>
    using namespace std;
    bool testBST(vector<int> arr1, vector<int> arr2,int sz,int it1,int it2,int min_val,int max_val){
    	int i,j;
    	for(i=it1;i<sz;i++){
    		if(arr1[i] >= min_val && arr1[i] < max_val)
    			break;
    	}
    	for(j=it2;j<sz;j++){
    		if(arr2[j] >= min_val && arr2[j] < max_val)
    			break;
    	}
    	if (i==sz && j==sz){
    		return true;
    	}
    	
    	
    	if( ((i==sz)^(j==sz) ) || arr1[i]!=arr2[j])
    		return false;
    	
    	return testBST(arr1,arr2,sz,i+1,j+1,arr1[i],max_val) && testBST(arr1,arr2,sz,i+1,j+1,min_val,arr1[i]);
    }
    bool sameBsts(vector<int> arr1, vector<int> arr2) {
      // Write your code here.
    	int sz1=size(arr1),sz2=size(arr2);
    	if(sz1!=sz2){
    		return false;
    	}
    	if(sz1==0){
    		return true;
    	}
    	if(arr1[0]!=arr2[0]){
    		return false;
    	}
    	
    	return testBST(arr1,arr2,sz1,0,0,INT_MIN, INT_MAX);
      
    }


So, Method 2 is Optimal solution.








