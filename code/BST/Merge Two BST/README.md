## Merge Two BST

> In this Question, we have two BSTs we need to create one array that stores both BST node values in ascending order.
 
> as we can know that minimum values in BST available at a left leaf node and then we can go to the root node and then the right parts, which means we can travel in Inorder.

## Method 1 :

> we can create two different arrays to store this BST in INORDER. after we get this array we have two sorted lists and we need to merge and sort order.  SO we can solve this In O(N+M) time. and Space is O(N+M).

**Code :**

    class Solution
    {
        public:
        //Function to return a list of integers denoting the node 
        //values of both the BST in a sorted order.
        void inoder(Node *root,vector<int> &arr){
            if(root==nullptr)
                return;
            inoder(root->left,arr);
            arr.push_back(root->data);
            inoder(root->right,arr);
        }
        vector<int> combine(vector<int> &v1,vector<int> &v2){
            vector<int> v3;
            int sz1=v1.size(),sz2=v2.size(),i=0,j=0;
            while(i<sz1 && j<sz2){
                if(v1[i]<v2[j]){
                    v3.push_back(v1[i]);
                    i++;
                }
                else{
                    v3.push_back(v2[j]);
                    j++;
                }
                    
            }
            while(i<sz1){
                v3.push_back(v1[i]);
                i++;
            }
            while(j<sz2){
                v3.push_back(v2[j]);
                j++;
            }
            return v3;
        }
        vector<int> merge(Node *root1, Node *root2)
        {
            vector<int> arr1,arr2;
            inoder(root1,arr1);
            inoder(root2,arr2);
            
            
           //Your code here
           return combine(arr1,arr2);
        }
    };

## Method 2:

> I do not solve this method 2, but I have some theoretical ideas about it. if we have parallel processing then this may be solved using thread and maybe using semaphore. we can use the INORDER method ,

    INORDER(root->left);
    root->value; // here we compare both BST and find a minimum one if its BST1 then we can open the right part for BST1 and put waiting for BST2.


