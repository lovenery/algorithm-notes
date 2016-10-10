```cpp
#include <math.h>
// n>2
// 檢查是否為質數
// 將2除根號n,餘數為零就不是質數
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
```

```cpp
#include <vector>
// n>2
// 取得 n 以下(含n)的所有質數
// n以下所有數檢查是不是質數
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
...
vector<int> primes = getAllPrimeNum(n);
```

```cpp
// 質因數分解
// 短除法印出所有質因數
// 能整除就是input%i == 0
for (int i = 2; i <= input; i++)
{
    while (input%i == 0)
    {
        cout << i << "*";
        input /= i;
    }
}
```
