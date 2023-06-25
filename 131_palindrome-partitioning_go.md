# 题目描述

# 解题思路
使用回溯算法，从字符串的起始位置开始，尝试不同的分割点，将字符串分割位为左右两个部分。如果左边的部分是回文串，将其加入到当前的分割方案中，然后递归处理右边的部分。

# 实现代码
```golang
func partition(s string) [][]string {
	var result [][]string   // Resultant slice to store all the partition combinations
	backtrack(s, 0, []string{}, &result)   // Call the backtrack function to find partitions
	return result
}

func backtrack(s string, start int, path []string, result *[][]string) {
	if start == len(s) {   // If we have reached the end of the string, add the current partition combination to the result
		temp := make([]string, len(path))
		copy(temp, path)
		*result = append(*result, temp)
		return
	}

	for i := start; i < len(s); i++ {   // Iterate through the string from the current start position
		if isPalindrome(s, start, i) {   // Check if the substring from start to i is a palindrome
			path = append(path, s[start:i+1])   // If it is a palindrome, add it to the current partition combination
			backtrack(s, i+1, path, result)   // Recursively backtrack for the remaining part of the string
			path = path[:len(path)-1]   // Remove the last added substring from the current partition combination
		}
	}
}

func isPalindrome(s string, left, right int) bool {
	for left < right {   // Check if the substring is a palindrome by comparing characters from left and right pointers
		if s[left] != s[right] {
			return false
		}
		left++
		right--
	}
	return true   // If the entire substring is a palindrome, return true
}

```

# 时间复杂度
O(n * 2^n)，其中 n 为字符串的长度。需要遍历所有可能的分割方案。
# 空间复杂度
O(n)，存储临时回文串的空间。

