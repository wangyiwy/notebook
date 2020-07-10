# 链表反转



* 使用栈：在原本链表的数据结构之外，引入一个栈/数组，将单链表循环遍历，将所有结点入栈，最后再从栈中循环出栈，记住出栈的顺序，得到的就是反转后的单链表。空间复杂度就变成了 O\(n\)

  ```go
    func reverse(head *Node) *Node {
        if head == nil || head.Next == nil {
            return head
        }

        var arr []*Node
        node := head
        for node != nil {
            arr = append(arr, node)
            node = node.Next
        }

        for i := len(arr) - 1; i >= 0; i-- {
            node1 := arr[i]
            if i-1 >= 0 {
                node2 := arr[i-1]
                node1.Next = node2
            } else {
                node1.Next = nil
            }
        }

        if arr != nil {
            return arr[len(arr)-1]
        }
        return nil
    }
  ```

* 遍历法：我们需要知道三个结点:待翻转的结点、待反转结点的前驱结点 prev、待反转结点的后续结点next,以头结点为参数，反转之后返回值为反转后的单链表头结点

  ```go
    func reverse(head *Node) *Node {
        if head == nil || head.Next == nil {
            return head
        }

        var prev *Node
        var next *Node
        for head != nil {
            next = head.Next
            head.Next = prev
            prev = head
            head = next
        }
        return prev
    }
  ```

* 递归法：先反转后面的链表，从最后面的两个结点开始反转，依次向前，将后一个链表结点指向前一个结点，注意每次反转后要将原链表中前一个结点的指针域置空，表示将原链表中前一个结点指向后一个结点的指向关系断开。

  ```go
    func reverse(head *Node) *Node {
        if head == nil || head.Next == nil {
            return head
        }

        var node = reverse(head.Next)
        head.Next.Next = head
        head.Next = nil
        return node
    }
  ```

