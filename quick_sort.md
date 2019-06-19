## 分治法
+ partition
+ quick_sort

+ array[i],array[j] = array[j], array[i]的理解
+ + 当i和j指向相同当位置时，执行的就是array[0]和array[0]的调换，也就是自己和自己的调换，

```
def quick_sort(nums, l, r):
    if l < r:
       p = partition(nums, l, r)
       quick_sort(nums, l, p-1)
       quick_sort(nums, p+1, r)
    
def partition(nums, l, r):
    x = nums[r]
    i = l -1
    
    for j in xrange(l, r+1):
        if nums[j] < x:
          i += 1
          nums[i], nums[j] = nums[j], nums[i]
    nums[i+1], nums[r] = nums[r], nums[i + 1]
    
    return i+1

```
