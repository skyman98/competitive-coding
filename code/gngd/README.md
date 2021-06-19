
# right smaller than

> In this question, one array is given we need to find no. of the smaller element from its right side and return the array (same size as input ).

**Input : [8,5,11,-1,3,4,2]
output: [5,4,4,0,1,1,0]**

  

**Method 1:**

> we can direct use brute force to solve this question, using two for loops.
In this method, time-complexity is O(n^2) and space complexity is O(n).

**CODE:**

    using namespace std;
    
    vector<int> rightSmallerThan(vector<int> arr) {
      // Write your code here.
    	vector<int> vec={};
    	for(int i=0;i<arr.size();i++){
    		int count=0;
    		for(int j=i+1;j<arr.size();j++){
    		if(arr[i]>arr[j]){
    			count++;
    		}
    			
    		}
    		vec.push_back(count);
    	}
      return vec;
    }
      

**method 2:**

> we can use a Binary search tree and reduce time complexity.
> 
> In this method, we can create BST for each node and store some extra information like no.of a node in the left part of the particular node.
> 
> To create BST we need O(n Logn) time.
 
 **CODE:**

     using namespace std;
    struct node{
    	int val;
    	int inx;
    	int leftsize;
    	int current;
    	struct node *left,*right;
    };
    struct node *newnode(int item,int ival,int leftsize,int pass,vector<int> &vec){
    	struct node *temp = (struct node *)malloc(sizeof(struct node));
      temp->val = item;
    	temp->inx=ival;
    	
    	temp->leftsize=leftsize;
    	temp->current=pass;
      temp->left = temp->right = nullptr;
    	vec.push_back(pass);
      return temp;
    }
    
    struct node *insert(struct node *node,int val,int ival,int leftsize,int pass,vector<int> &vec){
    	if(node == nullptr){
    		return newnode(val,ival,leftsize,pass,vec);
    	}
    	if(node->val >= val){
    		node->leftsize=node->leftsize + 1 ;
    		node->left = insert(node->left,val,ival,leftsize,pass,vec);
    	}
    	else{
    		
    		node->right = insert(node->right,val,ival,leftsize,pass+1+node->leftsize,vec);
    		
    	}
    	return node;
    }
    
    
    
    
    vector<int> rightSmallerThan(vector<int> arr) {
      // Write your code here.
    	if(arr.size()==0){
    		return {};
    	}
    	vector<int> vec={};
    	
    	struct node *root = nullptr;
    	for(int i=arr.size()-1;i>=0;i--){
    		root=insert(root,arr[i],i,0,0,vec);
    	}
    	reverse(vec.begin(),vec.end());
      return vec;
    }
|  

![gdgdd](https://drive.google.com/file/d/1nHHjlOEMTqqZEf0QYX3HlEaUTDXEL6Px/view?usp=sharing)

