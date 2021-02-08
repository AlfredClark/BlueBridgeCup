# BEGIN-4 Fibonacci数列

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> Fibonacci数列的递推公式为：Fn=Fn-1+Fn-2，其中F1=F2=1。
>
> 当n比较大时，Fn也非常大，现在我们想知道，Fn除以10007的余数是多少。

## 输入格式

> 输入包含一个整数n。

## 输出格式

> 输出一行，包含一个整数，表示Fn除以10007的余数。 

## 样例输入

> 10

## 样例输出

> 55

## 数据规模与约定

> 1 <= n <= 1,000,000。

## 解题思路

> 使用递归，同时每一步取其对10007的余数可以防止数据溢出

## 通过代码

```cpp
#include <iostream>

using namespace std;

int N = 0;

int fibonacci(int a, int b, int n) {
    return (n >= N ? a + b : fibonacci(b, (a + b) % 10007, n + 1)) % 10007;
}

int main() {
    cin >> N;
    cout << (N <= 2 ? 1 : fibonacci(1, 1, 3));
    return 0;
}
```

