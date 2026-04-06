# Experiment 1 - Functions and Arrays

## Q1) Write a program to create an UDF for input 10 numbers into a 1D array. Create two functions MAX() and MIN(). MAX() is used to return the largest element and MIN() is used to return the smallest number in array.

```c
#include <stdio.h>
#define SIZE 10

int MAX(int a[], int n) {
    int max = a[0];
    for (int i = 1; i < n; i++)
        if (a[i] > max)
            max = a[i];
    return max;
}

int MIN(int a[], int n) {
    int min = a[0];
    for (int i = 1; i < n; i++)
        if (a[i] < min)
            min = a[i];
    return min;
}

int main() {
    int a[SIZE];
    for (int i = 0; i < SIZE; i++)
        scanf("%d", &a[i]);
    printf("Max: %d\n", MAX(a, SIZE));
    printf("Min: %d\n", MIN(a, SIZE));
    return 0;
}
```

---

## Q2) Write a C program to create methods for operations insertion and display on 1D array of elements using UDF.

```c
#include <stdio.h>

void display(int a[], int n) {
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
}

void insert(int a[], int n, int ele, int pos) {
    for (int i = n; i > pos; i--)
        a[i] = a[i - 1];
    a[pos] = ele;
    display(a, n + 1);
}

int main() {
    int a[50], n, ele, pos;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    scanf("%d", &ele);
    scanf("%d", &pos);
    insert(a, n, ele, pos);
    return 0;
}
```

---

## Q3) Write a C program to create methods for operations deletion, and display on 1D array of elements using UDF.

```c
#include <stdio.h>

void display(int a[], int n) {
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
}

int del(int a[], int n, int pos) {
    for (int i = pos; i < n - 1; i++)
        a[i] = a[i + 1];
    display(a, n - 1);
    return n - 1;
}

int main() {
    int a[50], n, pos;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    scanf("%d", &pos);
    del(a, n, pos);
    return 0;
}
```
