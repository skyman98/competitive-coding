

## Remove Kth Node From End

> In this Question, we have one list and one integer as input. our task is to remove Kth elements from the end of the link list.

## Method :

> The basic idea to solve this method is to travel all nodes one by one and find the length of the link list after that we remove (Length - K )th node from the root node.
 
> but In this Approach, we need to travel 2 times. so is there any other optimal approach? 
> **Yes**  
> first, we Create a two-pointer one is First and second. First = second = root after that we move the second pointer to the k step. after this process, we move both pointers till we get second == nullptr

**Code:**

    void removeKthNodeFromEnd(LinkedList *head, int k) {
    	LinkedList *first=head;
    	LinkedList *second=head;
    	while(k--){
    		second=second->next;
    	}
    	if(second==nullptr){
    		head->value=head->next->value;
    		head->next=head->next->next;
    		return;
    	}
    	cout<<"**"<<second->value<<endl;
    	while(second->next!=nullptr){
    		second=second->next;
    		first=first->next;
    	}
    	cout<<"**"<<first->value<<endl;
    	first->next=first->next->next;
    	
    	
    }

**Time :O(n)
Space:O(1)**


