## code
```
def bubblesort(nums):
    n = len(nums)-1

    for i in range(n-1):
        for j in range(0, n-1-i):
            if nums[j] > nums[j+1]:
                nums[j], nums[j+1] = nums[j+1], nums[j]

```