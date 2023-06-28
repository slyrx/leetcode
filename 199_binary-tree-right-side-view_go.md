# 题目描述

# 解题思路
需要对右左子树都进行递归，但是右要放到左的前面。
左子树只在右子树无效的情况下才产生作用。

level 的设定为了映射树的高度，从 0 开始。
level 和数组的长度相等，表示当前层没有处理完成，需要添加元素。
level 的作用是为了规避，右子树不为空的情况下，左子树还想加入的情况。

所以递归的话，顺序还是很重要的。

# 实现代码

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func rightSideView(root *TreeNode) []int {
	result := []int{}
	dfs(root, 0, &result)
	return result
}

func dfs(node *TreeNode, level int, result *[]int) {
	if node == nil {
		return
	}

	// 每层只保留最右边的节点值
	if level == len(*result) {
        fmt.Println(level, len(*result), node.Val)
		*result = append(*result, node.Val)
	}

	// 先遍历右子树，再遍历左子树，保证每层最右边的节点被先访问到
	dfs(node.Right, level+1, result)
	dfs(node.Left, level+1, result)
}

```

# 时间复杂度
O(N)，其中 N 是二叉树中的节点数。需要遍历所有节点。
# 空间复杂度
O(H)，其中 H 是二叉树的高度。
