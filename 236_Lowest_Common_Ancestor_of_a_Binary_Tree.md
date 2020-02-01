## 题意
在一个二叉树中，找到给出的两个节点的共同最小父节点

## 输入
父节点，和任意两个节点

## 输出
结果节点

## 答案代码
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def __init__(self):
        self.ans = None
    def lowestCommonAncestor(self, root, p, q):
        """
        :type root: TreeNode
        :type p: TreeNode
        :type q: TreeNode
        :rtype: TreeNode
        """
        def dfs(root, p, q):
            if root == None:
                return False
            
            left = dfs(root.left, p, q)
            right = dfs(root.right, p, q)
            
            mid = root == q or root == p
            
            if left + right + mid >= 2:
                self.ans = root
            
            return mid or left or right

        dfs(root, p, q)
        
```
