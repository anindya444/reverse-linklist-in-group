# reverse-linklist-in-group
reverse linked list in group
#include <iostream>

using namespace std;

class Node {
public:Node*sorted=NULL;
       int data;
       Node* next;
   Node(int data1) {
        data = data1;
        next = nullptr;
    }
};
Node* reversegroup(Node*head,int k){
    Node*curr=head;
    Node*newhead=NULL;
    Node*tail=NULL;
         while(curr!=NULL){
                Node*pre=NULL;
                Node*grouphead=curr;
                Node*next=NULL;
                int count=0;
        while(curr!=NULL && count<k){
         next=curr->next;
         curr->next=pre;
         pre=curr;
         curr=next;
         count++;                   }

    if(tail!= NULL){ tail->next=pre;}
    if(newhead==NULL){ newhead=pre;}
       tail=grouphead;                    }
     return newhead;   
}
void printLinkedList(Node* head) {
    
    while (head != nullptr) {
        // Print the data of the current node
        cout << head->data << " "; 
        // Move to the next node
        head = head->next; 
    }
    cout << endl;
};


int main() {
    Node* head = new Node(4);
   head->next = new Node(8);
  head->next->next = new Node(9);
 head->next->next->next=new Node(1);
 head->next->next->next->next=new Node(7);
 head->next->next->next->next->next=new Node(2);

 printLinkedList(head);
 head= reversegroup(head,3);
 printLinkedList(head);
 return 0;
}
