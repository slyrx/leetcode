## code
```
def heapsort(nums):
    
    n = len(nums)-1
    parent_end = n/2
    for i in range(parent_end):
        heap_adjust(nums, i, n)

    for i in range(n):
        nums[1], nums[n] = nums[n], nums[1]
        heap_adjust(nums, 1, n-i) 

def heap_adjust(nums, start, end):
    temp = nums[start]
    i = start
    j = 2*i

    while j<=end:
        if j < end and nums[j] < nums[j+1]:
            j +=1
        
        if temp < nums[j]:
            nums[i] = nums[j]
            i = j
            j = 2*i
        else:
            break
        
    nums[j] = temp

```