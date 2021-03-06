# 插入排序（Insertion Sort）
## 1.算法描述
插入排序（Insertion-Sort）的算法描述是一种简单直观的排序算法。它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。插入排序在实现上，通常采用in-place排序（即只需用到O(1)的额外空间的排序），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。
## 2.算法实现
* 从第一个元素开始，该元素可以认为已经被排序
* 取出下一个元素，在已经排序的元素序列中从后向前扫描
* 如果该元素（已排序）大于新元素，将该元素移到下一位置
* 重复步骤3，直到找到已排序的元素小于或者等于新元素的位置
* 将新元素插入到该位置后
* 重复步骤2~5
## 3.Javascript 代码实现
```javascript
function insertionSort(arr) {
  //假设第0个元素是一个有序的数列，第1个以后的是无序的序列
  //所以从第1个元素开始将无序数列的元素插入到有序数列中
  for(var i=1; i<arr.length; i++) {
     var key = arr[i];
     var j = i-1;
     while(j>=0 && arr[j]>key) {
       arr[j+1] = arr[j];
       j--;
     }
     arr[j+1] = key;
  }
  return arr
}
```
## 4.算法分析
* 最佳情况：输入数组按升序排列。T(n) = O(n)
* 最差情况：输入数组按降序排列。T(n) = O(n2)
* 平均情况：T(n) = O(n2)
