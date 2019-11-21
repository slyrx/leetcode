## 题意
给出一个开始词，一个结尾词，另给一个词典，求出能从开始词变成结尾词的最短路径。

## 要求
1. 一次只能变化一个词
2. 每次变化的词必须都存在于词典中

## 输入
两个字符串，一个字符串数组

## 输出
整型


## 答案
```
class Solution(object):
    def ladderLength(self, beginWord, endWord, wordList):
        """
        :type beginWord: str
        :type endWord: str
        :type wordList: List[str]
        :rtype: int
        """
        #fail place: 在字典里设定映射矩阵的时候，不能写成tuple,而是键值对应的形式
        if endWord not in wordList or not beginWord or not endWord or not wordList:
            return 0
        
        L = len(beginWord)
        print 1
        com_dict = collections.defaultdict(list)
        for word in wordList:
            for i in range(L):
                medium_pattern = word[:i] + "*" + word[i+1:]
                com_dict[medium_pattern].append(word)
                
        que = [(beginWord, 1)]
        visited = {beginWord:True}
        while que:
            cur_word, level = que.pop(0)
            
            for i in range(L):
                mid_p = cur_word[:i] + "*" + cur_word[i+1:]
            
                for w in com_dict[mid_p]:
                    if w == endWord:
                        return level + 1
                    
                    if w not in visited:
                        visited[w] = True
                        que.append((w, level + 1))
                com_dict[mid_p] = []
                
        return 0
```
