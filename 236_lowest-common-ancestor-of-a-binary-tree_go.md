# 题目描述

# 解题思路

把每个节点遍历一遍，尝试寻找的节点可以不可以变成它两边的子节点。

# 实现代码
```golang
func lowestCommonAncestor(root, p, q *TreeNode) *TreeNode {
    
	// Base case: 如果当前节点为空或等于 p 或 q，直接返回当前节点
	if root == nil || root == p || root == q {
		return root
	}

	// 递归遍历左子树
	left := lowestCommonAncestor(root.Left, p, q)
	// 递归遍历右子树
	right := lowestCommonAncestor(root.Right, p, q)

	// 根据左右子树的返回值进行判断
	if left != nil && right != nil {
		// 如果左右子树都不为空，说明 p 和 q 分别在左右子树中，返回当前节点
		return root
	} else if left != nil {
		// 如果左子树不为空，说明 p 和 q 都在左子树中，返回左子树的返回值
		return left
	} else if right != nil {
		// 如果右子树不为空，说明 p 和 q 都在右子树中，返回右子树的返回值
		return right
	}

	// 如果左右子树都为空，返回空值
	return nil
}
```

# 时间复杂度

# 空间复杂度
