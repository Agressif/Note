# 归并排序（Merge Sort）
## 1.算法描述
归并排序是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。归并排序是一种稳定的排序方法。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为2-路归并。
## 2.算法实现
* 把长度为n的输入序列分成两个长度为n/2的子序列
* 对这两个子序列分别采用归并排序
* 将两个排序好的子序列合并成一个最终的排序序列
## 3.Javascript 代码实现
```javascript
function mergeSort(arr){
  var len = arr.length;
  if(len<2){
    return arr;
  }
  var middle = parseInt(len/2),
      left = arr.slice(0, middle);
      right = arr.slice(middle);
  return merge(mergeSort(left), mergeSort(right));
}
function merge(left, right){
  var result = [];
  while(left.length && right.length) {
    if(left[0] <= right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }
  while(left.length)
    result.push(left.shift());
  while(right.length)
    result.push(right.shift());
  return result;
}
```
## 4.算法分析
* 最佳情况：T(n) = O(n)
* 最差情况：T(n) = O(nlogn)
* 平均情况：T(n) = O(nlogn)
