# LinearLinkedList

This repo contains all my required codes for Linear Linked list.

#==============================================================================================================================================================================

All the codes of Linear Linked List that will be written by me will stay here. Any Python code or any project related to my language will come here for ther homage requirements.


BASIC CODE FOR EVERY PROJECT :

#Data Structure : Part 1 Linked List

#================================================================

# Node Class
class Node:

    # Initiate Function
    def __init__(self,data):
        self.data = data
        self.next = None


# Linked List Class
class LinkedList:

    # Function to intialise Head
    def __init__(self):
        self.head = None

    # Printing the linked List

    def printList(self):
        temp = self.head
        while(temp):
            print(temp.data, end=" ")
            temp = temp.next



    # Insert an element in front.

    def insertFront(self, new_data):

        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node

    # Insert at given point

    def insertAfter(self, prev_node, new_data):

        if prev_node is None:
            print("The given list should be inward one")
            return

        new_node = Node(new_data)

        new_node.next = prev_node.next
        prev_node.next = new_node

    # Insert at End

    def insertEnd(self, new_data):

        new_node = Node(new_data)

        if self.head is None:

            self.head = new_node
            print("The given list is done")
            return

        last = self.head
        while(last.next):
            last = last.next

        last.next = new_node


    # Delete Node From Linked List

    def deleteNode(self,del_data):

        temp = self.head

        if (temp != None):
            if (temp.data == del_data):
                self.head = temp.next
                temp = None
                return

        while(temp != None):
            if (temp.data == del_data):
                break
            prev = temp
            temp = temp.next

        if (temp == None):
            return

        prev.next = temp.next

        temp = None


    # Count the number of nodes

    def count_get(self):
        count = 0
        temp = self.head

        while(temp):
            count+=1
            temp = temp.next
        return(count)


    # Swap Nodes

    def swapNodes(self, x, y):

        if(x==y):
            return

        prevX = None
        currX = self.head
        while((currX != None) and (currX.data != x)):
            prevX = currX
            currX = currX.next

        
        prevY = None
        currY = self.head
        while((currY != None) and (currY.data != y)):
            prevY = currY
            currY = currY.next

        if(currX == None or currY == None):
            return

        if(prevX != None):
            prevX.next = currY
        else:
            self.head = currY 


        if(prevY != None):
            prevY.next = currX
        else:
            self.head = currX


        temp = currX.next
        currX.next = currY.next
        currY.next = temp

    # Revrse a given Linked List

    def reverse(self):
        
        prev = None
        current = self.head 
        while(current is not None): 
            next = current.next
            current.next = prev 
            prev = current 
            current = next
        self.head = prev


    # Reverse A Bunch at one Time

    def size_reverse(self, head, k): 
        current = head  
        next  = None
        prev = None
        count = 0 
          
        while(current is not None and count < k): 
            next = current.next
            current.next = prev 
            prev = current 
            current = next 
            count += 1
  
    
        if next is not None: 
            head.next = self.size_reverse(next, k) 
  
         
        return prev 


    # Detect The Loop in a Linked list and Remove it.
    
    def detectAndRemoveLoop(self): 
        slow_p = fast_p = self.head 
        while(slow_p and fast_p and fast_p.next): 
            slow_p = slow_p.next 
            fast_p = fast_p.next.next
          
            
            if slow_p == fast_p: 
                self.removeLoop(slow_p) 
                  
                 
                return 1 
   
        return 0

  
    # Function to remove Loop
    
    def removeLoop(self, loop_node): 
         
        ptr1 = self.head 
        while(1): 
            
            ptr2 = loop_node 
            while(ptr2.next != loop_node and ptr2.next != ptr1): 
                ptr2 = ptr2.next
              
            
            if ptr2.next == ptr1 :  
                break 
              
            ptr1 = ptr1.next
          
        ptr2.next = None


    # Rotate about Kth Node

    def rotate(self, k): 
        if k == 0:  
            return 
     
        current = self.head 

        count = 1 
        while((count < k) and (current != None)): 
            current = current.next
            count += 1
    
            return
  
        kthNode = current  
      
        while(current.next != None): 
            current = current.next
  
        current.next = self.head 
           
        self.head = kthNode.next
  
        kthNode.next = None
        
#==================================================================

# Main Code

if __name__ == '__main__':

    # Empty List Maker
    llist = LinkedList()

    # Action Performed (Construction)
    llist.insertFront(6)
    llist.insertFront(7)
    llist.insertFront(1)
    llist.insertFront(4)
    llist.insertFront(8)

    # Printing Part without any Modifications
    print('Created Linked List is : ', end=" ")
    llist.printList()
    
    # Modifications done (Deleting, Reversing, etc)
    #llist.deleteNode(4)
    #llist.swapNodes(8,7)
    #llist.reverse()
    #llist.size_reverse(llist.head, 2)
    llist.rotate(2)
    
    # Printing Part after Modifications
    print("\nLinked List After Modification: ", end=" ")
    Number_node = llist.count_get()
    llist.printList()
    print("\nThe Number of nodes is: ", Number_node)

    
