# Min Height BST

> in this Question, we have one sorted Array so now our task is to create BST of that array and the height of that BST tree is minimum.

  

## Method:

> so we have a sorted array and we need to create a minimum height.

> for minimum height, we need to balance all nodes .so that we get the equal size of the left subtree and right subtree.

> we can do that via the middle element.

> we can find the middle value and put it as the root node and we have two parts of array one is left subarray and right subarray so, we can do the same process for both parts.

> Time complexity is O(n) and Space Complexity O(n).

## Code:

    using namespace std;
    
    class BST {
    public:
      int value;
      BST *left;
      BST *right;
    
      BST(int value) {
        this->value = value;
        left = nullptr;
        right = nullptr;
      }
    
    //this INSERT function is not used in programm
      void insert(int value) {
        if (value < this->value) {
          if (left == nullptr) {
            left = new BST(value);
          } else {
            left->insert(value);
          }
        } else {
          if (right == nullptr) {
            right = new BST(value);
          } else {
            right->insert(value);
          }
        }
      }
    };
    BST *Spliter(vector<int> arr,int start,int end){
    	if(start > end){
    		return nullptr;
    	}
    	int mid=(start + end)/2;
    	BST *bst=new BST(arr[mid]);
    	bst->left=Spliter(arr,start,mid-1);
    	bst->right=Spliter(arr,mid+1,end);
    	return bst;
    }
    BST *minHeightBst(vector<int> arr) {
      return Spliter(arr,0,arr.size()-1);
    }

