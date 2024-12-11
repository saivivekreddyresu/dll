class Node:
    def __init__(first, data=None):
        first.data = data
        first.next = None
        first.prev = None
class DLL:
    def __init__(first):
        first.head = None
    
    def insert(first, data):
        new_node = Node(data)
        if first.head is not None:
            first.head.prev = new_node
        new_node.next = first.head
        first.head = new_node
    def reverse(first):
        if first.head is None:
            return
        temp = None
        current = first.head
        while current:
            temp = current.prev
            current.prev = current.next
            current.next = temp
            current = current.prev
        if temp:
            first.head = temp.prev
    def display(first):
        current = first.head
        while current:
            print(current.data, end=' ')
            current = current.next
        print(' ')
dll = DLL()
n = int(input("Enter the number of elements to insert: "))
for i in range(n):
    data = int(input("Enter input: "))
    dll.insert(data)
print("Original list:")
dll.display()
dll.reverse()
print("Reversed list:")
dll.display()

