# BASIC-17 矩阵乘法

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 给定一个N阶矩阵A，输出A的M次幂（M是非负整数）
> 例如：
> A =
> 1 2
> 3 4
> A的2次幂
> 7 10
> 15 22

## 输入格式

> 第一行是一个正整数N、M（1<=N<=30, 0<=M<=5），表示矩阵A的阶数和要求的幂数接下来N行，每行N个绝对值不超过10的非负整数，描述矩阵A的值。

## 输出格式

> 输出共N行，每行N个整数，表示A的M次幂所对应的矩阵。相邻的数之间用一个空格隔开。

## 样例输入

> 2 2
> 1 2
> 3 4

## 样例输出

> 7 10
> 15 22

## 数据规模与约定

> <无>

## 解题思路

> 使用二位数组记录矩阵的变化过程，通过vector的assign进行重赋值，迭代计算即可。

## 通过代码

```cpp
#include <vector>
#include <iostream>

using namespace std;

int main() {
    int N, M;
    cin >> N >> M;
    vector<vector<int> > Res(N, vector<int>(N, 0));
    for (int i = 0; i < N; ++i)
        for (int j = 0; j < N; ++j)
            cin >> Res[i][j];
    vector<vector<int> > Ta(Res);
    vector<vector<int> > Tb(Res);
    for (int k = M; k > 1; --k) {
        for (int i = 0; i < N; ++i)
            for (int j = 0; j < N; ++j) {
                Res[i][j] = 0;
                for (int l = 0; l < N; ++l)
                    Res[i][j] += Ta[i][l] * Tb[l][j];
            }
        if (k - 1 != 1)
            Tb.assign(Res.begin(), Res.end());
    }
    if (M == 0)
        for (int i = 0; i < N; ++i)
            for (int j = 0; j < N; ++j)
                Res[i][j] = i == j;
    for (int i = 0; i < N; ++i) {
        for (int j = 0; j < N; ++j)
            cout << Res[i][j] << " ";
        cout << endl;
    }
    return 0;
}
```

