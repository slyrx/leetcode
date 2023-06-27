# 题目描述

# 解题思路
首先判断根节点值是否相同，如果相同则调用 isSubStructureHelper() 判断 B 是否是以 A 的当前节点为根节点的子结构。isSubStructureHelper() 是一个递归函数，它分别判断 A 和 B 的左子树和右子树是否满足子结构的条件。

允许 B 只有一个节点，且是 A 中靠上的节点。B 可以是 A 中任意位置的子结构
在相同节点判断成功后，就可以继续判断树下子节点的值。
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
func isSubStructure(A *TreeNode, B *TreeNode) bool {
    if B == nil {
        return false
    }

    return dfs(A, B) || dfs(A.Left, B) || dfs(A.Right, B)

}

func dfs(A *TreeNode, B *TreeNode) bool {
    if B == nil {
        fmt.Println(A , B)
        return true
    }

    if A != nil && A.Val != B.Val {
        return false
    }

    return dfs(A.Left, B.Left) && dfs(A.Right, B.Right)
}

```

# 时间复杂度
O(m * n)，其中 m 是 A 的节点数，n 是 B 的节点数。
# 空间复杂度
O(m)，其中 m 是 A 的节点数。

