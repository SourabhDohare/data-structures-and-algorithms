# Doubly Linked List (DLL)

This folder contains **Doubly Linked List** concepts and interview-oriented problems.
Each problem includes:
- Clear explanation + pointer updates
- Edge cases
- Time & Space complexity
- Java implementation

---

## Why Doubly Linked List?
A Doubly Linked List is a linked list where each node has:
- `prev` pointer → previous node
- `next` pointer → next node

DLL makes operations efficient when we need:
- Bidirectional traversal
- Fast insertion/deletion near ends
- Real-world design patterns like **LRU Cache**

---

## Common Operations & Complexity

| Operation | Time |
|----------|------|
| Insert/Delete at head | O(1) |
| Insert/Delete at tail | O(1) |
| Insert/Delete before/after a node (if reference is known) | O(1) |
| Search / Access by index | O(n) |
| Reverse list | O(n) |

---

## Problems (In Order)

1. **Insert Node Before Tail in Doubly Linked List**
   - [`01-insert-node-before-tail-in-doubly-linked-list.md`](./problems/01-insert-node-before-tail-in-doubly-linked-list.md)

2. **Insert Node Before Kth Position in Doubly Linked List**
   - [`02-insert-node-before-kth-position-in-doubly-linked-list.md`](./problems/02-insert-node-before-kth-position-in-doubly-linked-list.md)
  
3. **Insert Node Before a Given Node in Doubly Linked List**
   - [`03-insert-node-before-given-node-in-doubly-linked-list.md`](./problems/03-insert-node-before-given-node-in-doubly-linked-list.md)

---

## Pointer Invariants (Important)
While working with DLL, always ensure:
- If `node.next != null` → `node.next.prev == node`
- If `node.prev != null` → `node.prev.next == node`
- `head.prev == null`
- `tail.next == null`


