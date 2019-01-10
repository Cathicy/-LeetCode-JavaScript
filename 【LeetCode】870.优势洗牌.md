
#### 优势洗牌
#### 来源：[LeetCode No.870](https://leetcode-cn.com/problems/advantage-shuffle/description/)
#### 问题描述：
给定两个大小相等的数组 A 和 B，A 相对于 B 的优势可以用满足 A[i] > B[i] 的索引 i 的数目来描述。

返回 A 的任意排列，使其相对于 B 的优势最大化。
#### 示例：
示例 1：

> 输入：A = [2,7,11,15], B = [1,10,4,11] 
> 输出：[2,11,7,15]

示例 2：

> 输入：A = [12,24,8,32], B = [13,25,32,11] 
> 输出：[24,32,8,12]

#### 提示：
1. `1 <= A.length = B.length <= 10000`
2. `0 <= A[i] <= 10^9`
3. `0 <= B[i] <= 10^9`
#### 思路分析：
思路类似于田忌赛马，用A数组中的最小的数据，对冲B数组中的比较大的数据，剩下A数组中的数据挑选略大于B数组中的数据。

**具体实现：**
先将A数组进行排序,从小到大进行排序，排序完成后，循环遍历B数组，用B数组中的每一项，去A数组中查找比这一项刚好大一点的数据：
- 查找到后，将其放入到对应位置。
- 如果查找不到，从排序完成的A数组中抽出最小的放到当前位置。

#### 代码实现：

```js
/**
 * @param {number[]} arr1
 * @param {number[]} arr2
 * @return {number[]}
 */
var advantageCount = function(arr1, arr2) {
    var arr = []; 
    arr1.sort(function(a, b) { 
        return a - b; 
    }); 
    arr2.forEach(function(item) { 
        var index = arr1.findIndex(function(_item) {
            return _item > item; 
        }); 
        if (index > -1) {
            arr.push(arr1.splice(index, 1)[0]); 
        } else {
            arr.push(arr2.splice(0, 1)[0]); } 
    }); 
    return arr;
};
```

