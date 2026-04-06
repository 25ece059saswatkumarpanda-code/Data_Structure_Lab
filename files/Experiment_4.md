# Experiment 4 - Stack and Queue

## Q1) Write a program using C to create a stack of numbers and perform using UDF: (i) push operation (ii) pop operation (iii) display operation

```c
#include <stdio.h>
#define SIZE 50

int stack[SIZE], top = -1;

void push() {
    if (top == SIZE - 1) {
        printf("Stack Overflow\n");
        return;
    }
    int x;
    printf("Enter value: ");
    scanf("%d", &x);
    stack[++top] = x;
}

void pop() {
    if (top == -1) {
        printf("Stack Underflow\n");
        return;
    }
    printf("Popped: %d\n", stack[top--]);
}

void display() {
    if (top == -1) {
        printf("Stack is empty\n");
        return;
    }
    for (int i = top; i >= 0; i--)
        printf("%d ", stack[i]);
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("1.Push 2.Pop 3.Display 4.Exit\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1: push(); break;
            case 2: pop(); break;
            case 3: display(); break;
            case 4: return 0;
        }
    }
}
```

---

## Q2) Write a C program to create a linear queue and perform the following operations using UDF: (i) insertion (ii) deletion and (iii) Traversal

```c
#include <stdio.h>
#define SIZE 50

int q[SIZE], front = -1, rear = -1;

void insert() {
    if (rear == SIZE - 1) {
        printf("Queue Full\n");
        return;
    }
    int x;
    printf("Enter value: ");
    scanf("%d", &x);
    if (front == -1)
        front = 0;
    q[++rear] = x;
}

void delete() {
    if (front == -1) {
        printf("Queue Empty\n");
        return;
    }
    printf("Deleted: %d\n", q[front]);
    if (front == rear)
        front = rear = -1;
    else
        front++;
}

void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }
    for (int i = front; i <= rear; i++)
        printf("%d ", q[i]);
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("1.Insert 2.Delete 3.Display 4.Exit\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1: insert(); break;
            case 2: delete(); break;
            case 3: display(); break;
            case 4: return 0;
        }
    }
}
```

---

## Q3) Write a C program to create a circular queue and perform the following operations using UDF: (i) insertion (ii) deletion and (iii) Traversal

```c
#include <stdio.h>
#define SIZE 5

int q[SIZE], front = -1, rear = -1;

void insert() {
    if ((rear + 1) % SIZE == front) {
        printf("Queue Full\n");
        return;
    }
    int x;
    printf("Enter value: ");
    scanf("%d", &x);
    if (front == -1)
        front = 0;
    rear = (rear + 1) % SIZE;
    q[rear] = x;
}

void delete() {
    if (front == -1) {
        printf("Queue Empty\n");
        return;
    }
    printf("Deleted: %d\n", q[front]);
    if (front == rear)
        front = rear = -1;
    else
        front = (front + 1) % SIZE;
}

void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }
    int i = front;
    while (1) {
        printf("%d ", q[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("1.Insert 2.Delete 3.Display 4.Exit\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1: insert(); break;
            case 2: delete(); break;
            case 3: display(); break;
            case 4: return 0;
        }
    }
}
```
