# 04 — Add Two Numbers Represented by Linked Lists (Java)

## Problem
You are given two **non-empty singly linked lists** representing two non-negative integers.  
The digits are stored in **reverse order**, and each node contains a single digit.

Add the two numbers and return the sum as a linked list in the same reversed format.

---

## Example
Input:  
l1 = 2 → 4 → 3  
l2 = 5 → 6 → 4  

Output:  
7 → 0 → 8  

Explanation:  
342 + 465 = 807

---

## Intuition
This problem is the same as **manual digit-by-digit addition**:

- Add corresponding digits from both lists
- Keep track of carry
- Store the last digit of the sum in a new node
- Continue until both lists and carry are exhausted

Since digits are stored in reverse order, we can directly process from head.

---

## Approach
1. Create a dummy node to simplify building the result list.
2. Maintain a pointer `current` for constructing the answer.
3. Maintain a variable `carry`.
4. Traverse while at least one list still has nodes or carry is non-zero.
5. Add digits from `l1`, `l2`, and `carry`.
6. Create a new node with `sum % 10`.
7. Update carry as `sum / 10`.
8. Return `dummy.next`.

---

## Java Code

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;

            if (l1 != null) {
                sum += l1.data;
                l1 = l1.next;
            }

            if (l2 != null) {
                sum += l2.data;
                l2 = l2.next;
            }

            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
        }

        return dummy.next;
    }
}

```
## Time Complexity

- **O(max(n, m))**
We traverse both linked lists once.

## Space Complexity

- **O(max(n, m))**
A new linked list is created to store the result.

---
## Key Interview Notes

Always include carry != 0 in the loop condition (e.g., 5 + 5 = 10).

Use a dummy node to simplify result construction.

This approach avoids integer overflow completely.

Works even when the lists are of different lengths.

Never convert the list into a number — it fails for large inputs.
