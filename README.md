# Daa_code


class LinkedList:
 
    # Function to initialize head
    def _init_(self):
        self.head = None
 
    def reverse(self, head, k):
       
        if head == None:
          return None
        current = head
        next = None
        prev = None
        count = 0
 
        # Reverse first k nodes of the linked list
        while(current is not None and count < k):
            next = current.next
            current.next = prev
            prev = current
            current = next
            count += 1
 
        # next is now a pointer to (k+1)th node
        # recursively call for the list starting
        # from current. And make rest of the list as
        # next of first node
        if next is not None:
            head.next = self.reverse(next, k)
 
        # prev is new head of the input list
        return prev
 
    # Function to insert a new node at the beginning
    def push(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node
 
    # Utility function to print the linked LinkedList
    def printList(self):
        temp = self.head
        while(temp):
            print (temp.data)
            temp = temp.next
 
 
# Driver program
llist = LinkedList()
llist.push(5)
llist.push(4)
llist.push(3)
llist.push(2)
llist.push(1)
 
print ("Given linked list")
llist.printList()
k = int(input("enter the kth element"))
llist.head = llist.reverse(llist.head, k)
 
print ("\nReversed Linked list")
llist.printList()
