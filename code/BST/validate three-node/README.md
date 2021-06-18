**

## # validate three-node:

> so in this question, as input one BST is given and 3 node pointer.
>  we need to find that this 3 node is in the correct position. 
**position:**
> node2 is the ancestor of node 1 and descendant of node 3 or vice-versa.

**Basic condition:**

 - we have BST tree (Not just Binary tree )

**Method 1:**

>we can use Binary search because BST is given. so first, we find that node1 is the ancestor of node2 and then find node3 is the descendent of node2. if this case does not work then we can use the same approach but we swap node1 and node3.

> In this method,  time complexity is O(h) and Space complexity is O(1)

**so can we use fast our algorithm ?**

> yes, 
> we can compare between node1 and node3 also, and if we get node3 before node2 that means we need to stop and return false because that case not satisfy our condition.

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
    bool verify(BST *node1, BST *node2, BST *node3){
    	if(node1==nullptr){
    		return false;
    	}
    	if(node1==node2){
    		return true;
    	}
    	if(node1==node3){
    		return false;
    	}
    	if(node1->value > node2->value && node1->value > node3->value){
    		return verify(node1->left,node2,node3);
    	}
    	else if(node1->value <= node2->value && node1->value <= node3->value){
    		return verify(node1->right,node2,node3);
    	}
    	else{
    		  return false;
    	}
    }
    bool validateThreeNodes(BST *node1, BST *node2, BST *node3) {
      // Write your code here.
    	return verify(node1,node2,node3) || verify(node3,node2,node1);
    
    }


  






