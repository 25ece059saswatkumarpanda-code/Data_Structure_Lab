# Experiment 6 - Sorting and Merging

## Q1) Write a program to input elements into two arrays A[5] and B[5]. Input the elements in ascending order and then merge their values into a resultant array C[10] in sorted manner using UDF.

```c
#include <stdio.h>

void merge(int a[], int b[], int c[], int n1, int n2) {
    int i = 0, j = 0, k = 0;
    while (i < n1 && j < n2) {
        if (a[i] < b[j])
            c[k++] = a[i++];
        else
            c[k++] = b[j++];
    }
    while (i < n1)
        c[k++] = a[i++];
    while (j < n2)
        c[k++] = b[j++];
}

int main() {
    int a[5], b[5], c[10];
    for (int i = 0; i < 5; i++)
        scanf("%d", &a[i]);
    for (int i = 0; i < 5; i++)
        scanf("%d", &b[i]);
    merge(a, b, c, 5, 5);
    for (int i = 0; i < 10; i++)
        printf("%d ", c[i]);
    printf("\n");
    return 0;
}
```

---

## Q2) Write a program to implement insertion sort on a given list of array elements.

```c
#include <stdio.h>

void insertionSort(int a[], int n) {
    for (int i = 1; i < n; i++) {
        int key = a[i];
        int j = i - 1;
        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
        }
        a[j + 1] = key;
    }
}

int main() {
    int a[50], n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    insertionSort(a, n);
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```

---

## Q3) Write a C program to implement quick sort to a given list of integers to sort in ascending order.

```c
#include <stdio.h>

int partition(int a[], int low, int high) {
    int pivot = a[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (a[j] <= pivot) {
            i++;
            int temp = a[i];
            a[i] = a[j];
            a[j] = temp;
        }
    }
    int temp = a[i + 1];
    a[i + 1] = a[high];
    a[high] = temp;
    return i + 1;
}

void quickSort(int a[], int low, int high) {
    if (low < high) {
        int pi = partition(a, low, high);
        quickSort(a, low, pi - 1);
        quickSort(a, pi + 1, high);
    }
}

int main() {
    int a[50], n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    quickSort(a, 0, n - 1);
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```
