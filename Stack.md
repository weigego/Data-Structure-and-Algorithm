## Stack
updated 2022/02/20 by wei
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
## Application

堆栈的后进先出规则，可以保证特定的存取顺序。

e.g. 翻转一组元素的顺序、铁路列车车辆调度、函数调用栈、浏览器的前进后退

#### 利用栈求解逆波兰（后缀）表达式

https://leetcode-cn.com/problems/evaluate-reverse-polish-notation/

逆波兰表达式是一种后缀表达式，所谓后缀就是指算符写在后面。

平常使用的算式则是一种中缀表达式，如 ( 1 + 2 ) * ( 3 + 4 ) 。
该算式的逆波兰表达式写法为 ( ( 1 2 + ) ( 3 4 + ) * ) 。
逆波兰表达式主要有以下两个优点：

去掉括号后表达式无歧义，上式即便写成 1 2 + 3 4 + * 也可以依据次序计算出正确结果。
适合用栈操作运算：遇到数字则入栈；遇到算符则取出栈顶两个数字进行计算，并将结果压入栈中

解题思路：给定一个合法的逆波兰表达式，每次遇到操作数operands，压入栈；如果遇到操作符operator，则连续出两次栈，第一个出栈的元素记为b，第二个记为a，计算**a** op **b**（注意不是**b** op **a**，例如：13/5的逆波兰表达式["13","5","/"])，将结果压入栈。
