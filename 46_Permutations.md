

## 答案代码
```
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        #key：全排列问题是典型的递归做问题；数组里是数字，但想实现两个拼接，使用[1]+[2]=[1,2]
        
        result = []
        self.dfs(nums, [], result)
        return result
    def dfs(self, nums, clist, result):
        if len(clist) == len(nums):
            result.append(clist)
            return
        
        for i in nums:
            if i in clist:
                continue
            else:
                self.dfs(nums, clist+[i], result)
```
