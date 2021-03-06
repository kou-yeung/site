# cyl_bessel_i
* cmath[meta header]
* function[meta id-type]
* std[meta namespace]
* [mathjax enable]
* cpp17[meta cpp]

```cpp
namespace std {
float cyl_bessel_if(float nu, float x);
double cyl_bessel_i(double nu, double x);
long double cyl_bessel_il(long double nu, long double x);
}
```

## 概要
第一種変形ベッセル関数 (modified Bessel functions of the first kind) を求める。


## 戻り値
引数 `nu`, `x` の第一種変形ベッセル関数
$$
I_\nu(x) = i^{-\nu} J_\nu(ix) = \sum_{k=0}^\infty \frac{1}{k! \Gamma(\nu + k + 1)} \left( \frac{x}{2} \right)^{\nu + 2k}
\quad \text{for } x \ge 0
$$
を返す。
$J$ は第一種ベッセル関数 ([`cyl_bessel_j`](cyl_bessel_j.md)) である。


## 備考
`nu >= 128` の場合、この関数の呼び出しの効果は実装定義である。


## 例
```cpp example
#include <cmath>
#include <iostream>

void p(double nu) {
  for (double x : {0, 1, 2})
    std::cout << "cyl_bessel_i(" << nu << ", " << x << ") = " << std::cyl_bessel_i(nu, x) << "\n";
  std::cout << "\n";
}

int main() {
  p(0);
  p(1);
  p(2);
}
```
* std::cyl_bessel_i[color ff0000]

### 出力例
```
cyl_bessel_i(0, 0) = 1
cyl_bessel_i(0, 1) = 1.26607
cyl_bessel_i(0, 2) = 2.27959

cyl_bessel_i(1, 0) = 0
cyl_bessel_i(1, 1) = 0.565159
cyl_bessel_i(1, 2) = 1.59064

cyl_bessel_i(2, 0) = 0
cyl_bessel_i(2, 1) = 0.135748
cyl_bessel_i(2, 2) = 0.688948

```


## バージョン
### 言語
- C++17

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 7.1.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


### 備考
#### GCC (libstdc++)
GCC 7.1.0–8.0.0 では `nu < 0` のときに [`std::domain_error`](/reference/stdexcept.md) を送出する


## 関連項目
* 第一種ベッセル関数 [`cyl_bessel_j`](cyl_bessel_j.md)
* 第二種変形ベッセル関数 [`cyl_bessel_k`](cyl_bessel_k.md)


## 参照
- [N3060 JTC1.22.29124 Programming Language C++ — Special Math Functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3060.pdf)
- [WG21 P0226R1 Mathematical Special Functions for C++17, v5](https://isocpp.org/files/papers/P0226R1.pdf)
- [ISO/IEC 29124:2010 Information technology -- Programming languages, their environments and system software interfaces -- Extensions to the C++ Library to support mathematical special functions](https://www.iso.org/standard/50511.html)
