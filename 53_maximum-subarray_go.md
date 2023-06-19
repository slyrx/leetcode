# 题目描述

# 解题思路
这个问题使用动态规划解决。
需要维护两个变量， currentSum 表示当前子数组的和，也就是需要动态规划转移方程处理的内容。maxSum 表示当前最大子数组的和。
对于每个元素，更新 currentSum，更新的过程就是当前元素的和依赖于前面元素的结果。并将更新的结果与 maxSum 进行比较，如果 currentSum 大于 maxSum, 则更新 maxSum。
当 currentSum 变为负数，需要将其重置为 0 ，因为负数加上后续的元素只会使子数组和更小。

根据题目描述，子数组最少包含一个元素，因此我们可以将 maxSum 和 currentSum 的初始值都设为数组的第一个元素。这样做的好处是，在处理数组的第一个元素时，我们可以直接将其作为初始的最大子数组和和当前子数组和，而无需特殊处理。

currentSum = max(nums[i], currentSum+nums[i]) ， currentSum 为负数，则后面的 nums[i] 为正则会把负数过滤比下去，为负则会继续累积，知道遇到一个正数，把结果比出来，如果全是负数，则也会计算出相对较大的负数。

# 实现代码
```golang

func maxSubArray(nums []int) int {
	maxSum := nums[0]   // 当前最大子数组的和
	currentSum := nums[0]  // 当前子数组的和

	for i := 1; i < len(nums); i++ {
		// 更新当前子数组的和
		currentSum = max(nums[i], currentSum+nums[i])
		// 更新当前最大子数组的和
		maxSum = max(maxSum, currentSum)
	}

	return maxSum
}

// 辅助函数，返回两个整数中的最大值
func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

```

# 时间复杂度
O(n)
# 空间复杂度
O(1)
