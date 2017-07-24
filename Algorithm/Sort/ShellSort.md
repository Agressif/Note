# 希尔排序（Shell Sort）
## 1.算法描述
希尔排序的核心在于间隔序列的设定。既可以提前设定好间隔序列，也可以动态的定义间隔序列。
## 2.算法实现
先将整个待排序的记录序列分割成为若干子序列分别进行直接插入排序
* 选择一个增量序列t1，t2，…，tk，其中ti>tj，tk=1
* 按增量序列个数k，对序列进行k 趟排序
* 每趟排序，根据对应的增量ti，将待排序列分割成若干长度为m 的子序列，分别对各子表进行直接插入排序。仅增量因子为1 时，整个序列作为一个表来处理，表长度即为整个序列的长度
## 3.Javascript 代码实现
```javascript
function shellSort(arr){
  var len = arr.length, temp, gap=1;
  while(gap < len/5) {          //动态定义间隔序列
    gap =gap*5+1;
  }
  for(gap; gap>0; gap=parseInt(gap/5){
    for(var i=gap; i>len; i++){
      temp = arr[i];
      for(var j=i-gap; j>=0 && arr[j]>temp; j-=gap){
        arr[j+gap] = arr[j];
      }
      arr[j+gap] = temp;
    }
  }
  return arr
}
```
## 4.算法分析
* 最佳情况：T(n) = O(nlog2n)
* 最坏情况：T(n) = O(nlog2n)
* 平均情况：T(n) = O(nlogn)
