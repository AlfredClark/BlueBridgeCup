# BASIC-18 矩形面积交

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 平面上有两个矩形，它们的边平行于直角坐标系的X轴或Y轴。对于每个矩形，我们给出它的一对相对顶点的坐标，请你编程算出两个矩形的交的面积。

## 输入格式

> 输入仅包含两行，每行描述一个矩形。
> 在每行中，给出矩形的一对相对顶点的坐标，每个点的坐标都用两个绝对值不超过10^7的实数表示。

## 输出格式

> 输出仅包含一个实数，为交的面积，保留到小数后两位。

## 样例输入

> 1 1 3 3
> 2 2 4 4

## 样例输出

> 1.00

## 数据规模与约定

> <无>

## 解题思路

> 通过选取最大矩形边界判断两个矩形是否相交，并通过边界极限求出相交部分的长宽，通过iomanip控制输出。

## 通过代码

```cpp
#include <cmath>
#include <vector>
#include <iomanip>
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    vector<double> X(4, 0), Y(4, 0);
    for (int i = 0; i < 4; ++i)
        cin >> X[i] >> Y[i];
    double W, H, w, h;
    W = *max_element(X.begin(), X.end()) - *min_element(X.begin(), X.end());
    H = *max_element(Y.begin(), Y.end()) - *min_element(Y.begin(), Y.end());
    w = fabs(X[0] - X[1]) + fabs(X[2] - X[3]);
    h = fabs(Y[0] - Y[1]) + fabs(Y[2] - Y[3]);
    W = w > W ? w - W : 0;
    H = h > H ? h - H : 0;
    cout << fixed << setprecision(2) << W * H;
    return 0;
}
```

