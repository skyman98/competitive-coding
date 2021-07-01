

## Rearrange linked list

> In this Que, we have a linked list and one integer k value. Our task is to rearrange all nodes of a linked list based on their value is less, more, or equal to the k.

## Method :

> we create 6 pointers which are pairs of (head-tail ) for all 3 conditions less, more, and equal.

**Code:**

    LinkedList *rearrangeLinkedList(LinkedList *head, int k) {
      LinkedList *less=nullptr;
    	LinkedList *l1=nullptr;
    	LinkedList *l2=nullptr;
    	LinkedList *l3=nullptr;
    	LinkedList *same=nullptr;
    	LinkedList *more=nullptr;
    	LinkedList *temp=head;
    	while(temp!=nullptr){
    		if(temp->value > k){
    			  if(more==nullptr){
    					more=temp;
    					l3=temp;
    				}
    			else{
    				more->next=temp;
    				more=more->next;
    			}
    		}
    		else if(temp->value < k){
    			if(less==nullptr){
    					less=temp;
    					l1=less;
    				}
    			else{
    				less->next=temp;
    				less=less->next;
    			}
    		}
    		else{
    			if(same==nullptr){
    					same=temp;
    				  l2=temp;
    				}
    			else{
    				same->next=temp;
    				same=same->next;
    			}
    		}
    		temp=temp->next;
    	}
    	if(less!=nullptr){
    		head=l1;
    		if(same!=nullptr){
    		less->next=l2;
    		same->next=l3;
    		}
    		else{
    			less->next=l3;
    		}
    	}
    	else{
    		if(same!=nullptr){
    		head=l2;
    		same->next=l3;
    	}
    		else{
    			head=l3;
    		}
    	}
      if(more!=nullptr){
    		more->next=nullptr;
    	}
    	
      return head;
    }

**Time: O(n)**
**Space: O(1)** 
