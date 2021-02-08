# BEGIN-3 圆的面积

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 给定圆的半径r，求圆的面积。

## 输入格式

> 输入包含一个整数r，表示圆的半径。

## 输出格式

> 输出一行，包含一个实数，四舍五入保留小数点后7位，表示圆的面积。 

## 样例输入

> 4

## 样例输出

> 50.2654825

## 数据规模与约定

> 1 <= r <= 10000。

## 解题思路

> 本题对精度要求较高，请注意π的值应该取较精确的值。atan(1.0) * 4 = pi

## 通过代码

```cpp
#include <cmath>
#include <iomanip>
#include <iostream>

using namespace std;

int main() {
    int r = 0;
    cin >> r;
    cout << fixed << setprecision(7) << atan(1.0) * 4 * r * r; // 固定小数点输出7位小数
    return 0;
}
```

