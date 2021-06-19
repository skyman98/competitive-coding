# Find Kth Largest value in BST

  

> in this question we have one BST and one int k value, so we need to find that kth largest value of BST.

  

**

## Method 1:

> we can travel in INORDER so, we get ascending values of the array. after that, we need to find the kth value from the end of the array.

> so this method takes O(n) time and O(n) Space.


## Method 2:


> instead of traveling in INORDER and then find the last kth value, we can use Reverse INORDER to get better time complexity.

> so we can travel from right node -> current node -> left node.

> so it will directly give you the kth element of BST. this method work with O(h + k ) time and O(h) space.

**Code :** 

    using namespace std;
    
    // This is an input class. Do not edit.
    class BST {
    public:
      int value;
      BST *left = nullptr;
      BST *right = nullptr;
    
      BST(int value) { this->value = value; }
    };
    struct treedata{
    	int val;
    	int lastvisited;
    };
    void finder(BST *node,int k,treedata &treeinfo){
    	if(node==nullptr || treeinfo.val >=k){
    		return;
    	}
    	finder(node->right,k,treeinfo);
    	if(treeinfo.val < k){
    		treeinfo.val++;
    		treeinfo.lastvisited = node->value;
    		finder(node->left,k,treeinfo);
    	}
    }
    int findKthLargestValueInBst(BST *tree, int k) {
      // Write your code here.
    	auto node=treedata{0,-1};
    	finder(tree,k,node);
    	return node.lastvisited;
    }


