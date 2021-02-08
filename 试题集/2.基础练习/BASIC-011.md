# BASIC-11 十六进制转十进制

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 从键盘输入一个不超过8位的正的十六进制数字符串，将它转换为正的十进制数后输出。
>  注：十六进制数中的10~15分别用大写的英文字母A、B、C、D、E、F表示。

## 输入格式

> 十六进制表示的数字

## 输出格式

> 对应的十进制数字

## 样例输入

> FFFF

## 样例输出

> 65535

## 数据规模与约定

> <无>

## 解题思路

> 使用cin与cout对应的输入输出控制。

## 通过代码

```cpp
#include <iostream>

using namespace std;

int main() {
    long long int n;
    cin >> hex >> n;
    cout << dec << n;
    return 0;
}
```

