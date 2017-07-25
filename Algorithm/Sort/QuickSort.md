# 快速排序（Quick Sort）
## 1.算法描述
快速排序的基本思想：通过一趟排序将待排记录分隔成独立的两部分，其中一部分记录的关键字均比另一部分的关键字小，则可分别对这两部分记录继续进行排序，以达到整个序列有序。
## 2.算法实现
* 从数列中挑出一个元素，称为 “基准”（pivot）
* 重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作
* 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序
## 3.Javascript 代码实现
```javascript
function quickSort(arr){
  if(arr.length <= 1){
    return arr;
  }
  // 选择基准
  var pivotIndex = Math.floor(arr.length/2);
  var pivot = arr.splice(pivotIndex, 1)[0];
  // 定义两个空数组，存放子集
  var left = [];
  var right = [];
  for (var i = 0; i < arr.length; i++){
　　if (arr[i] < pivot) {
　　　left.push(arr[i]);
　　} else {
　　　right.push(arr[i]);
　　}
　}
  return quickSort(left).concat([pivot], quickSort(right));
}
```
## 4.算法分析
* 最佳情况：T(n) = O(nlogn)
* 最差情况：T(n) = O(n2)
* 平均情况：T(n) = O(nlogn)
