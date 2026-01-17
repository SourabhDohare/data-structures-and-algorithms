# 02 — Insert Node Before Kth Position in Doubly Linked List (Java)

## Problem
Given the head of a **Doubly Linked List**, insert a new node with value `X`
**before the Kth position (1-indexed)** and return the head of the updated list.

---

## Example
DLL: `10 <-> 20 <-> 30 <-> 40`

- Insert `15` before `K = 2`  
  Result: `10 <-> 15 <-> 20 <-> 30 <-> 40`

- Insert `5` before `K = 1`  
  Result: `5 <-> 10 <-> 20 <-> 30 <-> 40`

---

## Intuition
To insert a node before the Kth node, first locate the **Kth node (`temp`)**.

Then insert `newNode` between:
- `prevNode = temp.prev`
- `temp`

Pointer updates:

- `prevNode.next = newNode`
- `newNode.prev = prevNode`
- `newNode.next = temp`
- `temp.prev = newNode`

---

## Approach
1. Handle base cases:
   - empty list
   - `K = 1` (insert before head)
2. Traverse to the **Kth node**
3. If Kth node doesn't exist → insert at the end (tail insertion)
4. Otherwise → perform constant pointer updates to insert before `temp`

---

## Java Code

```java
/*
class ListNode {
    public int data;
    public ListNode prev;
    public ListNode next;
    public ListNode();
    public ListNode(int data);
    public ListNode(int data, ListNode prev, ListNode next);
};
*/

class Solution {
    public ListNode insertBeforeKthPosition(ListNode head, int X, int K) {

        if (head == null) {
            return new ListNode(X);
        }

        ListNode newNode = new ListNode(X);

        // Insert before head
        if (K == 1) {
            newNode.next = head;
            head.prev = newNode;
            return newNode;
        }

        // Traverse to Kth node
        ListNode temp = head;
        int count = 1;

        while (temp != null && count < K) {
            temp = temp.next;
            count++;
        }

        // If K is out of bounds -> insert at end
        if (temp == null) {
            ListNode tail = head;
            while (tail.next != null) {
                tail = tail.next;
            }

            tail.next = newNode;
            newNode.prev = tail;
            return head;
        }

        // Insert before temp (Kth node)
        ListNode prevNode = temp.prev;

        prevNode.next = newNode;
        newNode.prev = prevNode;

        newNode.next = temp;
        temp.prev = newNode;

        return head;
    }
}
```
Time Complexity

O(n)
Because we may need to traverse the DLL to reach the Kth node (worst case: full traversal).

Space Complexity

O(1)
Only constant extra pointers are used.

Key Interview Notes

Always handle K = 1 separately → insertion before head.

Store prevNode = temp.prev before pointer updates (avoid losing reference).

Pointer invariant after insertion:

prevNode.next == newNode

newNode.prev == prevNode

newNode.next == temp

temp.prev == newNode

Be clear about what happens when K is out of bounds (here: insert at tail).
