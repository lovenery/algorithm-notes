# 比較好的版本

ref:http://notepad.yehyeh.net/Content/Algorithm/Sort/Heap/Heap.php

```cpp
#include <iostream>

using namespace std;

void heap(int *a, int root, int length) {
  int leftChildIndex = root * 2 + 1;  // root的左下元素
  int rightChildIndex = root * 2 + 2; // root的右下元素
  int maxNode = -1;

  // 找出最大的節點是root還是樹枝
  maxNode = root;
  if (leftChildIndex < length && a[leftChildIndex] > a[root]) {
    maxNode = leftChildIndex;
  }
  if (rightChildIndex < length && a[rightChildIndex] > a[maxNode]) {
    maxNode = rightChildIndex;
  }

  // 如果最大值不是root,交換root跟元素得值,並遞迴向下做heap
  if (maxNode != root) {
    swap(a[root], a[maxNode]);
    heap(a, maxNode, length);
  }
}

void heapSort(int *a, int length) {
  cout << "初始陣列: ";
  for (int i = 0; i < length; i++) {
    cout << a[i] << " ";
  }

  // 二元樹有floor(n/2)個節點
  // 由最後面的節點做堆積, -1是因為頂端的index是0
  // if length = 10 , i = 4,3,2,1,0
  for (int i = length / 2 - 1; i >= 0; i--) {
    heap(a, i, length);
  }

  cout << endl << "最大堆積: ";
  for (int i = 0; i < length; i++) {
    cout << a[i] << " ";
  }

  // 排序
  // length越來越短, -1是因為頂端的index是0
  for (int i = length - 1; i > 0; i--) {
    swap(a[0], a[i]); // 將最大值換到最後面
    heap(a, 0, i);    // 再做堆積
  }

  cout << endl << "堆積排序: ";
  for (int i = 0; i < length; i++) {
    cout << a[i] << " ";
  }
}

int main() {

  int arr[10] = {14, 51, 92, 79, 45, 2, 75, 70, 3, 57};

  heapSort(arr, 10);

  return 0;
}

// Sample Output
// 初始陣列: 14 51 92 79 45 2 75 70 3 57
// 最大堆積: 92 79 75 70 57 2 14 51 3 45
// 堆積排序: 2 3 14 45 51 57 70 75 79 92
```



# 以前寫的

```
Algorithm HeapSort(A,n)
Input: n個整數的array A
Output: A (由小到大排)

// 先建立最大堆積樹
toSortArray[n+1] // 宣告一個為n+1大小的陣列
toSortArray[0] = 0 // 其中陣列[0]是存放目前關注長度的值
for i = 1 to length
    toSortArray[i] = A[i-1]
    toSortArray[0]++ // 儲存這個array有幾個數字
    index = i // 第一次for不會進入while
    while ( toSortArray[index/2]<toSortArray[index] && (index/2)!=0 )
        swap(toSortArray[index], toSortArray[index/2])
        index = index / 2 // 換上去的時候變成上面的節點
    end while
end for

// HeapSort
while ( toSortArray[0]>0 ) //等於0代表全部都排完了
    swap(toSortArray[1], toSortArray[toSortArray[0]]) // 交換 最初跟最後的資料

    // 再變成最大堆積樹, 此時的最後一個數不用加入排序
    for i = 1 to toSortArray[0]-1
        index = i // 第一次for不會進入while
        while ( toSortArray[index/2]<toSortArray[index] && (index/2)!=0 )
            swap(toSortArray[index], toSortArray[index/2])
            index = index / 2 // 換上去的時候變成上面的節點
        end while
    end for

    toSortArray[0]-- // 數量減一 最後面的數字已經排完了

end while

// Ans Copy to A[]
for i = 1 to length
    A[i-1] = toSortArray[i]
end for

return A
```

```cpp
void heapSort(int *a,int length)
{
    // create max heap tree
    int toSortArray[length+1];
    toSortArray[0] = 0;
    for(int i = 1; i < length+1; i++)
    {
        toSortArray[i] = a[i-1];
        toSortArray[0]++; //holds the number of values in the array;
        int index = i;
        while(toSortArray[index/2]<toSortArray[index] && (index/2)!=0)
        {
            int temp = toSortArray[index/2];
            toSortArray[index/2] = toSortArray[index];
            toSortArray[index] = temp;
            index=index/2;
        }
    }

    // heap sort
    while(toSortArray[0]>0)
    {
        // swap first and last data
        int temp = toSortArray[1];
        toSortArray[1] = toSortArray[toSortArray[0]];
        toSortArray[toSortArray[0]] = temp;

        // then turn it to heap tree
        for(int i = 1; i < toSortArray[0]; i++)
        {
            int index = i;
            while(toSortArray[index/2]<toSortArray[index] && (index/2)!=0)
            {
                int temp1 = toSortArray[index/2];
                toSortArray[index/2] = toSortArray[index];
                toSortArray[index] = temp1;
                index=index/2;
            }
        }

        // numbers--
        toSortArray[0]--;
    }

    // output data
    for(int i=0; i<length; i++)
    {
        a[i]=toSortArray[i+1];
    }
}
```
