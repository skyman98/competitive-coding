

## Sum Of link list

> In this Question, we have two link lists and our task is to find the sum of this link list. 

> INPUT :
>   list1 : 2->4->7->1
>    list2: 9 -> 4 -> 5
 
> OUTPUT: 
> 1 -> 9 -> 2 -> 2 
> // list1 represant 1742
>  //list2 represent 549
> // 1742 + 549 = 2291

## Method :

> we can solve this problem by adding one-by-one elements from left to right. first, we add elements if the sum of nums is greater than 9 then we create carry bit = 1 and add this carry in the next addition.
> this process running till one of the pointers is nullptr. 
> after that, we add the remaining elements. after adding if still carry is one then we add another node whose value is the same as carry.

**Code :**

    LinkedList *sumOfLinkedLists(LinkedList *list1,
                                 LinkedList *list2) {
      // Write your code here.
    	LinkedList *ans=nullptr;
    	LinkedList *finalans=nullptr;
    	int flag=0;
    	int first=1;
    	while(list1!=nullptr && list2!=nullptr){
    		int val=list1->value + list2->value + flag ;
    		flag=0;
    		if(val > 9){
    					val=val%10;
    					flag=1;
    				}
    		cout<<"val:- "<<val<<" carray:- "<<flag<<endl;
    		LinkedList *temp=new LinkedList(val);			   	
    		if(first){
    			ans=temp;
    			finalans=ans;
    			first=0;
    		}
    		else{
    			ans->next=temp;
    			ans=ans->next;
    		}
    		
    		
    		list1=list1->next;
    		list2=list2->next;
    	}
    	if(list1==nullptr){
    		while(list2!=nullptr){
    			  int val=list2->value + flag ;
    			flag=0;
    				if(val > 9){
    					val=val%10;
    					flag=1;
    				}
    				LinkedList *temp=new LinkedList(val);			   
    			   ans->next=temp;
    				ans=ans->next;
    			list2=list2->next;
    		}
    	}
    	else{
    		while(list1!=nullptr){
    			  int val=list1->value + flag ;
    			flag=0;
    				if(val > 9){
    					val=val%10;
    					flag=1;
    				}
    			cout<<"val:- "<<val<<" carray:- "<<flag<<endl;
    				LinkedList *temp=new LinkedList(val)	;		   
    			  ans->next=temp;
    				ans=ans->next;
    			list1=list1->next;
    		}
    	}
    	if(flag){
    		LinkedList *temp=new LinkedList(flag)	;		   
    		ans->next=temp;
    		ans=ans->next;
    	}
    	
      return finalans;
    }

**Time: O( max(N,M))
Space :  O( max(N,M))**
