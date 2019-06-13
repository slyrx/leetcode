## 单词
+ subtle 精妙的
+ the divide and conquer approach 分而治之的方法
+ conquer 征服
+ divide 分开

## 思路
+ 目标寻找最大子数组的和
+ 需要遍历元素进行累加
+ 遍历的起始位置会移动
+ 设立一个临时求和变量，保存每次求得的和
+ ***关键***: 当求得的和出现负值时，说明前面的元素对于组成最大数组已经没有更多的帮助，因此需要被丢弃。子数组的起始位置应该向后移动。

## 问题
+ 当最大的和本身就是负值要怎么办？<br>
现在临时的和初始化为了0，此处应该初始化为最小值float('-inf').实验了以后发现不行。<br>
+ 应该把要返回的结果和初始化为第一个元素，而不是最小值<br>
因为子数组最小也就是一个元素了，后续的情况就是在这个元素的基础上更好或者更差。因此作为基准，最起码要返回这个基准。
+ [1,2]的情况错到哪儿了？<br>
临时和的初始化值不应该为float('-inf')，而应该为0.<br>
差别在哪儿？<br>
为float('-inf')，在循环第一个元素时，***float('-inf')+1的结果为float('-inf')***<br>
因此，float('-inf')应该只用到赋值和判断上，而不能是运算求和。

## 答案
```
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        temp_sum = 0
        result_sum = nums[0]
        
        for i in nums:
            print i, temp_sum
            temp_sum += i
            print i, temp_sum
            result_sum = max(temp_sum, result_sum)
            
            if temp_sum < 0:
                temp_sum = 0
        
        return result_sum
```
