# 06 — Sort-Linked List of 0s, 1s, and 2s (Java)

## Problem
Given the head of a singly linked list containing only values 0, 1, and 2, sort the linked list in ascending order.

The sorting should be done in-place, without modifying the structure of the nodes.

---

## Example
Input:
1 → 2 → 0 → 1 → 2 → 0

Output:
0 → 0 → 1 → 1 → 2 → 2 

---

## Intuition
Since the linked list contains only three distinct values (0, 1, 2), we don’t need a comparison-based sorting algorithm.

Instead:

 - Count how many 0s, 1s, and 2s are present

 - Overwrite the node values in sorted order

This keeps the solution simple, efficient, and easy to reason about.

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

1. Handle the edge case where the list is empty.
2. Traverse the list once and count:
	- number of 0s
	- number of 1s
	- number of 2s
3. Reset the traversal pointer to the head.
4. Overwrite node values in this order:
	- all 0s
	- then all 1s
	- then all 2s
5. Return the head of the sorted list.

---

## Java Code

```java
class Solution {
    public ListNode sortList(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode temp = head;
        int zeros = 0, ones = 0, twos = 0;

        // First pass: count 0s, 1s, and 2s
        while (temp != null) {
            if (temp.data == 0) {
                zeros++;
            } else if (temp.data == 1) {
                ones++;
            } else {
                twos++;
            }
            temp = temp.next;
        }

        // Second pass: overwrite node values
        temp = head;

        while (zeros-- > 0) {
            temp.data = 0;
            temp = temp.next;
        }

        while (ones-- > 0) {
            temp.data = 1;
            temp = temp.next;
        }

        while (twos-- > 0) {
            temp.data = 2;
            temp = temp.next;
        }

        return head;
    }
}

```
## Time Complexity

**O(n)**
	- One traversal for counting.
	- One traversal for overwriting
## Space Complexity

**O(1)**
	- No extra data structures used.
	- Sorting done in-place
