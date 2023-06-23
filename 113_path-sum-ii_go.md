# 题目描述

# 解题思路

# 实现代码
```golang

func pathSum(root *TreeNode, targetSum int) [][]int {
	var result [][]int       // 存储结果的二维数组
	var path []int           // 存储当前路径的数组
	backtrack(root, targetSum, []int{}, &result)
	return result
}

func backtrack(node *TreeNode, targetSum int, path []int, result *[][]int) {
	if node == nil {
		return
	}

	path = append(path, node.Val) // 将当前节点的值加入路径中
	targetSum -= node.Val         // 更新目标值

	// 如果是叶子节点且路径和等于目标值，将路径加入结果集
	if node.Left == nil && node.Right == nil && targetSum == 0 {
		temp := make([]int, len(path))
		copy(temp, path)
		*result = append(*result, temp)
		return
	}

	// 递归调用左子树和右子树
	backtrack(node.Left, targetSum, path, result)
	backtrack(node.Right, targetSum, path, result)

	// 在返回上一层之前，将路径数组的最后一个节点移除
	path = path[:len(path)-1]
}


```

# 时间复杂度

# 空间复杂度
