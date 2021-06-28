

## Find Closest value in BST

> In this Question, we have one BST and one target value. our task is to find the closest value in a given BST.

## Method :

> we can travel all nodes one by one and take difference with the target, if its minimum then returns those value. But is it optimal ??
> No, for the above task we have Time O(n) and we can also solve this problem using O(n logn ) time. 
> We can travel in only one direction ( left or right ) based on a given value that is greater than or less than.

**CODE :**

    class BST {
    public:
      int value;
      BST *left;
      BST *right;
    
      BST(int val);
      BST &insert(int val);
    };
    int samebst(BST *root,int target,BST *ans){
    	
    	int node=-1;
    	  while(root!=nullptr){
    			cout<<"** "<<root->value<<" -- "<<node<<endl;
    			int diff1=abs(ans->value - target);
    				int diff2=abs(root->value - target);
    			if(diff1 > diff2){
    				ans=root;
    			}
    
    			if(target > root->value){
    				root=root->right;
    			}
    			else if(target < root->value){
    				root=root->left;
    			}
    			else{
    				break;
    			}
    		}
    	return ans->value;
    	  
    }
    int findClosestValueInBst(BST *tree, int target) {
      // Write your code here.
    	return samebst(tree,target,tree);
      
    }

**Time : O(N)
Space:O(1)**
