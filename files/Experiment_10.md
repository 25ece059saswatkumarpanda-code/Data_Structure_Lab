# Experiment 10 - Advanced Programs using Linked List

## Q1) Write a program to create a single linked list for storing the N cricket player details having member's player name, team name and batting average. Display only those players information whose batting average>=50

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct node {
    char name[50];
    char team[50];
    float avg;
    struct node *next;
};

struct node *head = NULL;

void create(int n) {
    struct node *temp, *ptr;
    for (int i = 0; i < n; i++) {
        temp = (struct node *)malloc(sizeof(struct node));
        printf("Enter player name: ");
        scanf("%s", temp->name);
        printf("Enter team name: ");
        scanf("%s", temp->team);
        printf("Enter batting average: ");
        scanf("%f", &temp->avg);
        temp->next = NULL;
        if (head == NULL)
            head = temp;
        else {
            ptr = head;
            while (ptr->next != NULL)
                ptr = ptr->next;
            ptr->next = temp;
        }
    }
}

void display() {
    struct node *temp = head;
    printf("\nPlayers with batting average >= 50\n");
    while (temp != NULL) {
        if (temp->avg >= 50)
            printf("%s %s %.2f\n", temp->name, temp->team, temp->avg);
        temp = temp->next;
    }
}

int main() {
    int n;
    printf("Enter number of players: ");
    scanf("%d", &n);
    create(n);
    display();
    return 0;
}
```

---

## Q2) Write a program to create a double linked list for storing account details of bank customers such as AC no, name, balance. Store details for N bank account holders and find the total balance for all account holders.

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int acno;
    char name[50];
    float balance;
    struct node *prev;
    struct node *next;
};

struct node *head = NULL;

void create(int n) {
    struct node *temp, *ptr;
    for (int i = 0; i < n; i++) {
        temp = (struct node *)malloc(sizeof(struct node));
        printf("Enter account number: ");
        scanf("%d", &temp->acno);
        printf("Enter name: ");
        scanf("%s", temp->name);
        printf("Enter balance: ");
        scanf("%f", &temp->balance);
        temp->next = NULL;
        temp->prev = NULL;
        if (head == NULL)
            head = temp;
        else {
            ptr = head;
            while (ptr->next != NULL)
                ptr = ptr->next;
            ptr->next = temp;
            temp->prev = ptr;
        }
    }
}

void total_balance() {
    struct node *temp = head;
    float total = 0;
    while (temp != NULL) {
        total += temp->balance;
        temp = temp->next;
    }
    printf("\nTotal Balance of all customers = %.2f\n", total);
}

int main() {
    int n;
    printf("Enter number of customers: ");
    scanf("%d", &n);
    create(n);
    total_balance();
    return 0;
}
```
