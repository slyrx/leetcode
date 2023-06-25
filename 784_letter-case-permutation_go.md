# 题意描述

# 解题思路

# 实现代码
```golang
func letterCasePermutation(S string) []string {
	var result []string             // 存储结果的切片
	backtrack("", 0, S, &result)    // 调用回溯函数，找到所有排列组合
	return result
}

func backtrack(current string, index int, S string, result *[]string) {
	if index == len(S) {                          // 判断是否达到字符串 S 的长度
		*result = append(*result, current)        // 将当前生成的字符串添加到结果中
		return
	}

	ch := S[index]                                // 获取当前位置的字符
	if isLetter(ch) {                             // 判断是否为字母
		backtrack(current+string(ch), index+1, S, result)   // 第一次递归调用，将当前字符保持原大小写，继续下一层递归
		if isLower(ch) {
			backtrack(current+string(upper(ch)), index+1, S, result)   // 第二次递归调用，将当前字符转换为相反的大小写，继续下一层递归
		} else {
			backtrack(current+string(lower(ch)), index+1, S, result)
		}
	} else {
		backtrack(current+string(ch), index+1, S, result)   // 如果不是字母，直接将当前字符添加到当前生成的字符串中，继续下一层递归
	}
}

func isLetter(ch byte) bool {
	return ('a' <= ch && ch <= 'z') || ('A' <= ch && ch <= 'Z')   // 判断字符是否为字母
}

func isLower(ch byte) bool {
	return 'a' <= ch && ch <= 'z'         // 判断字符是否为小写字母
}

func lower(ch byte) byte {
	return ch + ('a' - 'A')               // 将字符转换为小写字母
}

func upper(ch byte) byte {
	return ch - ('a' - 'A')               // 将字符转换为大写字母
}


```

# 时间复杂度
O(2^N)，其中 N 是字符串 S 的长度。对于每个字符，都有两种情况，即转换为大写或小写。
# 空间复杂度
O(N)，存储中间结果的空间。

