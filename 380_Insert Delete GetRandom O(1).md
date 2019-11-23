## 题意
设计一个数据结构，使得要求的操作时间复杂度都在 O(1)。

## 规则
1. 插入
2. 删除
3. 获取随机，元素出现的概率相同


## 输入
未完成的类

## 输出
完整的类代码

## 答案代码
```
#fail place:获取set的某个元素的方法；逻辑对了，但是超时了
class RandomizedSet(object):

    def __init__(self):
        '''
        Initialize your data structure here.
        '''
        self.x = set()
        

    def insert(self, val):
        '''
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        :type val: int
        :rtype: bool
        '''
        if val not in self.x:
            self.x.add(val)
            return True
            
        return False

    def remove(self, val):
        '''
        Removes a value from the set. Returns true if the set contained the specified element.
        :type val: int
        :rtype: bool
        '''
        if val not in self.x:
            return False
        else:
            self.x.remove(val)
            return True

    def getRandom(self):
        '''
        Get a random element from the set.
        :rtype: int
        '''
        return random.sample(self.x, 1).pop()
        
        
        


# Your RandomizedSet object will be instantiated and called as such:
# obj = RandomizedSet()
# param_1 = obj.insert(val)
# param_2 = obj.remove(val)
# param_3 = obj.getRandom()
```
