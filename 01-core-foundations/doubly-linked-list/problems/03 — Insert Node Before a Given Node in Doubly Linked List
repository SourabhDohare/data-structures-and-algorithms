# 03 — Insert Node Before a Given Node in Doubly Linked List (Java)

## Problem
Given a **node reference** in a Doubly Linked List, insert a new node with value `X`
**just before the given node**.

Note: We are not given the head of the list, only a pointer/reference to the target node.

---

## Example
DLL: `10 <-> 20 <-> 30 <-> 40`

Given node = `30`  
Insert `25` before it

Result: `10 <-> 20 <-> 25 <-> 30 <-> 40`

---

## Intuition
Since this is a **Doubly Linked List**, each node has both:
- `prev` pointer
- `next` pointer

So if we are given the `node`, we can directly access:
- `prevNode = node.prev`

Then insert `newNode` between:
- `prevNode`
- `node`

Pointer updates required:

- `prevNode.next = newNode`
- `newNode.prev = prevNode`
- `newNode.next = node`
- `node.prev = newNode`

---

## Approach
1. Create a new node `newNode` with value `X`
2. Store the previous node of the given node: `prevNode = node.prev`
3. Update links to insert `newNode` between `prevNode` and `node`

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
    public void insertBeforeGivenNode(ListNode node, int X) {

        ListNode newNode = new ListNode(X);

        ListNode prevNode = node.prev;

        prevNode.next = newNode;
        newNode.prev = prevNode;

        newNode.next = node;
        node.prev = newNode;
    }
}
```

## Time Complexity
- **O(1)**  
  Because we directly insert before the given node using its `prev` pointer (no traversal needed).

## Space Complexity
- **O(1)**  
  Only constant extra pointers are used (and one new node).

---

## Key Interview Notes
- In a Doubly Linked List, insertion **before a given node** can be done in **O(1)** because `prev` pointer is available.
- Pointer update order matters: store `prevNode = node.prev` before rewiring links.
- Edge case: if the given node is the **head**, then `node.prev == null` and this code will cause `NullPointerException`.
  - In interview, mention handling head case separately if constraints allow.
- Pointer invariants after insertion:
  - `prevNode.next == newNode`
  - `newNode.prev == prevNode`
  - `newNode.next == node`
  - `node.prev == newNode`
