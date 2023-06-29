# 题目描述

# 解题思路
后序遍历的最后一个元素是根节点，通过这个根节点，我们可以将序列分为左子树和右子树两部分。左子树中的所有元素小于根节点，右子树中的所有元素大于根节点。然后递归地判断左子树和右子树是否满足二叉搜索树的性质。

# 实现代码
```golang
func verifyPostorder(postorder []int) bool {
    if len(postorder) == 0 {
        return true
    }

    root := postorder[len(postorder) - 1] // 分节点

    i := 0
    for ; i<len(postorder)-1; i++ {
        if postorder[i] > root {
            break
        }
    } // 分割左子树

    j := i
    for ; j < len(postorder)-1; j++ {
        if postorder[j] < root {
            return false
        }
    } // 分割右子树，并对右子树的元素进行校验，如果小于根节点则提前判断退出

    left := true
    if i > 0 {
        left = verifyPostorder(postorder[:i])
    } // 递归左子树

    right := true
    if i < len(postorder)-1 {
        right = verifyPostorder(postorder[i:len(postorder)-1])
    } // 递归右子树

    return left && right
}

```

# 时间复杂度

# 空间复杂度
