# BASIC-5 查找整数

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 给出一个包含n个整数的数列，问整数a在数列中的第一次出现是第几个。

## 输入格式

> 第一行包含一个整数n。
>
> 第二行包含n个非负整数，为给定的数列，数列中的每个数都不大于10000。
>
> 第三行包含一个整数a，为待查找的数。

## 输出格式

> 如果a在数列中出现了，输出它第一次出现的位置(位置从1开始编号)，否则输出-1。

## 样例输入

> 6
> 1 9 4 8 3 9
> 9

## 样例输出

> 2

## 数据规模与约定

> 1 <= n <= 1000。

## 解题思路

> 可以使用查找算法，也可以使用map每输入一个数，对于n较小也可以使用数组

## 通过代码

- 使用map

```cpp
#include <map>
#include <iostream>

using namespace std;

int main() {
    map<int, int> local;
    int n = 0, c = 0;
    cin >> n;
    for (int i = 1; i <= n; ++i) {
        cin >> c;
        if (local.find(c) == local.end())
            local[c] = i;
    }
    cin >> c;
    cout << (local.find(c) == local.end() ? -1: local[c]);
    return 0;
}
```

- 使用数组

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    int local[10001], n = 0, c = 0;
    fill(local, local + 10001, -1);
    cin >> n;
    for (int i = 1; i <= n; ++i) {
        cin >> c;
        if (local[c] == -1)
            local[c] = i;
    }
    cin >> c;
    cout << local[c];
    return 0;
}
```

