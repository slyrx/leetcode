# 题目描述

# 解题思路
使用回溯。
首先对数组进行排序，然后遍历数组的每个元素，在选择当前元素时，判断是否于前一个

关键是要排序
主要是没有搞懂回溯的路径，搞懂了就知道为什么要做相同元素过滤了，通过打 log 的方式，明确了回溯的路径，因为是从右向左遍历的，所以会添加相同的元素。

```golang
Choose: 1 Subset: [1]
Choose: 2 Subset: [1 2]
Choose: 2 Subset: [1 2 2]
Unchoose: 2 Subset: [1 2 2]
Unchoose: 2 Subset: [1 2]
Unchoose: 1 Subset: [1]
Choose: 2 Subset: [2]
Choose: 2 Subset: [2 2]
Unchoose: 2 Subset: [2 2]
Unchoose: 2 Subset: [2]
```

# 实现代码
```golang
import "sort"

func subsetsWithDup(nums []int) [][]int {
	sort.Ints(nums) // 对数组进行排序
	var subsets [][]int // 存储结果的二维数组
	backtrack(nums, 0, []int{}, &subsets) // 调用回溯函数，找到所有子集
	return subsets
}

func backtrack(nums []int, start int, subset []int, subsets *[][]int) {
	temp := make([]int, len(subset)) // 创建一个临时切片用于存储当前子集
	copy(temp, subset) // 将当前子集拷贝到临时切片中
	*subsets = append(*subsets, temp) // 将当前子集添加到结果中

	for i := start; i < len(nums); i++ { // 遍历数组的每个元素
		if i > start && nums[i] == nums[i-1] { // 判断是否与前一个元素相同，若相同则跳过，避免重复结果， 这里有点儿似懂非懂
			continue
		}
		subset = append(subset, nums[i]) // 将当前元素加入到当前子集中
		fmt.Println("Choose:", nums[i], "Subset:", subset) // 打印选择的元素和当前子集
		backtrack(nums, i+1, subset, subsets) // 递归调用下一个元素
		fmt.Println("Unchoose:", nums[i], "Subset:", subset) // 打印撤销选择的元素和当前子集
		subset = subset[:len(subset)-1] // 将当前元素从当前子集中移除，继续遍历下一个元素
	}
}



```

# 时间复杂度

# 空间复杂度
