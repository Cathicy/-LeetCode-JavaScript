#### 两个排列数组的中位数
#### 来源：[LeetCode No.007](https://leetcode-cn.com/problems/reverse-integer/description/)
#### 问题描述：
给定一个 32 位有符号整数，将整数中的数字进行反转。
要求：
环境只能存储 32 位有符号整数，其数值范围是 [−231,  231 − 1]。如果反转后的整数溢出，则返回 0。
#### 示例：
示例1:
输入: 123
输出: 321

示例2：
输入: -123
输出: -321

示例3：
输入: 120
输出: 21

#### 代码实现：
```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    let result = parseInt(x.toString().split('').reverse().join(''));
    if(result > Math.pow(2,31) - 1 || -result < Math.pow(-2, 31) - 1){
        return 0;
    }
    return x > 0 ? result : -result;                  
};
```

