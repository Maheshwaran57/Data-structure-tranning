#include <stdio.h>
#include <stdlib.h>
#include <string.h>
struct Node {
    char data[50];
    struct Node* next;
};

struct Node* createNode(const char* data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    strcpy(newNode->data, data);
    newNode->next = NULL;
    return newNode;
}

void insertAtEnd(struct Node** head, const char* data) {
    struct Node* newNode = createNode(data);

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
}

void insertAtBeginning(struct Node** head, const char* data) {
    struct Node* newNode = createNode(data);
    newNode->next = *head;
    *head = newNode;
}

void insertAtPosition(struct Node** head, const char* data, int position) {
    if (position <= 1) {
        insertAtBeginning(head, data);
        return;
    }

    struct Node* newNode = createNode(data);
    struct Node* temp = *head;

    for (int i = 1; i < position - 1 && temp != NULL; i++) {
        temp = temp->next;
    }

    if (temp == NULL) {
        printf("Position out of bounds. Inserting at end.\n");
        insertAtEnd(head, data);
        return;
    }

    newNode->next = temp->next;
    temp->next = newNode;
}


void displayList(struct Node* head) {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }

    struct Node* temp = head;
    while (temp != NULL) {
        printf("%s -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

void deleteList(struct Node** head) {
    struct Node* current = *head;
    struct Node* nextNode;

    while (current != NULL) {
        nextNode = current->next;
        free(current);
        current = nextNode;
    }

    *head = NULL;
}

int main() {
    struct Node* head = NULL;

   
    insertAtEnd(&head, "coffee");
    insertAtEnd(&head, "chocolate");
    insertAtEnd(&head, "biscuit");
    insertAtEnd(&head, "brownie");
    insertAtEnd(&head, "ice cream");

    printf("Initial List:\n");
    displayList(head);


    insertAtBeginning(&head, "cake");
    printf("\nAfter inserting 'cake' at beginning:\n");
    displayList(head);

    insertAtEnd(&head, "chicken rice");
    printf("\nAfter inserting 'chicken rice' at end:\n");
    displayList(head);
    insertAtPosition(&head, "curd rice", 4);
    printf("\nAfter inserting 'curd rice' at position 4:\n");
    displayList(head);

    deleteList(&head);
    printf("\nAfter deleting the list:\n");
    displayList(head);

    return 0;
}
