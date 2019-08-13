## code 
```
def selectsort(nums):
    n = len(nums)
    
    for i in range(n-1):
        min_index = i
        for j in range(i,n-1):
            if nums[j] < nums[j+1]:
                min_index = j
            else:
                min_index = j+1
        
        nums[min_index], nums[i] = nums[i], nums[mid_index] 

```