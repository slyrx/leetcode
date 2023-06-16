
# 题目描述

# 解题思路
使用中心扩展法，从字符串的每一个字符开始，分别向左右两边扩展，判断扩展后的子串是否是回文串，并记录最长的会问子串。

这个思路里涉及到了 3 个元素，以 i 为中心，以 i 和 i+1 为中心，以及 start 和 end 记录到当前位置。
end 和 start 是回文子串的索引位置，因此它们之间的距离需要加上 1 才能表示回文子串的实际长度。

疑难点：
为什么 start 的计算是 length - 1， 而 end 的计算是 length ?


```golang

  c <---b---> b d
        length 排除的就是自己

```

right - left - 1，在数组中，要把左边的开始节点囊括进来就是要用 -1，要把右边的结束节点囊括进来就是要用 +1 。


# 实现代码

```python

import "math"

func longestPalindrome(s string) string {
	if len(s) < 2 {
		return s
	}

	start, end := 0, 0 // 初始化最长回文子串的起始和结束位置
	for i := 0; i < len(s); i++ {
		len1 := expandAroundCenter(s, i, i) // 以当前字符为中心，向两边扩展的回文串长度（奇数长度）
		len2 := expandAroundCenter(s, i, i+1) // 以当前字符和下一个字符的间隙为中心，向两边扩展的回文串长度（偶数长度）
		length := int(math.Max(float64(len1), float64(len2))) // 使用 math.Max 函数比较两个整数 // 取奇数长度和偶数长度中的最大值作为当前位置的回文串长度
		if length > end-start+1 {
			start = i - (length-1)/2 // 更新最长回文子串的起始位置
			end = i + length/2       // 更新最长回文子串的结束位置
		}
	}

	return s[start : end+1] // 根据最长回文子串的起始和结束位置截取原字符串，得到最长回文子串
}

// 扩展中心，判断回文串的长度
func expandAroundCenter(s string, left, right int) int {
	for left >= 0 && right < len(s) && s[left] == s[right] {
		left--        // 向左扩展
		right++       // 向右扩展
	}
	return right - left - 1 // 返回回文串的长度
}

```

# 时间复杂度
O(n^2)
# 空间复杂度
O(1)




