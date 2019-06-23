## 题意
获取每级域名的访问次数

## 思路

## hints
+ 使用 ".".join()
+ 链接的内容是 frags[i:]
+ collections.Counter()
+ collections.Counter().items(), 使用方法 for ct, dom in collections.Counter().items()

## 答案
```
def sub(cpb):
  ans = collection.Counter()
  
  for one in cpb:
    count, domain = one.split()
    count = int(count)
    frags = domain.split(".")
    for i in xrange(len(frags)):
        ans[".".join(frags[i:])] += count
    
  return ["{} {}".format(ct, dom) for ct, dom in ans.items()]
      
```
