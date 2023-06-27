# 题目描述

# 解题思路
```golang
	if sum%k != 0 {
		return false
	}，这段代码的目的是干什么？
```
这段代码的目的是检查数组中所有元素的和 sum 是否能够被 k 整除。如果不能整除，意味着无法将数组划分为 k 个相等的子集，因为每个子集的和必须是整数，不能有剩余。因此，如果 sum 不能被 k 整除，函数会立即返回 false，表示无法满足划分的条件，节省了后续不必要的计算和搜索过程。

回溯的关键是回退和剪枝的操作。

# 实现代码
```golang
func canPartitionKSubsets(nums []int, k int) bool {
    sum := 0
    mx := nums[0]
    n := len(nums)

    // Calculate the sum of all elements in nums and find the maximum element
    for _, nu := range nums {
        sum += nu
        if nu > mx {
            mx = nu
        }
    }

    // If the sum is not divisible by k, it is not possible to partition into equal subsets
    if sum%k != 0 {
        return false
    }

    // Calculate the average value for each subset
    avg := sum / k

    // Sort the nums array in non-decreasing order
    sort.Ints(nums)

    ans := false
    arr := make([]int, k) // Create an array to track the sum of each subset

    // Define the DFS function to perform backtracking
    var dfs func(i int)
    dfs = func(i int) {
        // if ans {
        //     return
        // }

        // Base case: all elements have been assigned to subsets
        if i < 0 {
            ans = true
            return
        }

        lessCnt := 0
        for _, v := range arr {
            if v < avg {
                lessCnt++
            }
        }
        // Optimization: check if there are more subsets with sums less than avg than the remaining unassigned elements
        if lessCnt > i+1 {
            return
        }

        // Try assigning the current element to different subsets
        for j, v := range arr {
            if j > 0 && v == arr[j-1] {
                continue
            }

            // Optimization: if adding the current element exceeds the average, skip to the next subset
            if v+nums[i] > avg {
                continue
            }

            // Add the current element to the j-th subset
            arr[j] += nums[i]
            dfs(i - 1) // Recursively assign the next element
            // Backtrack: remove the current element from the j-th subset
            arr[j] -= nums[i]
        }
    }

    dfs(n - 1) // Start the backtracking process from the last element

    return ans // Return the final result
}

```

# 时间复杂度

# 空间复杂度
