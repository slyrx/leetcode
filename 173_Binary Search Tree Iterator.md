
## 思路
实现一个类，该类可以具有：
+ 检查是否有下一个 BST 节点的功能
+ 返回下一个节点的值

二叉搜索树是一个利用**基础存储结构**和**调用逻辑**最终形成的一种像树一样的**轨迹**。
+ 基础存储结构使用了**数组**
+ 调用逻辑使用了
+ + 栈
+ + BST 的存入和取出逻辑


## 关键
+ 实现构造 BST 需要的轨迹
+ + 存入 BST 的顺序
+ + 取出 BST 的顺序

## 问题
BST 涉及到的四方面问题
1. 熟悉 BST 的节点结构
2. 共有**4**个函数
3. 存储**树**节点使用的结构是**栈**
4. 调用逻辑
+ 存入逻辑
+ + 首次存入
+ + 中间存入
+ 取出逻辑
+ + 中间取出

## 答案
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
