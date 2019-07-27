## 思考
用 i-start 和 i-start+1 的区别是？
+ 返回值的不同
+ + 在树的题中，返回值是 max(sub_len, i-start+1)，因此，需要在计算的过程中就把+1的问题考虑进去
+ + 在本题中，返回的是 max(sub_len, len(s)-start),通过 len(s)-start 弥补了少1的情况。


