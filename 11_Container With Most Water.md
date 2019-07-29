## 思路
创建左、右指针，以元素间的差值为宽，以记录的高度为高，将两者相乘计算面积。因为是模拟水，所以以最短的高度来计算。

## 关键
以倒序来遍历，由最大的值向最小的值进行收敛。

## 涉及的情况
![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

## 答案
```
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        
        left, right = 0, len(height)-1
        w = len(height)-1
        
        result = 0
        for w in range(w, 0, -1):
            if height[right] < height[left]:
                result = max(result, height[right]*w)
                right -= 1
            elif height[right] >= height[left]:
                result = max(result, height[left]*w)
                left += 1
                
        return result
```
