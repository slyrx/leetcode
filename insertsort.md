## code
```
def insertsort(nums):
    n = len(nums)

    for i in range(n-1):
        for j in range(i, 0, -1):
            if nums[j] < nums[j-1]:
                nums[j-1], nums[j] = nums[j], nums[j-1]
            else:
                break

```