# 甚麼是演算法

## 廣義
演算法是解決某一問題的一步一步程序
(a step-by-step procedure for solving a problem)

## 狹義
演算法是一個由一些步驟所構成的集合，依循這些步驟得以解決數學問題或完成計算機進程
(a set of steps that are followed in order to solve a mathematical problem or to complete a computer process)

## 流程圖 (flowchart) 是演算法

## 計算機科學 嚴謹定義
由有限(finite)步驟(step)所構成的集合，依照給定輸入(input)依序執行每個明確(definite)且有效(effective) 的步驟，以便能夠解決特定的問題；而步驟的執行必定會終止(terminate)，並產生輸出(output) 。

## 特性
- 指定輸入(input)：演算法必須指定輸入，可以由外界輸入0 個、1 個或多個資料。
- 具有輸出(output)：演算法必定有至少1 個以上的輸出。
- 有限性(finiteness)：演算法步驟的個數必須是有限的，而且步驟的執行最後會終止(terminate)。
- 明確性(definiteness)：演算法的每個步驟都必須是明確(definite) 而不含糊的(unambiguous)。
- 有效性(effectiveness)：演算法的每個步驟必須是有效的(effective) 或說是可行的(feasible)。

# 如何表示演算法 Example : Euclidean algorithm

## 流程圖，Pseudo Code

## 自然語言

```
歐幾里德演算法:
問題：給定二個正整數m及n，找出此二數的最大公因數GCD(也就是能同時整除m及n的最大正整數)
解法：
步驟1.[找出餘數] 求出m除以n的餘數，並記錄於r。
步驟2.[餘數為0嗎?] 如果r=0則停止，輸出n為GCD。
步驟3.[換被除數與除數] 設定m=n,n=r，並跳至步驟1。
```

## C++

``` cpp
#include <iostream>
using namespace std;
int EuclidGCD(int m, int n){
  int r=m%n;
  while (r!=0) {
    m=n;
    n=r;
    r=m%n;
  }
  return n;
}
int main() {
  int m,n;
  cout<<"請輸入二個正整數m與n: ";
  cin>>m>>n;
  cout<<"整數"<<m<<"與整數"<<n<<"的最大公因數為"<<EuclidGCD(m,n);
}
```
