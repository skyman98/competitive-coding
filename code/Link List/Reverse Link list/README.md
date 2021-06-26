

## Reverse Link list

> In this Question, we have one singly link list and our task is to reverse this link list. 

##  Method :

 

> we can solve this Question using O(n) Space which is not preferable. So we use some optimal methods. we use 3 pointers that represent the consecutive node in the list. let's take this node as P1, P2, P3,
> 
> we run our code till P3!=Nullptr. at every time we change following things. 
> p2->next=p1
> p1=p2; 
> p2=p3;
> p3=p3->next; 
> and we get reverse of link list.

**Code :**

     using namespace std;
    
    class LinkedList {
    public:
      int value;
      LinkedList *next;
    
      LinkedList(int value) {
        this->value = value;
        this->next = nullptr;
      }
    };
    
    LinkedList *reverseLinkedList(LinkedList *head) {
     LinkedList *p1=nullptr;
    	LinkedList *p2=nullptr;
    	LinkedList *p3=nullptr;
    	if(head==nullptr){
    		return nullptr;
    	}
    	else{
    		p1=head;
    		if(p1->next==nullptr){
    			return p1;
    		}
    		else{
    			p2=p1->next;
    			p1->next=nullptr;
    			if(p2->next==nullptr){
    				p2->next=p1;
    				return p2;
    			}
    			else{
    				p3=p2->next;
    				p2->next=p1;
    				while(p3->next!=nullptr){
    					p1=p2;
    					p2=p3;
    					p3=p3->next;
    					p2->next=p1;
    				}
    				p3->next=p2;
    				return p3;
    			}
    		}
    	}
      return nullptr;
    }

## Code :

    using namespace std;
    
    class LinkedList {
    public:
      int value;
      LinkedList *next;
    
      LinkedList(int value) {
        this->value = value;
        this->next = nullptr;
      }
    };
    
    LinkedList *reverseLinkedList(LinkedList *head) {
      LinkedList *prev=nullptr;
    	LinkedList *curr=head;
    	while(curr!=nullptr){
    		LinkedList *next=curr->next;
    		curr->next=prev;
    		prev=curr;
    		curr=next;
    	}
    	
      return prev;
    }

**Time: O(n)
Space: O(1)**


