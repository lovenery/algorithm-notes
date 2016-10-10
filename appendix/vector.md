```cpp
#include <iostream>
#include <vector>
#include <math.h>

using namespace std;

// n>2
// 檢查是否為質數
bool isPrime(int n)
{
    for(int i = 2; i <= sqrt(n); i++)
    {
        if(n%i==0)
        {
            return false;
        }
    }
    return true;
}

// n>2
// 取得 n 以下(含n)的所有質數
vector<int> getAllPrimeNum(int n)
{
    vector<int> primes;

    for(int i = 2; i <= n; i++)
    {
        if(isPrime(i))
        {
            primes.push_back(i);
        }
    }

    return primes;
}

vector< vector<int> > result;

int main()
{
    int n;
    cin >> n;

    vector<int> v = getAllPrimeNum(n);

    // 存取元素
    cout << v[0] << endl; // 存取索引值為 i 的元素參照。
    cout << v.at(0) << endl; // 存取索引值為 i 的元素的參照，
    cout << v.front() << endl; // 回傳 vector 第一個元素的參照。
    cout << v.back() << endl; // 回傳 vector 最尾元素的參照。

    // loop 1
    for (vector<int>::iterator it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    // loop 2
    for(int i=0; i<v.size(); i++)
    {
        cout << v.at(i) << " ";
    }
    cout << endl;


    // 新增移除元素
    /*
    v.push_back(); // 新增元素至 vector 的尾端，必要時會進行記憶體配置。
    v.pop_back(); // 刪除 vector 最尾端的元素。
    v.insert(); // 插入一個或多個元素至 vector 內的任意位置。
    v.erase(); // 刪除 vector 中一個或多個元素。
    v.clear(); // 清空所有元素。
    */


    // 疊代 (Iterator)
    /*
    vec.begin(); // 回傳一個Iterator，它指向 vector 第一個元素。
    vec.end(); // 回傳一個Iterator，它指向 vector 最尾端元素的下一個位置（請注意：它不是最末元素）。
    vec.rbegin(); // 回傳一個反向Iterator，它指向 vector 最尾端元素的。
    vec.rend(); // 回傳一個Iterator，它指向 vector 的第一個元素。
    */

    // 取得長度/容量的用法
    /*
    vec.size(); // 取得 vector 目前持有的元素個數。
    vec.empty(); // 如果 vector 內部為空，則傳回 true 值。
    vec.capacity(); // 取得 vector 目前可容納的最大元素個數。這個方法與記憶體的配置有關，它通常只會增加，不會因為元素被刪減而隨之減少。
    重新配置／重設長度
    vec.reserve(); // 如有必要，可改變 vector 的容量大小（配置更多的記憶體）。在眾多的 STL 實做，容量只能增加，不可以減少。
    vec.resize(); // 改變 vector 目前持有的元素個數。
    */

    // 空間宣告的方法
    // 預留
    vector<string> a;  // 長度為 0
    a.reserve(65);  // 預留 65 個元素的位置，沒有初始化
    // 調整大小
    vector<string> b;  // 長度為 0
    b.resize(65);  // 預留 65 個元素的位置，呼叫 string 的 default constructor
    b.resize(65,"Q");
    // construct
    vector<string> c(65);  // 長度為 65
    vector<int> v0(10,0); // {0,0,0,0,0,0,0,0,0,0}
    vector<int> vtov(v0.begin(), v0.end());
    // assign
    vector<int> v1;
    v1.assign(10, 0); // v1 設 10 個 0
    v1.assign(v.begin(), v.end()); // v1 複制 v
    v1.assign(v.begin(), v.begin()+5); // 複製 v 前5個元素到 v1
    int arr[] = {0,1,2,3,4};
    v1.assign(arr, arr+5); // 複製 arr 前5個元素到 v1

    return 0;
}
```
