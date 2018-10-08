#### 无重复字符的最长子串
#### 来源： [LeetCode No.003](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/description/)
#### 问题描述：
给定一个字符串，找出不含有重复字符的最长子串的长度。
#### 示例：
输入: `"abcabcbb"`  无重复字符的最长子串是 `"abc"`，其长度为 3。
输入: `"bbbbb"`  无重复字符的最长子串是 `"b"`，其长度为 1。
输入:` "pwwkew"` 无重复字符的最长子串是 `"wke"`，其长度为 3。
(请注意，答案必须是一个子串，"pwke" 是一个子序列 而不是子串。)
#### 思路分析：
准备一个空字符串`str`用于存放 ，遍历字符串得到的字符`char`，若`str`里存在`char`则记录`str`的大小`res`。
然后截取`str`去除重复字符前的字符(包括该重复字符 )，继续遍历最后得到最大的子串长度 。
#### 代码实现：
```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    var res = 0;
    var str = "";
    for (var i = 0; i < s.length; i++) {
        var char = s.charAt(i);
        var index = str.indexOf(char);
        if (index === -1) {
            str += char;
            res = res < str.length ? str.length : res;
        } else {
            str = str.substr(index + 1) + char;
        }
    }
    return res;
};
```

