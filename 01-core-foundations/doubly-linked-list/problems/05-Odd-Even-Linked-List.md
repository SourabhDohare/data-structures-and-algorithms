# 05 — Odd Even Linked List

## Problem
Given the head of a singly linked list, group all nodes with **odd indices** together followed by nodes with **even indices**, and return the reordered list.

The relative order inside the odd and even groups must remain the same.

---

## Example
Input:  
1 → 2 → 3 → 4 → 5  

Output:  
1 → 3 → 5 → 2 → 4  

---

## Intuition
We separate the linked list into two chains:
- One for nodes at **odd positions**
- One for nodes at **even positions**

We maintain the head of the even chain so that after processing we can attach it at the end of the odd chain.

All rearrangement is done **in-place** using pointer updates.

---

## Approach
1. Handle edge cases where list has 0 or 1 node.
2. Use two pointers:
   - `odd` starting at head
   - `even` starting at head.next
3. Store the head of the even list as `evenHead`.
4. Traverse while both even and even.next are not null:
   - Link the next odd node
   - Link the next even node
5. After the loop, connect the last odd node to the head of the even list.

---

## Java Code

```java
class Solution {
  public ListNode oddEvenList(ListNode head) {
    if (head == null || head.next == null) return head;

    ListNode odd = head;
    ListNode even = head.next;
    ListNode evenHead = even;

    while (even != null && even.next != null) {
      odd.next = even.next;
      odd = odd.next;

      even.next = odd.next;
      even = even.next;
    }

    odd.next = evenHead;
    return head;
  }
}
```
## Time Complexity

**O(n)**
- The list is traversed once.

## Space Complexity

**O(1)**
- Only a few pointers are used for rearrangement.
