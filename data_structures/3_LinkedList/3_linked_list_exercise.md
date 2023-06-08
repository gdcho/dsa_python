# Exercise: Linked List

1. In [LinkedList class](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/3_LinkedList/3_linked_list.py) that we implemented in our tutorial add following two methods,
```
def insert_after_value(self, data_after, data_to_insert):
    # Search for first occurance of data_after value in linked list
    # Now insert data_to_insert after data_after node

def remove_by_value(self, data):
    # Remove first node that contains data
```
Now make following calls,
```
    ll = LinkedList()
    ll.insert_values(["banana","mango","grapes","orange"])
    ll.print()
    ll.insert_after_value("mango","apple") # insert apple after mango
    ll.print()
    ll.remove_by_value("orange") # remove orange from linked list
    ll.print()
    ll.remove_by_value("figs")
    ll.print()
    ll.remove_by_value("banana")
    ll.remove_by_value("mango")
    ll.remove_by_value("apple")
    ll.remove_by_value("grapes")
    ll.print()
```
My solution:
```
def insert_after_value(self, data_after, data_to_insert):
    if self.head is None:
            return
            
    itr = self.head
    while itr:
        if itr.data == data_after:
                node = Node(data_to_insert, itr.next)
                itr.next = node
                break
    itr = itr.next
            
def remove_by_value(self, data):
    if self.head is None:
        return
    itr self.head
    while itr:
        if itr.data == data:
        itr = itr.next.next
        break
    itr = itr.next
    
```
[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/3_LinkedList/Solution/singly_linked_list_exercise.py)

2. Implement doubly linked list. The only difference with regular linked list is that double linked has prev node reference as well. That way you can iterate in forward and backward direction.
Your node class will look this this,
```
class Node:
    def __init__(self, data=None, next=None, prev=None):
        self.data = data
        self.next = next
        self.prev = prev
```
Add following new methods,
```
def print_forward(self):
    # This method prints list in forward direction. Use node.next

def print_backward(self):
    # Print linked list in reverse direction. Use node.prev for this.
```
Implement all other methods in [regular linked list class](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/3_LinkedList/3_linked_list.py) and make necessary changes for doubly linked list (you need to populate node.prev in all those methods)

My solution:
```
class Node:
    def __init__(self, data=None, next=None, prev=None):
        self.data = data
        self.next = next
        self.prev = prev
        
class DoublyLinkedList:
    def __init__(self):
        self.head = None
        
    def print_forward(self):
        if self.head = None:
            print("Empty list")
            return
            
        itr = self.head
        llstr = ''
        while itr:
            llstr += str(itr.data) + ' --> '
            itr = itr.next
        print(llstr)
    def print_backword(self):
        if self.head = None:
            print("Empty list")
            return
        
        itr = self.get_last_node()
        llstr = ''
        while itr:
            llstr += itr.data + '-->'
            itr = itr.prev
        print(llstr)
        
      def get_last_node(self):
        itr = self.head
        while itr.next:
            itr = itr.next
        return itr
    def get_length(self):
        count = 0
        itr = self.head
        while itr:
            count+=1
            itr = itr.next
        return count
    def insert_at_begining(self, data):
        if self.head == None:
            node = Node(data, self.head, None)
            self.head = node
        else:
            node = Node(data, self.head, None)
            self.head.prev = node
            self.head = node
    def insert_at_end(self, data):
        if self.head is None:
            self.head = Node(data, None, None)
            return
        itr = self.head
        while itr.next:
            itr = itr.next
        itr.next = Node(data, None, itr)
    def insert_at(self, index, data):
        if index<0 or index>self.get_length():
            raise Exception("Invalid Index")
        if index==0:
            self.insert_at_begining(data)
            return
        count = 0
        itr = self.head
        while itr:
            if count == index - 1:
                node = Node(data, itr.next, itr)
                if node.next:
                    node.next.prev = node
                itr.next = node
                break
            itr = itr.next
            count += 1
    def remove_at(self, index):
        if index<0 or index>=self.get_length():
            raise Exception("Invalid Index")
        if index==0:
            self.head = self.head.next
            self.head.prev = None
            return
        count = 0
        itr = self.head
        while itr:
            if count == index:
                itr.prev.next = itr.next
                if itr.next:
                    itr.next.prev = itr.prev
                break
            itr = itr.next
            count+=1
    def insert_values(self, data_list):
        self.head = None
        for data in data_list:
            self.insert_at_end(data)
            
```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/3_LinkedList/Solution/doubly_linked_list_exercise.py)
