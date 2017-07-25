# 基数排序（Radix Sort）
## 1.算法描述
基数排序是按照低位先排序，然后收集；再按照高位排序，然后再收集；依次类推，直到最高位。有时候有些属性是有优先级顺序的，先按低优先级排序，再按高优先级排序。最后的次序就是高优先级高的在前，高优先级相同的低优先级高的在前。基数排序基于分别排序，分别收集，所以是稳定的。
## 2.算法实现
* 取得数组中的最大数，并取得位数
* arr为原始数组，从最低位开始取每个位组成radix数组
* 对radix进行计数排序（利用计数排序适用于小范围数的特点）
## 3.Javascript 代码实现
```javascript
function radixSort(arr, maxDigit) {
  var mod = 10;
  var dev = 1;
  var counter = [];
  for (var i = 0; i < maxDigit; i++, dev *= 10, mod *= 10) {
    for (var j = 0; j < arr.length; j++) {
      var bucket = parseInt((arr[j] % mod) / dev);
      if (counter[bucket] == null) {
        counter[bucket] = [];
      }
      counter[bucket].push(arr[j]);
    }
    var pos = 0;
    for (var j = 0; j < counter.length; j++) {
      var value = null;
      if (counter[j] != null) {
        while ((value = counter[j].shift()) != null) {
          arr[pos++] = value;
        }
      }
    }
  }
  return arr;
}
```
## 4.算法分析
* 最佳情况：T(n) = O(n * k)
* 最差情况：T(n) = O(n * k)
* 平均情况：T(n) = O(n * k)

## 5.基数排序 vs 计数排序 vs 桶排序

这三种排序算法都利用了桶的概念，但对桶的使用方法上有明显差异：
* 基数排序：根据键值的每位数字来分配桶
* 计数排序：每个桶只存储单一键值
* 桶排序：每个桶存储一定范围的数值
