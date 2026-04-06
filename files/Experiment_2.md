# Experiment 2 - Concepts of Matrix and Sparse Matrix

## Q1) Write a C program to create function for performing matrix multiplication using UDF.

```c
#include <stdio.h>

void mul(int a[10][10], int b[10][10], int r[10][10], int r1, int c1, int c2) {
    for (int i = 0; i < r1; i++)
        for (int j = 0; j < c2; j++) {
            r[i][j] = 0;
            for (int k = 0; k < c1; k++)
                r[i][j] += a[i][k] * b[k][j];
        }
}

void disp(int a[10][10], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++)
            printf("%d ", a[i][j]);
        printf("\n");
    }
}

int main() {
    int a[10][10], b[10][10], r[10][10], r1, c1, r2, c2;
    scanf("%d %d", &r1, &c1);
    scanf("%d %d", &r2, &c2);
    if (c1 != r2)
        return 0;
    for (int i = 0; i < r1; i++)
        for (int j = 0; j < c1; j++)
            scanf("%d", &a[i][j]);
    for (int i = 0; i < r2; i++)
        for (int j = 0; j < c2; j++)
            scanf("%d", &b[i][j]);
    mul(a, b, r, r1, c1, c2);
    disp(r, r1, c2);
    return 0;
}
```

---

## Q2) Write a C program to input elements into a square matrix and display the transpose of it using UDF.

```c
#include <stdio.h>

void transpose(int a[10][10], int t[10][10], int n) {
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            t[j][i] = a[i][j];
}

void disp(int a[10][10], int n) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++)
            printf("%d ", a[i][j]);
        printf("\n");
    }
}

int main() {
    int a[10][10], t[10][10], n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &a[i][j]);
    transpose(a, t, n);
    disp(t, n);
    return 0;
}
```

---

## Q3) Write a program to input elements into a 4X4 matrix, check it for sparse or not. If sparse then store the non-zero elements into an alternate matrix and then display it using UDF.

```c
#include <stdio.h>

int isSparse(int a[4][4]) {
    int z = 0;
    for (int i = 0; i < 4; i++)
        for (int j = 0; j < 4; j++)
            if (a[i][j] == 0)
                z++;
    return z > 8;
}

void store(int a[4][4], int b[][2], int *c) {
    *c = 0;
    for (int i = 0; i < 4; i++)
        for (int j = 0; j < 4; j++)
            if (a[i][j] != 0) {
                b[*c][0] = i;
                b[*c][1] = j;
                (*c)++;
            }
}

void disp(int b[][2], int c) {
    for (int i = 0; i < c; i++)
        printf("%d %d\n", b[i][0], b[i][1]);
}

int main() {
    int a[4][4], b[16][2], c;
    for (int i = 0; i < 4; i++)
        for (int j = 0; j < 4; j++)
            scanf("%d", &a[i][j]);
    if (isSparse(a)) {
        store(a, b, &c);
        disp(b, c);
    }
    return 0;
}
```
