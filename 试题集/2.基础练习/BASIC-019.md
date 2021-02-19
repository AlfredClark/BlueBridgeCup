# BASIC-19 完美的代价

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 回文串，是一种特殊的字符串，它从左往右读和从右往左读是一样的。小龙龙认为回文串才是完美的。现在给你一个串，它不一定是回文的，请你计算最少的交换次数使得该串变成一个完美的回文串。
> ​交换的定义是：交换两个相邻的字符
> ​例如mamad
> ​第一次交换 ad : mamda
> ​第二次交换 md : madma
> ​第三次交换 ma : madam (回文！完美！)

## 输入格式

> 第一行是一个整数N，表示接下来的字符串的长度(N <= 8000)
> 第二行是一个字符串，长度为N.只包含小写字母

## 输出格式

> 如果可能，输出最少的交换次数。
> 否则输出Impossible

## 样例输入

> 5
> mamad

## 样例输出

> 3

## 数据规模与约定

> <无>

## 解题思路

> 使用贪心算法原理，通过局部最优达到全局最优，根据题意，要通过交换使字符串回文有多种情况，这里采用以最左侧为基准的方式，从左向右遍历字符，针对每一个左侧的字符，通过反向遍历寻找最靠近右侧的相同字符，同时在寻找时统计将该字符交换到最右侧需要的交换次数，同时应该特别注意单个字符的情况，对于单个字符要做好标记，整个字符串中只允许有一个奇数数量的字符，在该情况下，需要移动的次数为剩余字符串长度的一半（向下取整）。

## 通过代码

```cpp
#include <iostream>

using namespace std;

int main() {
    string str;
    bool flag = false;
    int cost = 0, n = 9, c;
    cin >> n >> str;
    string::iterator left = str.begin(), right = str.end() - 1;
    while (left != str.end()) {
        c = 0;
        while (left < right) {
            if (*left == *right) {
                str.erase(right, right + 1);
                break;
            }
            right--;
            c++;
        }
        if (left != right)
            cost += c;
        else if (!flag) {
            flag = true;
            cost += int((str.end() - left) / 2);
        } else {
            cout << "Impossible" << endl;
            return 0;
        }
        left++;
        right = str.end() - 1;
    }
    cout << cost << endl;
    return 0;
}
```

