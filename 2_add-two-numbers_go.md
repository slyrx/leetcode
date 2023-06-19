# 题意描述

# 解题思路
可以通过遍历 2 个链表，并将对应位置的数字相加，同时考虑进位的情况。
创建一个新的链表，用于存储相加后的结果。
遍历过程中，使用一个变量 carry 来记录进位值，初始值为 0 。
将两个链表对应位置的数字相加，并加上进位值，将和的个位数作为新链表的节点值，并更新进位值。
遍历结束后，若进位值仍然大于 0 ，则将其作为新链表的额外节点，最终得到的新链表即为两数相加的结果。

# 实现代码
```golang
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	dummy := &ListNode{} // 哑节点，方便操作链表
	curr := dummy        // 当前节点
	carry := 0           // 进位值

	for l1 != nil || l2 != nil {
		sum := carry // 当前位置的和等于进位值
		if l1 != nil {
			sum += l1.Val // 加上 l1 的值
			l1 = l1.Next  // 移动 l1 的指针
		}
		if l2 != nil {
			sum += l2.Val // 加上 l2 的值
			l2 = l2.Next  // 移动 l2 的指针
		}
		carry = sum / 10    // 计算新的进位值
		curr.Next = &ListNode{Val: sum % 10} // 创建新节点
		curr = curr.Next   // 移动当前指针
	}

	if carry > 0 {
		curr.Next = &ListNode{Val: carry} // 若有剩余的进位值，创建额外节点
	}

	return dummy.Next // 返回结果链表的起始节点
}
```

# 时间复杂度
O(max(m, n))
# 空间复杂度
O(max(m, n))



