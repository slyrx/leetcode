# 题目描述

# 解题思路

对回溯的开始和单个完整的循环，概念不明确。
回溯的 3 个关键点：过滤结果，分割节点，回退。

突出特征，强化记忆。

关键的点：
1、判断在哪儿
2、循环
3、顺序，按照流程做的事情

# 实现代码
```golang
func restoreIpAddresses(s string) []string {
	var res []string // 存储结果的切片
	backtrack(s, []string{}, &res) // 调用回溯函数生成结果
	return res
}

func backtrack(s string, segments []string, res *[]string) {
	// 如果已经找到了 4 个段且字符串刚好被切分完，则将结果添加到结果切片中
	if len(segments) == 4 && len(s) == 0 {
		ipAddress := strings.Join(segments, ".")
		*res = append(*res, ipAddress)
		return
	}

	// 如果已经找到了 4 个段但字符串还未被切分完，说明当前切分不符合要求，直接返回
	if len(segments) == 4 && len(s) > 0 {
		return
	}

	// 尝试不同的切分长度
	for i := 1; i <= 3 && i <= len(s); i++ {
		segment := s[:i] // 取出当前切分段
		// 判断当前切分段是否符合要求
		if isValid(segment) {
			segments = append(segments, segment) // 将当前切分段加入段列表
			backtrack(s[i:], segments, res)       // 递归处理剩余字符串
			segments = segments[:len(segments)-1] // 回溯，撤销选择
		}
	}
}

func isValid(segment string) bool {
	// 判断切分段是否合法，满足以下条件：长度为 1 或者首字符不为 0 且转换为整数后不超过 255
	if len(segment) > 1 && segment[0] == '0' {
		return false
	}
	num, _ := strconv.Atoi(segment)
	return num >= 0 && num <= 255
}

```

# 时间复杂度
O(3^4) = O(1)
# 空间复杂度
O(1)
