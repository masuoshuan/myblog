title: 常用排序算法学习
date: 2016-07-08 22:39:24
tags: 算法
categories: algorithm
---
** {{ title }}：** <Excerpt in index | 首页摘要>
    程序员各种排序算法，算法的实现和分析
 <!-- more -->
<The rest of contents | 余下全文>

## 排序算法的分类
1. 排序分内排序和外排序。
2. 内排序:指在排序期间数据对象全部存放在内存的排序。
3. 外排序:指在排序期间全部对象个数太多,不能同时存放在内存,必须根据排序过程的要求,不断在内、外存之间移动的排序。
4. 内排序的方法有许多种,按所用策略不同,可归纳为五类:插入排序、选择排序、交换排序、归并排序、分配排序和计数排序。
5. 插入排序主要包括直接插入排序，折半插入排序和希尔排序两种;
6. 选择排序主要包括直接选择排序和堆排序;
7. 交换排序主要包括冒泡排序和快速排序;
8. 归并排序主要包括二路归并(常用的归并排序)和自然归并。
9. 分配排序主要包括箱排序和基数排序


## 冒泡排序
- 冒泡排序就是把小的元素往前调或者把大的元素往后调。比较是相邻的两个元素比较，交换也发生在这两个元素之间。所以，如果两个元素相等，是不用交换的；如果两个相等的元素没有相邻，那么即使通过前面的两两交换把两个相邻起来，这时候也不会交换，所以相同元素的前后顺序并没有改变，所以冒泡排序是一种稳定排序算法
```js
// js代码
function sort(arr) {
if (arr.length == 0) {
    return [];
}
var length = arr.length;
for (var i = 0; i < length; i++) {
        for (var j = 0; j < length - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                var temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                console.log(arr);
            }
        }
    }
}

```


## 快速排序
- 快速排序是对冒泡排序的一种改进。它的基本思想是：通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列.
- 时间复杂度：O（n*lgn）最坏：O（n^2）空间复杂度：O（n*lgn）

```js
// js递归实现
function quickSort(arr) {
    if (arr.length == 0) {
        return [];
    }
    var left = [];
    var right = [];
    var pivot = arr[0];
    for (var i = 1; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }
    return quickSort(left).concat(pivot, quickSort(right));
}
var a = [];
for (var i = 0; i < 10; ++i) {
    a[i] = Math.floor((Math.random() * 100) + 1);
}
console.log(a);
console.log(quickSort(a));
```
## 直接插入排序  
- 直接插入排序(straight insertion sort)的作法是：每次从无序表中取出第一个元素，把它插入到有序表的合适位置，使有序表仍然有序.

```js
function insertionSort(arr) {
    var temp, inner;
    for (var outer = 1; outer <= arr.length - 1; ++outer) {
        temp = arr[outer];
        inner = outer;
        while (inner > 0 && (arr[inner - 1] >= temp)) {
            arr[inner] = arr[inner - 1];
            --inner;
        }
        arr[inner] = temp;
    }
    return arr;
}
var a = [];
for (var i = 0; i < 10; ++i) {
    a[i] = Math.floor((Math.random() * 100) + 1);
}
console.log(a);
console.log(insertionSort(a));
```

## 折半插入排序
- 折半插入排序算法的具体操作为：在将一个新元素插入已排好序的数组的过程中，寻找插入点时，将待插入区域的首元素设置为a[low],末元素设置为 a[high]，则轮比较时将待插入元素与a[m],其中m=(low+high)/2相比较,如果比参考元素小，则选择a[low]到a[m-1]为新 的插入区域(即high=m-1)，否则选择a[m+1]到a[high]为新的插入区域（即low=m+1），如此直至low<=high不成 立，即将此位置之后所有元素后移一位，并将新元素插入a[high+1]


## 希尔排序
- 先取一个小于n的整数d1作为第一个增量，把文件的全部记录分成d1个组。所有距离为dl的倍数的记录放在同一个组中。先在各组内进行直接插入 排序；然后，取第二个增量d2<d1重复上述的分组和排序，直至所取的增量dt=1(dt<dt-l<…<d2<d1)， 即所有记录放在同一组中进行直接插入排序为止。
- 该方法实质上是一种分组插入方法。插入排序（Insertion Sort）的一个重要的特点是，如果原始数据的大部分元素已经排序，那么插入排序的速度很快（因为需要移动的元素很少）。从这个事实我们可以想到，如果原 始数据只有很少元素，那么排序的速度也很快。－－希尔排序就是基于这两点对插入排序作出了改进。


## 直接选择排序
- 直接选择排序是给每个位置选择当前元素最小的，比如给第一个位置选择最小的，在剩余元素里面给第二个元素选择第二小的，依次类推，直到第n-1个元素，第n个 元素不用选择了，因为只剩下它一个最大的元素了。那么，在一趟选择，如果当前元素比一个元素小，而该小的元素又出现在一个和当前元素相等的元素后面，那么 交换后稳定性就被破坏了。比较拗口，举个例子，序列5 8 5 2 9，我们知道第一遍选择第1个元素5会和2交换，那么原序列中2个5的相对前后顺序就被破坏了，所以选择排序不是一个稳定的排序算法。时间复杂度是O(n^2)


## 堆排序
- 我们知道堆的结构是节点i的孩子为2*i和2*i+1节点，大顶堆要求父节点大于等于其2个子节点，小顶堆要求父节点小于等于其2个子节点。在一个长为n 的序列，堆排序的过程是从第n/2开始和其子节点共3个值选择最大(大顶堆)或者最小(小顶堆),这3个元素之间的选择当然不会破坏稳定性。但当为n /2-1, n/2-2, ...1这些个父节点选择元素时，就会破坏稳定性。有可能第n/2个父节点交换把后面一个元素交换过去了，而第n/2-1个父节点把后面一个相同的元素没 有交换，那么这2个相同的元素之间的稳定性就被破坏了。所以，堆排序不是稳定的排序算法。



## 二路归并排序
- 归并排序是把序列递归地分成短序列，递归出口是短序列只有1个元素(认为直接有序)或者2个序列(1次比较和交换),然后把各个有序的段序列合并成一个有 序的长序列，不断合并直到原序列全部排好序。可以发现，在1个或2个元素时，1个元素不会交换，2个元素如果大小相等也没有人故意交换，这不会破坏稳定 性。那么，在短的有序序列合并的过程中，稳定是是否受到破坏？没有，合并过程中我们可以保证如果两个当前元素相等时，我们把处在前面的序列的元素保存在结 果序列的前面，这样就保证了稳定性。所以，归并排序也是稳定的排序算法。