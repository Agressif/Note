# 冒泡排序（Bubble Sort）
## 1.算法描述
冒泡排序是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果它们的顺序错误就把它们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。
## 2.算法实现
* 比较相邻的元素。如果第一个比第二个大，就交换它们两个
* 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数
* 针对所有的元素重复以上的步骤，除了最后一个
* 重复步骤1~3，直到排序完成
## 3.Javascript 代码实现
### (1)bubbleSort_1
```javascript
function bubbleSort1(arr) {
  var len = arr.length;
  for (var i = 0; i < len; i++) {
    for (var j = 0; j < len - 1 - i; j++) {
      if (arr[j] > arr[j+1]) {       
        var temp = arr[j+1];       // 元素交换
        arr[j+1] = arr[j];
        arr[j] = temp;
      }
    }
  }
  return arr;
}
```
### (2)bubbleSort_2
改进冒泡排序： 设置一标志性变量pos,用于记录每趟排序中最后一次进行交换的位置。由于pos位置之后的记录均已交换到位,故在进行下一趟排序时只要扫描到pos位置即可。
```javascript
function bubbleSort2(arr) {
  var i = arr.length - 1;
  while(i > 0) {
    var pos = 0;  // 每趟开始时，无记录交换
    for (var j = 0; j< i; j++)
      if (arr[j]> arr[j+1]) {
        pos = j; //记录交换的位置
        var tmp = arr[j]; 
        arr[j] = arr[j+1];
        arr[j+1] = tmp;
      }
    i = pos; //为下一趟排序作准备
  }
  return arr
}
```
### (3)bubbleSort_3
传统冒泡排序中每一趟排序操作只能找到一个最大值或最小值，考虑利用在每趟排序中进行正向和反向两遍冒泡的方法一次可以得到两个最终值(最大者和最小者)，从而使排序趟数几乎减少了一半。
```javascript
function bubbleSort3(arr) {
  var low = 0;
  var high = arr.length - 1;          //设置变量的初始值
  var tmp,j;
  while (low < high) {
    for (j = low; j < high; ++j) {     //正向冒泡，找到最大者
      if (arr[j] > arr[j+1]) {
        tmp = arr[j]; 
        arr[j] = arr[j+1];
        arr[j+1] = tmp;
      }
      --high;                       //修改high值，前移一位
    }             
    for (j = high; j > low; --j) {      //反向冒泡，找到最小者
      if (arr[j] < arr[j-1]) {
        tmp = arr[j]; 
        arr[j] = arr[j-1];
        arr[j-1] = tmp;
      }
      ++low;                  //修改low值，后移一位
    }
  }
  return arr;
}
```
