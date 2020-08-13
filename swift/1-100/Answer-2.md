# LeeCodeSwiftAnswer - 两数相加 -2
>难度：中等

###题目描述
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

**示例:**
```
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```


###递归遍历
> 首先从最低有效位也就是列表 l1 和 l2 的表头开始相加。由于每位数字都应当处于 0…9 的范围内，我们计算两个数字的和时可能会出现 “溢出”。例如，5 + 7 = 12。在这种情况下，我们会将当前位的数值设置为 2，并将进位 carry = 1带入下一次迭代。进位 carry 必定是 0 或 1，这是因为两个数字相加（考虑到进位）可能出现的最大和为 9 + 9 + 1 = 19。

```
func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        return addTwoNumbersWith(l1,l2,0)
    }

    func addTwoNumbersWith(_ l1: ListNode?, _ l2: ListNode?, _ more : Int) -> ListNode? {
        var result:ListNode?
        if l1 == nil && more == 0 {
            return l2
        }

        if l2 == nil && more == 0 {
            return l1
        }

        if l1 == nil && l2 == nil && more == 0 {
            return l1
        }

        let index:Int = (l1?.val ?? 0 ) + (l2?.val ?? 0 ) + more
        result = ListNode.init(index % 10)
        result?.next = addTwoNumbersWith(l1?.next,l2?.next,index/10)
        return result
    }
```