# 题目描述
LRU的全称是"Least Recently Used"，即"最近最少使用"。它是一种缓存淘汰策略，用于在缓存空间不足时决定哪些数据应该被优先移除。LRU策略的原理是根据数据的访问时间来判断数据的热度，最近被访问的数据具有更高的热度，因此最久未被访问的数据会被优先淘汰。

设计并实现一个最近最少使用（LRU）缓存机制。
该缓存应该支持以下操作：获取数据get(key)和写入数据put(key, value)。

get 的功能是要做什么？如果关键字存在于缓存中，则返回关键字的值，否则返回 -1

# 解题思路
双向节点的作用：把最常用的节点放在尾部，最不常用的节点放在头部；这样可以方便删除最不常用的节点。
key 和 value 的关系：其实两者没有必然联系，可以不一样，只是这里设置为一样
双向节点和 map 的关系：两者没有关系，又或者，因为链表查找某个节点太困难了，所以 map 相当于它的登记表，直接记录了每个节点的位置，双向链表则是
删除头节点和删除节点功能的区别是？删除节点可以指定删除哪一个，删除头节点是在容量超量的时候被动删除的。

```golang

节点1:        节点2:
+------+    +------+
| prev |<---| next |
+------+    +------+
|  val |    |  val |
+------+    +------+
| next |--->| prev |
+------+    +------+

```


# 实现代码
```golang
type Node struct {
  key    int
  value  int
  prev   *Node
  next   *Node
}

type LRUCache struct {
  capacity   int
  size       int
  cache      map[int]*Node
  head       *Node
  tail       *Node
}

func Constructor(capacity int) LRUCache {
  cache := LRUCache{
     capacity: capacity,
     size: 0,
     cache: make(map[int]*Node, 0),
     head: &Node{},
     tail: &Node{},
  }
  cache.head.next = cache.tail
  cache.tail.prev = cache.head
  
  return cache
}

func (this *LRUCache) Get(key int) int {
  if node, ok := this.cache[key]; ok {
      this.moveToTail(node)
      return node.value
  }
  return -1
}

func (this *LRUCache) Put(key, val int) {
  if node, ok := this.cache[key]; ok {
      node.value = val
      this.moveToTail(node)
  } else {
      newNode := &Node{key:key, value:val}
      this.cache[key] = newNode
      this.addToTail(newNode)
      this.size++
      if this.size > this.capacity {
         removeNode := this.removeFromHead()
         delete(this.cache, removeNode.key)
         this.size--
      }
  }
}

func (this *LRUCache) moveToTail(node *Node) {
    this.removeFromList(node)
    this.addToTail(node)
}

func (this *LRUCache) removeFromList(node *Node) {
    node.prev.next = node.next
    node.next.prev = node.prev
    
}

func (this *LRUCache) addToTail(node *Node) {
    this.tail.prev.next = node
    node.prev = this.tail.prev
    node.next = this.tail
    this.tail.prev = node
}

func (this *LRUCache) removeFromHead() *Node {
    node := this.head.next
    this.removeFromList(node)
    return node
}

```

```golang
type LRUCache struct {
    capacity  int
    cache     map[int]*list.Element
    lruList   *list.List
}

type cacheItem struct {
    key    int
    value  int
}

func Constructor(capacity int) LRUCache {
    return LRUCache{
        capacity: capacity,
        cache: make(map[int]*list.Element),
        lruList: list.New(),
    }
}


func (this *LRUCache) Get(key int) int {
    if elem, ok := this.cache[key]; ok {
        this.lruList.MoveToFront(elem)
        return elem.Value.(*cacheItem).value
    }
    return -1
}


func (this *LRUCache) Put(key int, value int)  {
    if elem, ok := this.cache[key]; ok {
        elem.Value.(*cacheItem).value = value
        this.lruList.MoveToFront(elem)
    } else {
        if this.lruList.Len() == this.capacity {
            lastElem := this.lruList.Back()
            delete(this.cache, lastElem.Value.(*cacheItem).key)
            this.lruList.Remove(lastElem)
        }
        newItem := &cacheItem{key:key, value:value}
        newElem := this.lruList.PushFront(newItem)
        this.cache[key] = newElem
    }
}


/**
 * Your LRUCache object will be instantiated and called as such:
 * obj := Constructor(capacity);
 * param_1 := obj.Get(key);
 * obj.Put(key,value);
 */

```

# 时间复杂度
get 和 put 的操作，时间复杂度都是 O(1)

# 空间复杂度
为 O(capacity), capacity 是 LRU 的容量







