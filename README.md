# DSA
#include <stdio.h>
#include <stdlib.h>

/* Node structure for linked list */
struct Node {
    int data;
    struct Node* next;
};

/* Function to create a new node */
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

/* Function to insert a node at the beginning of the linked list */
void insertAtBeginning(struct Node** headRef, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = *headRef;
    *headRef = newNode;
}

/* Function to reverse the linked list */
void reverseList(struct Node** headRef) {
    struct Node *prevNode, *currentNode, *nextNode;
    prevNode = NULL;
    currentNode = *headRef;
    while (currentNode != NULL) {
        nextNode = currentNode->next;
        currentNode->next = prevNode;
        prevNode = currentNode;
        currentNode = nextNode;
    }
    *headRef = prevNode;
}

/* Function to print the linked list */
void printList(struct Node* node) {
    while (node != NULL) {
        printf("%d ", node->data);
        node = node->next;
    }
    printf("\n");
}

/* Main function */
int main() {
    struct Node* head = NULL;
    insertAtBeginning(&head, 6);
    insertAtBeginning(&head, 5);
    insertAtBeginning(&head, 4);
    insertAtBeginning(&head, 3);
    insertAtBeginning(&head, 2);
    insertAtBeginning(&head, 1);

    printf("Original list: ");
    printList(head);

    reverseList(&head);

    printf("Reversed list: ");
    printList(head);

    return 0;
}