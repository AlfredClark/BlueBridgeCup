# BASIC-12 十六进制转八进制

## 资源限制

>时间限制：1.0s  内存限制：256.0MB

## 问题描述

> 给定n个十六进制正整数，输出它们对应的八进制数。

## 输入格式

> 输入的第一行为一个正整数n 。
> 接下来n行，每行一个由0~9、大写字母A~F组成的字符串，表示要转换的十六进制正整数，每个十六进制数长度不超过100000。

## 输出格式

> 输出n行，每行为输入对应的八进制正整数。

## 样例输入

> 2
> 39
> 123ABC

## 样例输出

> 71
> 4435274

## 数据规模与约定

> 1<=n<=10

## 解题思路

> 先将十六进制数转换成二进制数，再由二进制数转换成八进制。具体的十六进制转换为二进制后，由后向前每取三位即可获得一个对应的八进制数。

## 通过代码

```cpp
#include<iostream>
#include<string>

using namespace std;

int main() {
    int i, N;
    cin >> N;
    while (N--) {
        string OX, OXC, O;
        cin >> OX;
        for (i = 0; i < (int) OX.size(); i++)
            switch (OX[i]) {
                case '0':
                    OXC += "0000";
                    break;
                case '1':
                    OXC += "0001";
                    break;
                case '2':
                    OXC += "0010";
                    break;
                case '3':
                    OXC += "0011";
                    break;
                case '4':
                    OXC += "0100";
                    break;
                case '5':
                    OXC += "0101";
                    break;
                case '6':
                    OXC += "0110";
                    break;
                case '7':
                    OXC += "0111";
                    break;
                case '8':
                    OXC += "1000";
                    break;
                case '9':
                    OXC += "1001";
                    break;
                case 'A':
                    OXC += "1010";
                    break;
                case 'B':
                    OXC += "1011";
                    break;
                case 'C':
                    OXC += "1100";
                    break;
                case 'D':
                    OXC += "1101";
                    break;
                case 'E':
                    OXC += "1110";
                    break;
                case 'F':
                    OXC += "1111";
                    break;
            }
        switch ((int) OXC.size() % 3) {
            case 0:
                break;
            case 1:
                OXC = "00" + OXC;
                break;
            case 2:
                OXC = "0" + OXC;
                break;
        }
        for (i = 0; i <= (int) OXC.size() - 3; i += 3)
            if (OXC[i] == '0')
                if (OXC[i + 1] == '0')
                    if (OXC[i + 2] == '0')
                        O += "0";
                    else
                        O += "1";
                else if (OXC[i + 2] == '0')
                    O += "2";
                else
                    O += "3";
            else if (OXC[i + 1] == '0')
                if (OXC[i + 2] == '0')
                    O += "4";
                else
                    O += "5";
            else if (OXC[i + 2] == '0')
                O += "6";
            else
                O += "7";
        if (O[0] == '0')
            O.erase(0, 1);
        cout << O << endl;
    }
    return 0;
}
```

