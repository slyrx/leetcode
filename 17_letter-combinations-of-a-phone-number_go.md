# 题目描述

# 解题思路
回溯算法，将数字映射到对应的字母集合，通过回溯遍历所有可能的组合。

现在理解，回溯就是经过剪枝的递归，也可以不剪枝。

# 实现代码
```golang
var phoneMap = map[byte]string{
	'2': "abc",
	'3': "def",
	'4': "ghi",
	'5': "jkl",
	'6': "mno",
	'7': "pqrs",
	'8': "tuv",
	'9': "wxyz",
}

func letterCombinations(digits string) []string {
	if digits == "" {
		return nil
	}
	
	var combinations []string  // 存储结果的字符串切片
	backtrack("", 0, digits, &combinations)  // 调用回溯函数生成结果
	return combinations
}

func backtrack(combination string, index int, digits string, combinations *[]string) {
	if index == len(digits) {  // 如果已经遍历完所有数字，则将当前组合添加到结果中
		*combinations = append(*combinations, combination)
	} else {
		digit := digits[index]  // 获取当前数字
		letters := phoneMap[digit]  // 获取当前数字对应的字母集合
		for _, letter := range letters {  // 遍历字母集合
			backtrack(combination+string(letter), index+1, digits, combinations)  // 递归调用回溯函数生成下一个字符的组合
		}
	}
}

```

# 时间复杂度
O(3^N * 4^M)
# 空间复杂度
O(3^N * 4^M)
