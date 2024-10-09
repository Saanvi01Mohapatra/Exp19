# Experiment 19: Linked List Implementation

## Aim
To study and implement linked lists in C++.

## Theory
A **linked list** is a fundamental data structure used in computer science to store collections of elements (nodes) where each node points to the next one, forming a sequential chain. Unlike arrays, linked lists allow dynamic memory allocation, enabling them to grow and shrink as needed during runtime. This flexibility makes them particularly useful for applications where the number of elements is unpredictable.

### Types of Linked Lists
1. **Singly Linked List**: Each node contains data and a pointer to the next node. The last node points to `nullptr`, indicating the end of the list.
2. **Doubly Linked List**: Each node contains a pointer to both the next and the previous node, allowing traversal in both directions.
3. **Circular Linked List**: The last node points back to the first node, creating a circular structure that can be useful in certain applications.

### Basic Operations
- **Insertion**: Adding a new node to the list, which can occur at the beginning, middle, or end.
- **Deletion**: Removing a node based on its value or position within the list.
- **Traversal**: Visiting each node in the list to display or process its data.

Understanding linked lists is crucial for implementing more complex data structures and algorithms, and they are widely used in various applications such as dynamic memory allocation, real-time simulations, and more.

## Code Implementation

### 1. Linked List
```
// Name: Saanvi
// PRN: 23070123110
// Class: EnTC B-2

#include<iostream>
using namespace std;

class Link {
public:
    int data;
    Link* next;
    Link(int num) {
        data = num;
        next = NULL;
    }
};

void insert_head(Link* &head, int data) {
    Link* new_node = new Link(data);
    new_node->next = head; 
    head = new_node;
}

void disp(Link* head) {
    Link* temp = head;
    while(temp != NULL) { 
        cout << temp->data << "->";
        temp = temp->next;
    } 
    cout << "NULL" << endl;
}

int main() {
    Link* head = NULL;
    insert_head(head, 30);
    disp(head);
    insert_head(head, 32);
    disp(head);
    insert_head(head, 35);
    disp(head);
}
```
# Output:
```
100->NULL
200->100->NULL
500->200->100->NULL
```
### 2. Inserting, Displaying, and Deleting Linked List Nodes
```
// Name: Saanvi
// PRN: 23070123110
// Class: EnTC B-2

#include<iostream>
using namespace std;

class Link {
public:
    int data;
    Link* next;
    Link(int num) {
        data = num;
        next = NULL;
    }
};

void insert_head(Link* &head, int data) {
    Link* new_node = new Link(data);
    new_node->next = head; 
    head = new_node;
}

void disp(Link* head) {
    Link* temp = head;
    while(temp != NULL) { 
        cout << temp->data << "->";
        temp = temp->next;
    } 
    cout << "NULL" << endl;
}

void delete_node(Link* &head, int value) {
    if(head == NULL) {
        cout << "List is empty, nothing to delete." << endl;
        return;
    }
    Link* temp = head;
    Link* prev = NULL;

    if(temp != NULL && temp->data == value) {
        head = temp->next;
        delete temp;
        return;
    }

    while(temp != NULL && temp->data != value) {
        prev = temp;
        temp = temp->next;
    }

    if(temp == NULL) {
        cout << "Node with value " << value << " not found." << endl;
        return;
    }

    prev->next = temp->next;
    delete temp;
}

int main() {
    Link* head = NULL;
    insert_head(head, 30);
    disp(head);
    insert_head(head, 32);
    disp(head);
    insert_head(head, 35);
    disp(head);
    delete_node(head, 32); 
    disp(head);
    delete_node(head, 35); 
    disp(head);
    delete_node(head, 100); 
    disp(head);
}
```
# Output:
```
30->NULL
32->30->NULL
35->32->30->NULL
35->30->NULL
30->NULL
Node with value 100 not found.
30->NULL
```
# Conclusion
This experiment successfully demonstrated the significance and efficiency of linked lists in C++ programming. The implementation illustrated the advantages of linked lists in terms of dynamic memory management and operation efficiency, while also emphasizing the necessity for careful pointer management to prevent memory leaks or crashes. This foundational understanding of linked lists paves the way for exploring more advanced data structures and algorithms.
