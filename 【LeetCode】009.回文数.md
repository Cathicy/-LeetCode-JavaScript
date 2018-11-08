### 回文数
### 来源：[LeetCode009](https://leetcode-cn.com/problems/palindrome-number/description/)
### 问题描述：
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。
### 示例：
输入: 121  —> true

输入: -121 —> false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

输入: 10 —> false
解释: 从右向左读, 为 01 。因此它不是一个回文数。

### 代码实现：
方法一：
将整数`x`转化为字符串，依次比较第一位和最后一位、第二位和倒数第二位...是否相等，过程中只要一组不相等即返回`false`，只需要比较字符串长度的一半次数即可。
```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    var xRe = x.toString();
    for (var i = 0; i < xRe.length / 2; i++) {
        if (xRe[i] != xRe[xRe.length - 1 - i]) {
            return false;
        }
    }
    return true;
};
```
方法二：
直接将整数`x`反转，然后和原数字比较是否相等。
```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    let y = x;
    let xRe = 0;
    while (x > 0) {
        xRe = x % 10 + xRe * 10;
        x = Math.floor(x / 10);
    }
    return y == xRe;
};
```

