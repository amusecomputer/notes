### **Node Class**

```javascript
class Node {
  constructor(data) {
    this.data = data; // Value stored in the node
    this.next = null; // Pointer to the next node
  }
}
```

### **Linked List Class**

```javascript
class LinkedList {
  constructor() {
    this.head = null; // Start with an empty list
  }

  // Append a new node at the end
  append(data) {
    let newNode = new Node(data);

    if (this.head === null) {
      this.head = newNode; // If the list is empty, the new node becomes the head
      return;
    }

    let current = this.head;
    while (current.next !== null) {
      current = current.next; // Traverse to the last node
    }

    current.next = newNode; // Add the new node at the end
  }

  // Prepend a new node at the beginning
  prepend(data) {
    let newNode = new Node(data);
    newNode.next = this.head; // Point the new node to the current head
    this.head = newNode; // Update the head to the new node
  }

  // Delete a node by its value
  deleteByValue(value) {
    if (this.head === null) return; // Empty list

    // If the node to be deleted is the head
    if (this.head.data === value) {
      this.head = this.head.next; // Move the head to the next node
      return;
    }

    let current = this.head;
    while (current.next !== null && current.next.data !== value) {
      current = current.next; // Traverse the list
    }

    if (current.next !== null) {
      current.next = current.next.next; // Skip the node to delete it
    }
  }

  // Print the entire list
  printList() {
    let current = this.head;
    while (current !== null) {
      console.log(current.data);
      current = current.next; // Move to the next node
    }
  }
}
```

### **Usage Example**

```javascript
let list = new LinkedList();

list.append(10); // Add 10
list.append(20); // Add 20
list.append(30); // Add 30
list.printList(); // Output: 10, 20, 30

list.prepend(5); // Add 5 at the beginning
list.printList(); // Output: 5, 10, 20, 30

list.deleteByValue(20); // Remove 20
list.printList(); // Output: 5, 10, 30
```
