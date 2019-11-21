## 题意
实现二叉搜索树的迭代器

## 输入
半待完成的类

## 输出
完整的类代码

## 答案代码
```

# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class BSTIterator(object):

    def __init__(self, root):
        """
        :type root: TreeNode
        """
        self.stack = []
        self.pushAll(root)

    def next(self):
        """
        @return the next smallest number
        :rtype: int
        """
        temp = self.stack.pop()
        self.pushAll(temp.right)
        return temp.val
        

    def hasNext(self):
        """
        @return whether we have a next smallest number
        :rtype: bool
        """
        
        return self.stack
        
    def pushAll(self, node):
        while node is not None:
            self.stack.append(node)
            node = node.left
        


# Your BSTIterator object will be instantiated and called as such:
# obj = BSTIterator(root)
# param_1 = obj.next()
# param_2 = obj.hasNext()
```
