## 并查集的主要作用
检查图中的点有没有环

## 主要步骤
1. 把当前的内容映射到数组
+ 内容映射数组
+ 记录树的深度数组
2. 定义必要的两个函数
+ 找父节点
+ 合并节点
3. 在主函数中调用两个检查函数


## 涉及4个函数
+ 初始化内容和 rank 数组
+ find_parent
+ union
+ 主函数调用


## 代码
```
def initalise():
   parent = []
   rank = []
   for i in range(6):
     parent[i] = -1
     rank[i] = 0
     
   return parent, rank
```
```
def find_root(x, parent):
   x_root = x
   while parent[x_root] != -1:
      x_root = parent[x_root]
   
   return x_root
```
```
def unio(x, y, parent, rank):
   x_root = find_root(x, parent)
   y_root = find_root(y, parent)
   
   if x_root == y_root:
      return 0
   else:
      if rank[x_root] > rank[y_root]:
         parent[y_root] = x_root
      elif rank[x_root] < rank[y_root]:
         parent[x_root] = y_root
      else:
         parent[x_root] = y_root
         rank[y_root] += 1
      return 1
```
