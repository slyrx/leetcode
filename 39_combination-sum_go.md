# 题目描述

# 解题思路
使用回溯算法，并通过约束条件进行剪枝。

在回退前和后打 log ，可以看出差别。

# 实现代码
```golang
func combinationSum(candidates []int, target int) [][]int {
	var res [][]int // 存储结果的二维切片
	backtrack(candidates, target, 0, []int{}, &res) // 调用回溯函数生成结果
	return res
}

func backtrack(candidates []int, target, start int, curComb []int, res *[][]int) {
	if target == 0 { // 当目标数等于0时，将当前组合加入结果集
		*res = append(*res, append([]int{}, curComb...))
		return
	}

	for i := start; i < len(candidates); i++ { // 把 i 再次传入了回溯函数，就说明了可以重复使用备选元素
		if target-candidates[i] >= 0 { // 当目标数减去当前元素仍大于等于0时，可以继续加入当前元素
			curComb = append(curComb, candidates[i]) // 将当前元素加入当前组合
			backtrack(candidates, target-candidates[i], i, curComb, res) // 递归调用回溯函数
			curComb = curComb[:len(curComb)-1] // 回溯，移除最后一个加入的元素
		}
	}
}

```

# 时间复杂度
O(N^target)
# 空间复杂度
O(target)
