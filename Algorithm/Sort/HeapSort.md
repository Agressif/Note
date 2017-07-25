# 堆排序（Heap Sort）
## 1.算法描述
堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。
## 2.算法实现
* 将初始待排序关键字序列(R1,R2….Rn)构建成大顶堆，此堆为初始的无序区
* 将堆顶元素R[1]与最后一个元素R[n]交换，此时得到新的无序区(R1,R2,……Rn-1)和新的有序区(Rn),且满足R[1,2…n-1]<=R[n]
* 由于交换后新的堆顶R[1]可能违反堆的性质，因此需要对当前无序区(R1,R2,……Rn-1)调整为新堆，然后再次将R[1]与无序区最后一个元素交换，得到新的无序区(R1,R2….Rn-2)和新的有序区(Rn-1,Rn)。不断重复此过程直到有序区的元素个数为n-1，则整个排序过程完成
## 3.Javascript 代码实现
```javascript
function heapSort(arr){
  /**
   * 从index开始检查并保持最大堆性质
   * @arr
   * @index 检查的起始下标
   * @heapSize 堆大小
   **/
  function maxHeapify(arr, index, heapSize) {
    var iMax = index,
      iLeft = 2 * index + 1,
      iRight = 2 * (index + 1);
    if (iLeft < heapSize && arr[index] < arr[iLeft]) {
      iMax = iLeft;
    }
    if (iRight < heapSize && arr[iMax] < arr[iRight]) {
      iMax = iRight;
    }
    if (iMax != index) {
      swap(arr, iMax, index);
      maxHeapify(arr, iMax, heapSize); // 递归调整
    }
  }
  function swap(arr, i, j) {
    var temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
  // 创建最大堆
  function buildMaxHeap(arr) {
    var i,
      iParent = Math.floor(arr.length / 2) - 1;
    for (i = iParent; i >= 0; i--) {
      maxHeapify(arr, i, arr.length);
    }
  }
  function sort(arr) {
    buildMaxHeap(arr);
    for (var i = arr.length - 1; i > 0; i--) {
      swap(arr, 0, i);
      maxHeapify(arr, 0, i);
    }
    return arr;
  }
  return sort(arr);
}
```
## 4.算法分析
* 最佳情况：T(n) = O(nlogn)
* 最差情况：T(n) = O(nlogn)
* 平均情况：T(n) = O(nlogn)
