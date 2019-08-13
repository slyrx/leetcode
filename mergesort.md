## code

```
def mergesort(nums, start, end):
    if start < end:
        mid = (start + end)/2
        mergesort(nums, start, mid)
        mergesort(nums, mid+1, end)
        merge(nums, start, mid, end)


def merge(nums, start, mid, end):
    array = []
    for i in nums:
        array.append(i)

    left = start
    right = mid + 1
    current = end

    while left <= mid and right <= end:
        if array[left] < array[right]:
            nums[current] = array[left]
            left += 1
        else:
            nums[current] = array[right]
            right += 1

        current += 1
     
     remaining = mid - left
     for i in range(remaining):
        nums[current+i] = array[left+i]

```