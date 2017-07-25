# 桶排序（Bucket Sort）
## 1.算法描述
桶排序是计数排序的升级版。它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定。桶排序 (Bucket sort)的工作的原理：假设输入数据服从均匀分布，将数据分到有限数量的桶里，每个桶再分别排序（有可能再使用别的排序算法或是以递归方式继续使用桶排序进行排序）。
## 2.算法实现
* 设置一个定量的数组当作空桶
* 遍历输入数据，并且把数据一个一个放到对应的桶里去
* 对每个不是空的桶进行排序
* 从不是空的桶里把排好序的数据拼接起来
## 3.Javascript 代码实现
```javascript
function bucketSort(arr, num) {
  if (arr.length <= 1) {
    return arr;
  }
  var len = arr.length,
    buckets = [],
    result = [],
    min = arr[0],
    max = arr[0],
    regex = '/^[1-9]+[0-9]*$/',
    space, n = 0;
  num = num || ((num > 1 && regex.test(num)) ? num : 10);
  for (var i = 1; i < len; i++) {
    min = min <= arr[i] ? min : arr[i];
    max = max >= arr[i] ? max : arr[i];
  }
  //求出每一个桶的数值范围
  space = (max - min + 1) / num;
  //将数值装入桶中
  for (var j = 0; j < len; j++) {
    //找到相应的桶序列
    var index = Math.floor((arr[j] - min) / space);
    //判断是否桶中已经有数值
    if (buckets[index]) {
      //数组从小到大排列
      var k = buckets[index].length - 1;
      while (k >= 0 && buckets[index][k] > arr[j]) {
        buckets[index][k + 1] = buckets[index][k];
        k--
      }
      buckets[index][k + 1] = arr[j];
    } else {
      //新增数值入桶，暂时用数组模拟链表
      buckets[index] = [];
      buckets[index].push(arr[j]);
    }
  }
  //开始合并数组
  var n = 0;
  while (n < num) {
    result = result.concat(buckets[n]);
    n++;
  }
  return result;
}
```
## 4.算法分析
桶排序最好情况下使用线性时间O(n)，桶排序的时间复杂度，取决与对各个桶之间数据进行排序的时间复杂度，因为其它部分的时间复杂度都为O(n)。很显然，桶划分的越小，各个桶之间的数据越少，排序所用的时间也会越少。但相应的空间消耗就会增大。
* 最佳情况：T(n) = O(n+k)
* 最差情况：T(n) = O(n+k)
* 平均情况：T(n) = O(n2)
