## 题意
给出一组整型数组和一个目标值，求出能组成该目标值的组合数，包括重复元素在内

## 输入
整型数组和目标值

## 输出
组合数

## 答案代码
```
class Solution(object):
    def threeSumMulti(self, A, target):
        '''
        :type A: List[int]
        :type target: int
        :rtype: int
        '''
        counts = collections.Counter(A)
        
        nums = sorted(counts)
        res = 0
        for i in range(len(nums)):
            for j in range(i, len(nums)):
                t = target - nums[i] - nums[j]
                if t == nums[i] == nums[j]:
                    res += counts[t] * (counts[t]-1) * (counts[t] - 2)/6
                elif t != nums[i] == nums[j]:
                    res += counts[nums[i]] * (counts[nums[i]] - 1) * counts[t]/2
                elif t > nums[i] and t > nums[j]:
                    res += counts[t] * counts[nums[i]] * counts[nums[j]]
                
        return res%(10**9 + 7)
```
