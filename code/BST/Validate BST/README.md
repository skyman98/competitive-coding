## Validate BST

> in this Question, we have one BST as input and we need to identify that this BST is valid or not?

**

## Method:

**

> At every node position. we have some specific range conditions. so, we can use that property to solve this question.
Time Complexity : O(n)
Space Complexity: O(d) d=depth of tree

**Code:**

    class BST {
    public:
      int value;
      BST *left;
      BST *right;
    
      BST(int val);
      BST &insert(int val);
    };
    bool checker(BST *tree,int minval,int maxval){
    	if(tree->value < minval || tree->value >= maxval){
    		return false;
    	}
    	if(tree->left !=nullptr && !checker(tree->left,minval,tree->value)){
    		return false;
    	}
    	if(tree->right !=nullptr && !checker(tree->right,tree->value,maxval)){
    		return false;
    	}
    	return true;
    }
    bool validateBst(BST *tree) {
      // Write your code here.
      return checker(tree,INT_MIN,INT_MAX);
    }


