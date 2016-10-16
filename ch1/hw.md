(A) 使用虛擬瑪(pseudo code)寫一個演算法，輸入一個整數n(n>2)並輸出小於n的最大因數(factor) (Write an algorithm using the pseudo code to input an integer n and output the n's largest factor that is less than n.)

```
Input: n (n>2)
Output: Max
Max = 1
FOR i = 1 to n
    IF n%i == 0 && i>Max
        Max = i
    END IF
END FOR
Print Max
```

(B) 使用虛擬 瑪(pseudo code)寫一個演算法，輸入一個整數n(n>2)並輸出所有n除了本身以外的正因數(factor)總和 (Write an algorithm using the pseudo code to input an integer n and output the total summation of all n's factors except n.)

(C) 使用虛擬瑪(pseudo code)寫一個演算法，輸入整數n及m(n>m>2)，輸出所有比n小並大於m的n的因數(factor)總和，若無此因數則輸出0 (Write an algorithm using the pseudo code to input integers n and m, and output all n's factors larger than m and less than n.)

(D) 使用虛擬瑪(pseudo code)寫一個演算法，輸入一個整數n並判斷n是否為完美數(perfect number) (Write an algorithm using the pseudo code to input an integer n and output (decide) if n is a perfect number.)

(E) 使用虛擬瑪(pseudo code)寫 一個演算法，輸入一個整數n(n>0)並判斷n是否為快樂數(happy number) (Write an algorithm to input an integer n and output (decide) if n is a happy number.)
註: 快樂數有以下的特性：在給定的進位制下，該數字所有數位(digits)的平方和，得到的新數再次求所有數位的平方和，如此重複進行，最終結果必為1。例 如，以十進位為例：
28 → 22+82= 68 → 62+82=100 → 12+02+02=1，因此28是快樂數

(F) 使用虛擬瑪(pseudo code)寫一個演算法，以輸入一個具有n個元素的集合S並輸出S的幂集(pwoer set) (Write an algorithm to input a set S of n elements and output the power set of S.)
