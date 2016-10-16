# Problem Set 2:

## (A) 在氣泡排序(bubble sort)演算法中，若在某回合中完全沒有任何資料對調，則可推論資料已經排序完成而立即結束演算法執行，這稱為改良氣泡排序(improved bubble sort)演算法。請以虛擬碼描述「改良氣泡排序演算法」。(請注意:在有些文獻中，所謂「氣泡排序演算法」其實指的是「改良氣泡排序演算法」)
ref: http://notepad.yehyeh.net/Content/Algorithm/Sort/Bubble/1.php#

若未排序的資料中，比對時都沒有進行交換位置 ⇒ `flag = false`  
代表資料已排序好,提早結束排序

```rb
Algorithm ImprovedBubbleSort(A,n)
Input: n個整數的array A
Output: A (由小到大排)
flag = true
for i=n-1 to 1 && flag do
    flag = false
    for j=0 to i-1 do
        if A[j]>A[j+1] then
            swap(A[j], A[j+1])
            flag = true
        end if
    end for
end for
return A
```

## (B) 分析改良氣泡排序演算法最佳、最差與平均時間複雜 度

#### 時間複雜度(Time Complexity)  
1. Best Case：$$Ο(n)$$  
當資料的順序恰好為由小到大時  
第一次執行後，未進行任何swap ⇒ 提前結束  
2. Worst Case：$$Ο(n^2)$$  
當資料的順序恰好為由大到小時  
每回合分別執行：n-1、n-2、...、1次  
(n-1) + (n-2) + ... + 1 = n(n-1)/2 ⇒ Ο(n^2)  
3. Average Case：$$Ο(n^2)$$  
第n筆資料，平均比較(n-1)/2次  


## (C) 使用虛擬碼描述堆積排序(heap sort)演算法

```rb
Algorithm HeapSort(A,n)
Input: n個整數的array A
Output: A (由小到大排)

MaxHeapify(A, root, n)
    leftChild = root*2+1
    rightChild = root*2+2
    maxNode = root
    if leftChild < n && A[leftChild] > A[root]
        maxNode = leftChild
    end if
    if rightChild < n && A[rightChild] > A[maxNode]
        maxNode = rightChild
    end if
    if maxNode != root
        swap(A[root], A[maxNode]);
        MaxHeapify(A, maxNode, n);
    end if
end func

MAIN

for i=n/2-1 to 0
    MaxHeapify(A, i, n)
end for

for i=n-1 to 1
    swap(A[0], A[i])
    MaxHeapify(A, 0, i)
end for

return A

END MAIN

```


## (D) 分析堆積排序演算法時間空間複雜度

#### 時間複雜度(Time Complexity)

1. Best Case：Ο(n log n)
2. Worst Case：Ο(n log n)
3. Average Case：Ο(n log n)

> 說明：  
建立MaxHeap： Ο(n)  
執行n-1次Delete Max：(n-1) × Ο(log n) = Ο( n log n)  
Ο(n) + Ο( n log n) = Ο( n log n)

#### 空間複雜度(Space Complexity)：Ο(1)
原地置換(In-Place)

## (E) 使用虛擬碼描述基數(radix sort)演算法

```rb
Algorithm RadixSort(A,n)
Input: n個整數的array A
Output: A (由小到大排)

count[n] = {0}
buckets[n][10]
MAXradix = 100
radix = 1
dataIndex = 0

while radix <= MAXradix

    for i=0 to n-1
        LSD = (A[i]/radix) % 10
        buckets[LSD][count[LSD]] = A[i]
        count[LSD]++
    end for

    radix = radix * 10

    dataIndex = 0
    for i=0 to 10
        if count[i] != 0
            for j=0 to count[i]-1
                A[dataIndex++] = buckets[i][j]
            end for
        end if
        count[i] = 0
    end for

end while


return A
```

## (F) 分析基數排序演算法時間空間複雜度

#### 時間複雜度(Time Complexity)

1. Best Case：Ο(d × (n+r))  
2. Worst Case：Ο(d × (n+r))  
3. Average Case：Ο(d × (n+r))  

> 說明：  
d = 執行回合數  
n = 數列長度  
r = 基數  
每回合將資料分配到桶子需Ο(n)  
每回合將桶子內的資料取出，合併成數列需Ο(r)  
∴每回合需Ο( n + r)

#### 空間複雜度(Space Complexity)：Ο(n × r)
使用二維陣列來當桶子：Ο(n × r)  
n = 數列長度  
r = 基數  
需要r個桶子，每個桶子需可放n筆資料 ⇒ Ο( n × r)  
使用鏈結串列來當桶子：Ο(n)  
n = 數列長度

# Programming Problem Set 2
## (PA) 寫一個程式實作基數排序演算法
[連結](/ch2/radixsort.html)
