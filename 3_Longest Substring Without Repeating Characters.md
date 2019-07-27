## 思考
用 i-start 和 i-start+1 的区别是？
+ 返回值的不同
+ + 在904树的题中，返回值是 max(sub_len, i-start+1)，因此，需要在计算的过程中就把+1的问题考虑进去
+ + 在本题中，返回的是 max(sub_len, len(s)-start),通过 len(s)-start 弥补了少1的情况。
与904树的题的另外一个不同
+ 904中的 start 指针不需要跳跃，这个是求相同的连续，所以要挨个检查
+ 本题中的 start 指针需要跳跃，这个是求不同的唯一，所以能跳跃重复的元素

max(temp_len, len(s)-start)
+ 用来区别前面已经做了记录，间隔一段之后，后面又遇到一段新的子数组可以做比较。
+ 这点上和上面的问题是相通的

start = max(start, board\[x]+1)
+ 这种情况是描述 start 被某个元素已经带到很前面了，接着又遇到一个相隔很远的重复元素，此时 board\[x]+1 就会小于 start


## 列举可能出现的情形
+ ""
+ "a"
+ 已经求出了最大值和正在逐渐求最大值
+ + 前半段长度比后半段长度大的情况
+ + 前半段长度比后半段长度小的情况

## 答案
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        start = 0
        board = {}
        temp_len = 0
        
        for i, x in enumerate(s):
            if x in board:
                temp_len = max(temp_len, i-start)
                start = max(start, board[x]+1)
                
            board[x] = i
            
        return max(temp_len, len(s)-start)
```
