# 题目描述

# 解题思路
需要对右左子树都进行递归，但是右要放到左的前面。
左子树只在右子树无效的情况下才产生作用。

level 的设定为了映射树的高度，从 0 开始。
level 和数组的长度相等，表示当前层没有处理完成，需要添加元素。
level 的作用是为了规避，右子树不为空的情况下，左子树还想加入的情况。

所以递归的话，顺序还是很重要的。

通过递归遍历二叉树的节点。在每个节点的访问过程中，通过判断当前层数与结果列表的长度，将每层最右边的节点值加入结果列表。为了保证最右边的节点先被访问，需要先遍历右子树，再遍历左子树。

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


```golang
type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
}

func rightSideView(root *TreeNode) []int {
	if root == nil {
		return []int{}
	}

	result := []int{}
	queue := []*TreeNode{root}

	for len(queue) > 0 {
		size := len(queue)

		 // 遍历当前层的节点
		for i := 0; i < size; i++ {
			node := queue[i]
			if i == size-1 {
				// 如果是当前层的最右边节点，将其值加入结果列表
				result = append(result, node.Val)
			}

			// 将下一层的节点加入队列
			if node.Left != nil {
				queue = append(queue, node.Left)
			}
			if node.Right != nil {
				queue = append(queue, node.Right)
			}
		}

		// 移除当前层的节点
		queue = queue[size:]
	}

	return result
}


```

# 时间复杂度
O(N)，其中 N 是二叉树中的节点数。需要遍历所有节点。
# 空间复杂度
O(H)，其中 H 是二叉树的高度。
