# 01 — Insert Node Before Tail in Doubly Linked List (Java)

## Problem
Given the head of a **Doubly Linked List**, insert a new node with value `X`
**just before the tail node**, and return the head of the updated list.

---

## Example
DLL: `10 <-> 20 <-> 30`  
Insert `25` before tail → `10 <-> 20 <-> 25 <-> 30`

---

## Intuition
To insert a node before the tail, we need to update **4 pointers**:

Let:
- `tail` be the last node
- `prevTail` be the node just before tail

Then insert `newNode` between them:

- `prevTail.next = newNode`
- `newNode.prev = prevTail`
- `newNode.next = tail`
- `tail.prev = newNode`

---

## Edge Cases Handled
### ✅ Case 1: Empty list
If `head == null`  
→ the new node itself becomes the list.

### ✅ Case 2: Single node list
If `head.next == null`  
→ inserting before tail means inserting **before the only node** (becomes new head).

---

## Approach
Instead of traversing till the last node, we traverse till the **second last node**:

- Use `temp` pointer
- Loop until `temp.next.next == null`
- At that moment:
  - `temp` = node before tail
  - `tail` = `temp.next`

Then insert the node in between.

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
    public ListNode insertBeforeTail(ListNode head, int X) {

        ListNode newNode = new ListNode(X);

        // Case 1: empty DLL
        if (head == null) {
            return newNode;
        }

        // Case 2: single node DLL
        if (head.next == null) {
            newNode.next = head;
            head.prev = newNode;
            return newNode;
        }

        // Traverse to second last node
        ListNode temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }

        ListNode tail = temp.next;

        // Insert newNode between temp and tail
        temp.next = newNode;
        newNode.prev = temp;

        newNode.next = tail;
        tail.prev = newNode;

        return head;
    }
}
