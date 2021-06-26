

## Shift Link List

> In this Question, we have one link list and one integer k value. 
> Our task is to shift this link by k steps in one direction ( forward or backward ) based on k value is negative or positive.

## Method:

> suppose we have a circular link list then in this Question, our task is to find the only head of the link list. so we first convert simple link list to circular link list by updating   tail -> next = head;  when we find the tail pointer during this we also find the length of the link list so, we can reduce time in calculation.

**Code:**

    using namespace std;
    
    class LinkedList {
    public:
      int value;
      LinkedList *next;
    
      LinkedList(int value) {
        this->value = value;
        next = nullptr;
      }
    };
    
    LinkedList *shiftLinkedList(LinkedList *head, int k) {
    	int len=1;
    	if(head==nullptr){
    		return nullptr;
    	}
      if(k==0)
    		return head;
    	LinkedList *tail=head;
    	while(tail->next!=nullptr){
    		tail=tail->next;
    		len++;
    	}
    	tail->next=head;	
    	if(k>0){
    		k=k%len;
    	  if(k!=0){
    			k=len-k;
    		}
    	}else{
    		k=k%len;
    		k=-k;
    	}
    	while(k){
    		head=head->next;
    		tail=tail->next;
    		k--;
    		
    	}
    	tail->next=nullptr;
      return head;
    }

**Time : O(n)
Space: O(1)**
