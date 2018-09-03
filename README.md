# performing-operations-on-singly-linked-list
/* Write Menu driven program to implement following operation on singly linked list
	a.Insert a node at the front/last/before a node/after a node in linked list
	b.delete a node at the front/last/before a node/after a node in linked list
	c.Traverse in forward/reverse order in the linked list
	d.Search a node and print its address.
	e.Update node information
*/
#include<stdio.h>
typedef struct Singly_Linked_List{
	int Data;
	Singly_Linked_List *Next;
}Node;
Node *Head;

void Create_list(){
	Head=NULL;
}

Node *Create_node(){
	Node *New_node;
	New_node=(Node *)malloc(sizeof(Node));
	printf("\n Enter number :");
	scanf("%d", &New_node->Data);
	New_node->Next=NULL;
	return New_node;
}

void Insert_first(){
	Node *New;
	New=Create_node();
	if(Head == NULL)
		Head=New;
	else{
		New->Next=Head;
		Head=New;
	}
}

void Insert_last(){
	Node *New, *temp;
	New=Create_node();

	if(Head==NULL)
		Head=New;
	else{
		temp=Head;
		while(temp != NULL)
			temp=temp->Next;

		temp->Next=New;
	}
}

void Insert_before( int key){
	Node *New, *temp;
	New=Create_node();
	if(Head==NULL)
		Head=New;
	else{
		temp=Head;
		while(temp != NULL){
			if((temp->Next)->Data == key)
				break;
			else
				temp=temp->Next;
		}
		if(temp == NULL)
			printf("\n Not found.");
		else{
			New->Next=temp->Next;
			temp->Next=New;
		}
	}
}

void Insert_after(int key){
	Node *New, *temp;
	New=Create_node();
	if(Head == NULL)
		Head = New;
	else{
		temp=Head;
		while(temp != NULL){
			if(temp->Data == key)
				break;
			else
				temp=temp->Next;
		}
		if(temp == NULL)
			printf("\n Not found.");
		else{
			New->Next=temp->Next;
			temp->next=New;
		}
	}
}

void Delete_first(){
	Node *temp;
	temp=Head;
	if(temp == NULL)
		printf("\n List is empty.");
	else{
		Head=temp->Next;

		temp->Next=NULL;
	}

	free(temp);
}
void Delete_last(){
	Node *temp, *temp1;
	temp=Head;
	if(temp == NULL)
		printf("\n List is empty.");
	else{
		while(temp != NULL){
			temp1=temp;
			temp=temp->Next;
		}


		temp1->Next=NULL;
	}
	free(temp);
}
void Delete_after(int key){
	Node *temp, *temp1;
	temp1=Head;
	if(temp1 == NULL)
		printf("\n List is empty.");
	else{
		while(temp1 != NULL){
			if(temp1->Data == key)
				break;
			else
				temp1=temp1->Next;
		}
		if(temp1 == NULL)
			printf("\n Not found");
		else{
			temp=temp1->Next;
			temp1->Next=temp->Next;
			temp->Next=NULL;
		}
		free(temp);
	}
}
void Delete_before(){
	Node *temp, temp1;
	temp1=Head;
	if(temp1 == NULL)
		printf("\n List is empty.");
	else{
		while(temp1 != NULL){
			if((temp1->Next)->Data == key)
				break;
			else{
				temp=temp1;
				temp1=temp1->Next;
			}
		}
		if(temp1 == NULL)
			printf("\n NOt found");
		else{
			temp->Next=temp1->Next;
			temp1->Next=NULL;
		}
		free(temp1);
	}
}
void Traverse_forward(){
	Node *temp;
	temp=Head;
	if(temp == NULL)
		printf("\n List is empty.");
	else{
		while(temp != NULL){
			printf("%d ", temp->Data);
			temp=temp->Next;
		}
	}
}
void Traverse_reverse(Node *temp){
	if(temp == NULL)
		return;
	else{
		Traverse_reverse(temp->Next);
		printf("%d ", temp->Data);
	}
}

Node *Search(int key){
	Node *temp;
	temp=Head;
	if(temp == NULL)
		printf("\n List is empty.");
	else{
		while(temp != NULL){
			if(temp->Data == key)
				break;
			else
				temp=temp->Next;
		}
		if(temp == NULL)
			return NULL;
		else
		      return (temp);
	 }
}
void Update(int val){
	Node *temp;
	int n;
	temp=Search(val);
	if(temp == NULL)
		printf("\n Not found.");
	else{
	      printf("\n Enter the update number :");
	      scanf("%d", &n);
	      temp->Data=n;
	}
}
main(){
	int ch, val;
	char ch1;
	do{
	    print("\n MENU");
	    printf("\n 1.Insert_first node");
	    printf("\n 2.Delete");
	    printf("\n 3.Traverse");
	    printf("\n 4.Search");
	    printf("\n 5.Update");
	    printf("\n Enter your choice :");
	    scanf("%d", &ch);
	    switch(ch){
	       case 1: printf("\n 1.Insert as first node");
		       printf("\n 2.Insert as last node");
		       printf("\n 3.Insert_before node");
		       printf("\n 4.Insert_after node");
		       printf("\n Enter your choice :");
		       scanf("%d", &ch);
		       switch(ch){
			 case 1:Insert_first();
				 break;
			 case 2:Insert_last();
				 break;
			 case 3: printf("\n Enter the number :");
				 scanf("%d", &val)
				 Insert_before(val);
				 break;
			 case 4: printf
				 Insert_after();
				 break;
			 default:printf("\n Wrong choice.");
			 }
			 break;
	       case 2:printf("\n 1.Delete the first node");
		       printf("\n 2.delete the last node");
		       printf("\n 3.delete_before node");
		       printf("\n 4.delete_after node");
		       printf("\n Enter your choice :");
		       scanf("%d", &ch);
		       switch(ch){
			 case 1:Delete_first();
				 break;
			 case 2:Delete_last();
				 break;
			 case 3:Delete_before();
				 break;
			 case 4:Delete_after();
				 break;
			 default:printf("\n Wrong choice.");
			}
   return 0;
 }  


