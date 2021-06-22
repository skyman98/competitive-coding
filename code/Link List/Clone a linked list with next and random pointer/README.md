

## Clone a linked list with next and random pointer

**Link of this Quetion :** 
[Clone a linked list with next and random pointer](https://practice.geeksforgeeks.org/problems/clone-a-linked-list-with-next-and-random-pointer/1/?track=md-linkedlist&batchId=144#)

  

> You are given a special linked list with **N** nodes where each node has a next pointer pointing to its next node. You are also given **M** random pointers , where you will be given **M** number of pairs denoting two nodes **a** and **b**  **i.e.** a->arb = b**.**

  

**Example :**

> **Input:**
 N = 4, M = 2
 value = {1,2,3,4}
 pairs = {{1,2},{2,4}}
**Output:** 1
 
> **Explanation:** In this test case, there are 4 nodes in linked list. Among these 4 nodes, 2 nodes have arbit pointer
 set, rest two nodes have arbit pointer as NULL. Second line tells us the value of four nodes. The third line gives the information about arbitrary pointers. The first node arbit pointer is set to node 2. The second node arbit pointer is set to node 4.

  

**Your Task:**

> The task is to complete the function **copyList**() which takes one argument the head of the linked list to be cloned and should
 **return** the head of the cloned linked list.
  
> **NOTE :** If their is any node whose arbitrary pointer is not given then it's by default null.

**Expected Time Complexity** : O(n)

**Expected Auxilliary Space** : O(1)

**Constraints:**

> 1 <= N <= 100
> 
> 1 <= M <= N
> 
> 1 <= a, b <= 100

  

## Method 1:

![Sample image for method 1](https://www.google.com/url?sa=i&url=https://www.geeksforgeeks.org/a-linked-list-with-next-and-arbit-pointer/&psig=AOvVaw35hrnEW20RYXZqkaYCt3Xr&ust=1624466148074000&source=images&cd=vfe&ved=0CAoQjRxqFwoTCOCQzJzWq_ECFQAAAAAdAAAAABAD)

 

> first, we create another link list that stores data and the next point is the same as the given link list, and we arb values take null.
 now we take the original node and update the next value to the address of the corresponding Copy node. now we can take a copy link list and update all arb values to the corresponding original node address, now we can update all arb using below method,
 
> curr->arb = curr -> arb -> arb -> next ;
 
>  and return the head of copy link list.

  

## Method 2:

> we can push pair of the node of the link list into a map like (original node address, create a new node, and return address).

>  after that, we update its all next and arb values according to below code :

  

**Code:**

    Node *copyList(Node *root) {
    
    Node *curr=root;
    
    map<Node *,Node *> ans;
    
    Node *clone=nullptr;
    
    while(root!=nullptr){
    
    ans.insert({root,new Node(root->data)});
    
    root=root->next;
    
    }
    
      
    
    for(auto itr=ans.begin();itr!=ans.end();itr++){
    
    Node *olddata=itr->first;
    
    Node *newdata=itr->second;
    
    newdata->arb=ans[itr->first->arb];
    
    newdata->next=ans[itr->first->next];
    
    }
    
    return ans[curr];
    
    
    }

