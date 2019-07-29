## 目标
把数组中所有0向后移动

## 思路
+ 空布袋思想：
1. 独有指针 i
2. 互换的思想

## 问题
出现一次问题，是因为把=写成了==

## 答案
```
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        x = 0
        for i in xrange(len(nums)):
            if nums[i] != 0:
                nums[x], nums[i] = nums[i], nums[x]
                x += 1
```
