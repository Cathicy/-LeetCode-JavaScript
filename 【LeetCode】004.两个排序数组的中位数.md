#### 两个排列数组的中位数
#### 来源：[LeetCode No.004](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/description/)
#### 问题描述：
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2 。
请找出这两个有序数组的中位数。要求算法的时间复杂度为 O(log (m+n)) 。
你可以假设 nums1 和 nums2 不同时为空。
#### 示例：
nums1 = [1, 3]； nums2 = [2]； 中位数是 2.0
nums1 = [1, 2]； nums2 = [3, 4]； 中位数是 (2 + 3)/2 = 2.5
#### 思路分析：
中位数：把一个数组分成两部分，左边最大的数应该小于右边最小的数。数组1和数组2的长度分别为m，n，一般的长度为`（m+n）/2`，即`m/2+n/2`，所以可以直接把数组1的前半部分和数组2的前半部分合并，数组1和数组2的后半部分合并，然后前半部分的最大值小于等于后半部分的最小值，即可求出中位数，关系式如下：

```js
j + i = (m + n) / 2 && max(nums1[j - 1) nums2[i - 1]) <= min(nums[j] nums[i])
```
- 如果`nums1[j-1] > nums2[i]`，这时候我们可以理解为，数组1的左边有数据过大，所以我们必须把这个大数给 右边，但是这样就会产生左边的总数少了，那我们就把数组2右边的给左边一个就行了。所以左边合起来的总是依旧等于右边合起来的总数
- 同理，如果`nums2[i-1] > nums1[j]`，就把 `nums2[i-1]`送给右边同时把`nums1[j]`送给左边就行。

#### 代码实现：

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    var result = [];
    while (nums1.length > 0 && nums2.length > 0) {
        if (nums1[0] < nums2[0]) {
            result.push(nums1.shift());
        } else {
            result.push(nums2.shift());
        }
    }
    var res = result.concat(nums1, nums2);
    var middle = Math.floor(res.length / 2);
    if (res.length % 2) {
        return res[middle];
    } else {
        return (res[middle - 1] + res[middle]) / 2;
    }
};
```

