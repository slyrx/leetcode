## 解决思路
快速排序

## 答案代码
```
    def sortArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        sort_nums = nums
        
        def quickSort(nums, start, end):
            if start < end:
                p = partition(nums, start, end)
                quickSort(nums, start, p-1)
                quickSort(nums, p+1, end)
            
        def partition(nums, l, r):
            x = nums[r]
            i = l-1
            
            for j in xrange(l, r+1):
                if nums[j] < x:
                    i += 1
                    nums[i], nums[j] = nums[j], nums[i]
                    
            nums[i+1],nums[r] = nums[r], nums[i+1]
            
            return i+1
            
            
        quickSort(sort_nums, 0, len(nums)-1)
        
        
        return sort_nums

```
