# 题目描述

# 解题思路
通过选择一个基准元素，把数组分成 2 部分。分别是大于基准元素的部分和小于基，准元素的部分。
然后判断基准元素所在的位置与目标位置的关系，
如果基准元素的位置大于目标位置，说明目标元素在基准元素的左侧，递归地在左侧部分进行查找。
如果基准元素的位置小于目标位置，说明目标元素在基准元素的右侧，递归地在右侧部分进行查找。
重复这个过程，直到找到第 k 个最大元素。

具体而言，targetIdx := len(nums) - k 将目标位置 k 转换为对应的下标索引。假设数组长度为 n，那么下标索引范围是从 0 到 n-1。当 k 为 1 时，即要找到最大元素，其下标索引为 n-1。当 k 为 2 时，即要找到第二大元素，其下标索引为 n-2。以此类推，当 k 为 k 时，第 k 个最大元素的下标索引为 n-k。

所以，通过 targetIdx := len(nums) - k 将目标位置 k 转换为下标索引，我们可以在数组中定位到第 k 个最大元素。

# 实现代码
```golang
func findKthLargest(nums []int, k int) int {
    // 根据目标位置 k 转换为下标索引
    targetIdx := len(nums) - k
    return quickSelect(nums, 0, len(nums)-1, targetIdx)
}

// 快速选择算法
func quickSelect(nums []int, left, right, targetIdx int) int {
    // 划分数组，获取基准元素的位置
    pivotIdx := partition(nums, left, right)
    
    // 基准元素的位置与目标位置的关系
    if pivotIdx == targetIdx {
        return nums[pivotIdx]
    } else if pivotIdx < targetIdx {
        // 目标元素在基准元素的右侧，递归地在右侧部分进行查找
        return quickSelect(nums, pivotIdx+1, right, targetIdx)
    } else {
        // 目标元素在基准元素的左侧，递归地在左侧部分进行查找
        return quickSelect(nums, left, pivotIdx-1, targetIdx)
    }
}

// 划分数组，返回基准元素的位置
func partition(nums []int, left, right int) int {
    // 选择最右边的元素作为基准元素
    pivot := nums[right]
    // 定义划分的边界索引
    i := left
    
    // 将小于基准元素的数移到左边，大于基准元素的数移到右边
    for j := left; j < right; j++ {
        if nums[j] < pivot {
            nums[i], nums[j] = nums[j], nums[i]
            i++
        }
    }
    
    // 将基准元素放到合适的位置
    nums[i], nums[right] = nums[right], nums[i]
    
    return i
}
```

# 时间复杂度
平均情况下为 O(n)，最坏情况下为 O(n^2)
# 空间复杂度
O(1)
