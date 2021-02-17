# BASIC-16 分解质因数

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 求出区间[a,b]中所有整数的质因数分解。

## 输入格式

> 输入两个整数a，b。

## 输出格式

> 每行输出一个数的分解，形如k=a1*a2*a3...(a1<=a2<=a3...，k也是从小到大的)(具体可看样例)

## 样例输入

> 3 10

## 样例输出

> 3=3
> 4=2\*2
> 5=5
> 6=2\*3
> 7=7
> 8=2\*2\*2
> 9=3\*3
> 10=2\*5

## 数据规模与约定

> 2<=a<=b<=10000

## 解题思路

> 数据值较小，可以使用Pollard Rho快速因数分解，或者使用质数表

## 通过代码

> Pollard Rho快速因数分解

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    int a, b, n;
    cin >> a >> b;
    for (int i = a; i <= b; ++i) {
        n = i;
        cout << n << '=';
        for (int j = 2; j <= n; j++)
            while (n != j) {
                if (n % j == 0) {
                    cout << j << '*';
                    n = n / j;
                } else
                    break;
            }
        cout << n << endl;
    }
    return 0;
}

```

> 质数表

```cpp
#include <cstring>
#include <iostream>

using namespace std;

int prime[1500];       // 记录素数列，prime[0]记录素数个数
bool is_prime[10001];  // 筛表

int sieve(int n) {
    memset(prime, 0, sizeof(prime));
    memset(is_prime, true, sizeof(is_prime));
    for (int i = 2; i <= n; i++) {
        if (is_prime[i])
            prime[++prime[0]] = i;
        for (int j = 1; j <= prime[0] && i * prime[j] <= n; ++j) {
            is_prime[i * prime[j]] = false;
            if (i % prime[j] == 0)
                break;
        }
    }
    return prime[0];
}

void decompose(int n){
    cout << n << "=";
    for (int j = 1; j < prime[0] && n > prime[j]; ++j) {
        if (n == j)
            break;
        while (n != prime[j] && n % prime[j] == 0){
            cout << prime[j] << "*";
            n /= prime[j];
        }
    }
    cout << n << endl;
}

int main() {
    sieve(10000);
    int a, b;
    cin >> a >> b;
    for (int i = a; i <= b; ++i) {
        decompose(i);
    }
    return 0;
}

```

