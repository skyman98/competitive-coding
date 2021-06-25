

## Remove Duplicate from LinkList

> In this Question, we have one List of integers and our task is to remove duplicates from that list. There is one more important condition that is Given the list of integers is in sorted order.

## Method :

> we can travel from the root node to the end node and during this process if the previous node is the same as the current node then remove the current node.

**Code:**


    LinkedList *removeDuplicatesFromLinkedList(LinkedList *root) {
      // Write your code here.
    	LinkedList *ans = root;
    	LinkedList *temp = root;
    	if(root==nullptr)
    		return ans;
    
    	root=root->next;
    	while(root!=nullptr){
    		if(temp->value==root->value){
    			temp->next=root->next;
    			root=root->next;
    		}
    		else{
    			temp=root;
    			root=root->next;
    		}
    			
    		
    	}
      return ans;
    }

**Time :O(n)
Space:O(1)**

