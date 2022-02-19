## Stack

Stack is one type of linear list (线性表). Stack can be implemented as either array or linked list.

### implement stack as array

we can do this using list in Python.
![image](https://user-images.githubusercontent.com/72336341/154809675-721c6286-4f85-4d2d-9470-b1ffb7b86504.png)
```python
class Stack:
    # initialize a stack
    def __init__(self,size):
        self.size = size
        self.top = -1 #top=-1 表示空栈
        self.stack = [ ] #in Python, we use list to implement stack as array

    # check if stack is empty
    def isEmpty(self):
        return self.top == -1
	# check if stack is full
    def isFull(self):
        return self.top == self.size-1
	#add an element to stack
    def push(self, value): 
        if self.isFull():
            raise Exception('Stack is full')
        else:
            # 正常的话是先top+=1，然后索引stack[top]=value，但在Python的实现方式不太一样，要注意!
            self.stack.append(value)
            self.top += 1
    #removing an element from the stack.
    def pop(self):
        if self.isEmpty():
            raise Exception('Stack is empty')
        else:
            self.stack.pop()
            self.top -= 1
    #peek(): return the top data element of the stack, without removing it.
    def peek(self):
        if self.isEmpty():
            raise Exception('Stack is empty')
        else:
            return self.stack[self.top]
        
        
    
```



Note that when the stack is full or we need to resize the stack, we need to create a larger stack and move a lot of elements to this new stack. In this case, implement stack as linked list is a better solution.

### implement stack as Linked List

in this case, it's implementation is actually linked list, but with restriction.
![image](https://user-images.githubusercontent.com/72336341/154809671-38e97e96-d4b5-4e73-82ff-bdf87a1bccdb.png)

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
class Stack:
    #initialize the stack, just assign top pointer to None.
    def __init__(self): 
        self.top = None
        
    def isEmpty(self):
        return self.top == None
    
    #do not implement def isFull(self)
    
    def push(self, value):
        cur = Node(value)
        cur.next = self.top
        self.top = cur
    #pop: remove element on the top of stack (must check if Empty!)    
    def pop(self):
        if self.isEmpty():
        	raise Exception('Stack is empty')
        else:
            cur = self.top
            self.top = self.top.next
            del cur
    #peek: return the top data element of the stack, without removing it. 
    def peek(self):
        if self.isEmpty():
        	raise Exception('Stack is empty')
        else:
           return self.top.value #not just self.top!!!
        
        
```


