## 思路
一个整数相当于一个半排序的序列，找它的下一个较大值，等价于一下三步：
+ 找第一相邻的顺序数字关系，记录位置
+ 用最小值进行互换
+ 对记录位置之后的数字重新排序

## 关键
这里涉及到2方面的内容，第一是位置，第二是数字的大小。按照本次变换的理解，位置越靠后，优先级越高；其次数字越小，优先级越高。

## 涉及的情况
低1 高1 高2 低2

## 答案
```
class Solution(object):
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        
        if not nums:
            return
        
        i = len(nums) - 1
        j = -1
        
        while i > 0:
            if nums[i] > nums[i-1]:
                j = i-1
                break
            i -= 1
            
        
        for i in range(len(nums)-1, -1, -1):
            if nums[i] > nums[j]:
                nums[i], nums[j] = nums[j], nums[i]
                nums[j+1:] = sorted(nums[j+1:])
                return
                
        
```
