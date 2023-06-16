# 题目描述

# 解题思路
使用滑动窗口来解决，
定义一个左指针 left 和一个右指针 right， 分别表示当前考察的子串的左右边界。
初始时，两个指针都指向字符串的起始位置。然后，通过移动右指针来扩展当前的子串，直到出现重复字符为止。如果出现重复字符，就移动左指针，缩小窗口的大小，直到不再右重复字符为止。
不断重复这个过程，直到右指针达到字符串的末尾。
在扩展子串的过程中，通过更新结果变量来记录最长的不含重复字符的子串的长度。


right 是一直向右走的，遇到重复的字符更新的也是左面的指针，遇到了不重复的字符，默认操作就是更新 map 和指针继续右移

# 实现代码

```golang

func lengthOfLongestSubstring(s string) int {
	maxLength := 0                // 最长子串的长度
	left, right := 0, 0           // 滑动窗口的左右指针
	visited := make(map[byte]int) // 记录字符的出现位置

	for right < len(s) {
		char := s[right] // 当前字符
		// 如果当前字符已经在窗口中出现过且出现位置在窗口内，则移动左指针
		if index, ok := visited[char]; ok && index >= left {
			left = index + 1
		}
		visited[char] = right       // 更新当前字符的出现位置
		length := right - left + 1 // 当前子串的长度
		if length > maxLength {    // 更新最长子串的长度
			maxLength = length
		}
		right++ // 移动右指针，扩展窗口
	}

	return maxLength
}

```

# 时间复杂度

# 空间复杂度
