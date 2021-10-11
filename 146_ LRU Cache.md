
# 思路

# 关键

# 涉及情况

# 答案

```
#key:使用到的元素在使用前都要先删除一下；改写的popitem函数让dict具有了栈和队列的性质。
class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.d = collections.OrderedDict()
        self.c = capacity
        

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        ret = -1
        if key in self.d:
            ret, self.d[key] = self.d[key], self.d.pop(key)
        return ret
        

    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """
        if key in self.d:
            del self.d[key]
        self.d[key] = value
        if len(self.d) > self.c:
            self.d.popitem(last=False)
        


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```
