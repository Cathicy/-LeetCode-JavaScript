#### 两数之和
#### 来源：[LeetCode No.001](https://leetcode-cn.com/problems/two-sum/description/)
#### 问题描述：
给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
#### 示例：
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
#### 代码实现：
##### 方法一：
时间复杂度： O(n^2^)
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
function getSum(arr, target) {
	for (var i = 0; i < arr.length; i++) {
		for (var j = 0; j < arr.length; j++) {
			if (arr[i] + arr[j] === target) {
				return [i, j];
			}
		}
	}
}
```
##### 方法二：
时间复杂度：O（n）
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
function getSum(arr, target) {
	var map = {};
	for (var i = 0; i < arr.length; i++) {
		if (map[target-arr[i]] !== undefined) {
			return [map[target-arr[i]],i];
		} else {
			map[arr[i]] = i;
		}
	}
}
```
