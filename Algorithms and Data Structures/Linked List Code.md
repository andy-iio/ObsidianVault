```cpp
#include <stdio.h>
#include <iostream>

using namespace std;

//set up the node class, this is a singly linked list
class Node {
public:
    int data;
    Node* next;
};

//print the list, starting from node n
void print_list(Node* n) {
    while (n != NULL) {
        cout << n->data << " ";
        n = n->next;
    }
}

//insert a new node at the start of the list
void pushToStart(struct Node** head_ref, int new_data) {
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = (*head_ref);
    (*head_ref) = new_node;
}


void appendToEnd(struct Node** head_ref, int new_data) {
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    struct Node* last = *head_ref;
    new_node->data = new_data;
    new_node->next = NULL;
    while (last->next != NULL)
        last = last->next;
    last->next = new_node;
}

int main() {
    Node* head = NULL;
    Node* second = NULL;
    Node* third = NULL;

    head = new Node();
    second = new Node();
    third = new Node();

    head->data = 1;
    head->next = second;

    second->data = 2;
    second->next = third;

    third->data = 3;
    third->next = NULL;

    print_list(head);
    push(&head, 11);
    print_list(head);
}
```