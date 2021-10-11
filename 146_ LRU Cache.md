
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


```
class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.lrudict = {}
        self.lrulist = []

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        if key in self.lrudict:
            self.lrulist.remove(key)
            self.lrulist.insert(0,key)
            return self.lrudict[key]
        else:
            return -1

    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """   
        if key in self.lrudict:
            self.lrudict[key] = value
            self.lrulist.remove(key)
            self.lrulist.insert(0,key)
        elif len(self.lrudict) == self.capacity:
            rmKey = self.lrulist.pop(-1)
            del self.lrudict[rmKey]
            self.lrudict[key] = value
            self.lrulist.insert(0,key)
        else:
            self.lrudict[key] = value
            self.lrulist.insert(0,key)
        
        


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```

```
class Node:
    def __init__(self, k, v):
        self.key = k
        self.val = v
        self.prev = None
        self.next = None
        
class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.dic = {}
        self.head = Node(0, 0)
        self.tail = Node(0, 0)
        self.head.next = self.tail
        self.tail.prev = self.head
        

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        if key in self.dic:
            n = self.dic[key]
            self._remove(n)
            self._add(n)
            return n.val
        return -1
        

    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """
        if key in self.dic:
            self._remove(self.dic[key])
        n = Node(key, value)
        self._add(n)
        self.dic[key] = n
        if len(self.dic) > self.capacity:
            n = self.head.next
            self._remove(n)
            del self.dic[n.key]
    
    def _remove(self, node):
        p = node.prev
        n = node.next
        p.next = n
        n.prev = p
    
    def _add(self, node):
        p = self.tail.prev
        p.next = node
        self.tail.prev = node
        node.prev = p
        node.next = self.tail
        


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```

```
class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.map = {}
        self.recent = deque()
        

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        if key in self.map:
            self.recent.remove(key)
            self.recent.append(key)
            return self.map[key]
        return -1
        

    def put(self, key, value):
        if key in self.map:
            self.recent.remove(key)
            self.recent.append(key)
            self.map[key] = value
        else:
            if len(self.map) >= self.capacity:
                leastUsed = self.recent.popleft()
                del self.map[leastUsed]
                self.map[key] = value
                self.recent.append(key)
            else:
                self.map[key] = value
                self.recent.append(key)
```
