## 题意
给出一个正整数数组，每一位元素表示当前索引的权重，写一个函数，让其按照索引代表的权重来摘取元素。

## 输入
一个字符串数组，多维数组表示的权重

## 输出
一维数组

## 答案代码
```
class Solution(object):

    def __init__(self, W):
        '''
        :type w: List[int]
        '''
        self.s = 0
        self.ps = []
        print W
        for w in W:
            self.s = self.s+ w
            self.ps.append(self.s)
        #print self.ps
        self.ps = map(lambda x:x/float(self.s), self.ps)
        
                
    def pickIndex(self):
        '''
        :rtype: int
        '''
        #print self.ps
        pick = random.random()
        
        insert =  bisect.bisect_right(self.ps,pick)
        return insert if insert < len(self.ps) else len(self.ps)-1

# Your Solution object will be instantiated and called as such:
# obj = Solution(w)
# param_1 = obj.pickIndex()

```
