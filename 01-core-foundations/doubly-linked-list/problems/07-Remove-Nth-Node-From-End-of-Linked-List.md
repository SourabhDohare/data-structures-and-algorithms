# 07 — Remove Nth Node From End of Linked List (Java)

## Problem
Given the head of a singly linked list, remove the Nth node from the end of the list and return the head of the modified list.

---

## Example
Input:
1 → 2 → 3 → 4 → 5, n = 2

Output:
1 → 2 → 3 → 5
---

## Intuition
To remove the Nth node from the end, we need to identify the node just before it.

A straightforward way is:

1. First, calculate the length of the linked list.
2. Convert “Nth from end” into a position from the start.
3. Traverse to the node before the target and update pointers.

This avoids unnecessary complexity and keeps pointer manipulation controlled.
---

## Approach
1. Handle the edge case when the list is empty.
2. Traverse the list once to compute its total length.
3. If n equals the list size, remove the head node.
4. Traverse again to the (size - n)th node.
5. Skip the next node by rewiring pointers.
6. Return the head.

---

## Java Code

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head == null) {
            return null;
        }

        ListNode temp = head;
        int size = 0;

        // First pass: calculate length
        while (temp != null) {
            size++;
            temp = temp.next;
        }

        // If head needs to be removed
        if (size == n) {
            return head.next;
        }

        // Second pass: reach node before target
        temp = head;
        for (int i = 1; i < size - n; i++) {
            temp = temp.next;
        }

        // Remove the nth node from end
        temp.next = temp.next.next;
        return head;
    }
}

```
## Time Complexity

**O(n)**
 - One traversal to compute length.
 - One traversal to remove the node
 
## Space Complexity

**O(1)**
 - No extra data structures used.
