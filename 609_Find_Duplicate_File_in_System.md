## 答案代码
```
    def findDuplicate(self, paths):
        """
        :type paths: List[str]
        :rtype: List[List[str]]
        """
        #input: 只有内容相同才算是相同文件，文件一不一样不去管他
        dd = collections.defaultdict(list)
        
        for i in paths:
            s = i.split(" ")
            path = s[0]
            for j in range(1, len(s)):
                b = s[j].index("(")
                e = s[j].index(")")
                dd[tuple(s[j][b+1:e])].append(path+"/"+s[j][:b])
        result = []   
        for k in dd.values():
            if len(k) > 1:
                result.append(k)
        return result
```
