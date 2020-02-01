## 答案代码
```
    def isValidBST(self, root):
        
        :type root: TreeNode
        :rtype: bool
        
        
        
        def isBST(root, min_val, max_val):
            if not root:
                return True
            
            if root.val <= min_val:
                return False
            if root.val >= max_val:
                return False
            
            return isBST(root.left, min_val, root.val) and isBST(root.right, root.val, max_val)
        
        return isBST(root, float('-inf'), float('inf'))
```
