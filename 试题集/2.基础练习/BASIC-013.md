# BASIC-13 数列排序

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 给定一个长度为n的数列，将这个数列按从小到大的顺序排列。

## 输入格式

> 第一行为一个整数n。
> 第二行包含n个整数，为待排序的数，每个整数的绝对值小于10000。

## 输出格式

> 输出一行，按从小到大的顺序输出排序后的数列。

## 样例输入

> 5
> 8 3 6 4 9

## 样例输出

> 3 4 6 8 9

## 数据规模与约定

> 1<=n<=200

## 解题思路

> 可以自己写排序算法，也可以直接使用STL中的排序算法。

## 通过代码

```cpp
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    vector<int> number;
    int n, num;
    cin >> n;
    for (int i = 0; i < n; ++i) {
        cin >> num;
        number.push_back(num);
    }
    sort(number.begin(), number.end());
    for (int i = 0; i < n; ++i)
        cout << number[i] << " ";
    return 0;
}
```

