

## Merge two Sorted Link list

> In this Question, we have two sorted link lists and our task is to merge both link lists according to sorted order and without any extra space.

## Method:

> we use three-pointers as indexing pointer.(ans1,ans2,prev) 
> asn1 pointing to list1.
> ans2 pointing to list2. 
> prev pointing to the previous node of the
> final node list.

**Code:**

    #include <vector>
    
    using namespace std;
    
    // This is an input class. Do not edit.
    class LinkedList {
    public:
      int value;
      LinkedList *next;
    
      LinkedList(int value) {
        this->value = value;
        next = nullptr;
      }
    };
    
    LinkedList *mergeLinkedLists(LinkedList *list1, LinkedList *list2) {
      LinkedList *ans1=list1;
    	LinkedList *prev=nullptr;
    	LinkedList *ans2=list2;
    	while(ans1!=nullptr && ans2!=nullptr){
    		 if(ans1->value < ans2->value){
    			 prev=ans1;
    			 ans1=ans1->next;
    		 }
    		else{
    			if(prev!=nullptr){
    				prev->next=ans2;
    			}
    			prev=ans2;
    			ans2=ans2->next;
    			prev->next=ans1;
    		}
    		
    	}
    	if(ans1==nullptr){
    		prev->next=ans2;
    	}
      return list1->value < list2->value ? list1 :list2;
    }


**Time : O(n+m) 
Space:O(1)**
