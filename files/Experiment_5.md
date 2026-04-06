# Experiment 5 - Searching and Sorting

## Q1) Write a program to implement binary search on array elements using UDF.

```c
#include <stdio.h>

int binarySearch(int a[], int n, int key) {
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (a[mid] == key)
            return mid;
        else if (a[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    return -1;
}

int main() {
    int a[50], n, key;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    scanf("%d", &key);
    int result = binarySearch(a, n, key);
    if (result == -1)
        printf("Element not found\n");
    else
        printf("Element found at index %d\n", result);
    return 0;
}
```

---

## Q2) Write a program to implement selection sort on a given list of array elements.

```c
#include <stdio.h>

void selectionSort(int a[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < n; j++)
            if (a[j] < a[minIdx])
                minIdx = j;
        int temp = a[minIdx];
        a[minIdx] = a[i];
        a[i] = temp;
    }
}

int main() {
    int a[50], n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    selectionSort(a, n);
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```

---

## Q3) Write a program to input a string and sort the alphabets in ascending order using bubble sort.

```c
#include <stdio.h>
#include <string.h>

void bubbleSort(char s[], int n) {
    for (int i = 0; i < n - 1; i++)
        for (int j = 0; j < n - i - 1; j++)
            if (s[j] > s[j + 1]) {
                char temp = s[j];
                s[j] = s[j + 1];
                s[j + 1] = temp;
            }
}

int main() {
    char s[100];
    scanf("%s", s);
    int n = strlen(s);
    bubbleSort(s, n);
    printf("%s\n", s);
    return 0;
}
```
