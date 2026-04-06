# Experiment 9 - Double Linked List

## Q1) Write a C program to perform the operations on a Double linked list: i) Insertion at beginning, ii) Deletion of 1st node iii) display all nodes

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *prev;
    struct node *next;
};

struct node *head = NULL;

void insert_begin() {
    struct node *temp;
    int x;
    temp = (struct node *)malloc(sizeof(struct node));
    printf("Enter value: ");
    scanf("%d", &x);
    temp->data = x;
    temp->prev = NULL;
    temp->next = head;
    if (head != NULL)
        head->prev = temp;
    head = temp;
}

void delete_first() {
    struct node *temp;
    if (head == NULL) {
        printf("List empty\n");
        return;
    }
    temp = head;
    head = head->next;
    if (head != NULL)
        head->prev = NULL;
    free(temp);
}

void display() {
    struct node *temp = head;
    if (head == NULL) {
        printf("List empty\n");
        return;
    }
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.Insert Beginning\n2.Delete First\n3.Display\n4.Exit\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1: insert_begin(); break;
            case 2: delete_first(); break;
            case 3: display(); break;
            case 4: exit(0);
        }
    }
}
```

---

## Q2) Write a C program to perform the operations on a double linked list: i) insertion at end, ii) deletion of last node iii) display all the nodes

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *prev;
    struct node *next;
};

struct node *head = NULL;

void insert_end() {
    struct node *temp, *ptr;
    int x;
    temp = (struct node *)malloc(sizeof(struct node));
    printf("Enter value: ");
    scanf("%d", &x);
    temp->data = x;
    temp->next = NULL;
    if (head == NULL) {
        temp->prev = NULL;
        head = temp;
        return;
    }
    ptr = head;
    while (ptr->next != NULL)
        ptr = ptr->next;
    ptr->next = temp;
    temp->prev = ptr;
}

void delete_last() {
    struct node *temp = head;
    if (head == NULL) {
        printf("List empty\n");
        return;
    }
    if (head->next == NULL) {
        free(head);
        head = NULL;
        return;
    }
    while (temp->next != NULL)
        temp = temp->next;
    temp->prev->next = NULL;
    free(temp);
}

void display() {
    struct node *temp = head;
    if (head == NULL) {
        printf("List empty\n");
        return;
    }
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.Insert End\n2.Delete Last\n3.Display\n4.Exit\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1: insert_end(); break;
            case 2: delete_last(); break;
            case 3: display(); break;
            case 4: exit(0);
        }
    }
}
```
