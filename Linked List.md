# Linked List notes

(update 2022/01/11 by Wei)

链表是最基础、最简单的数据结构。**「链表」** 是实现线性表的链式存储结构的基础。它使用一组任意的存储单元（可以是连续的，也可以是不连续的），来存储一组具有相同类型的数据。

链表最大的优点在于可以灵活的添加和删除元素。链表进行访问元素、改变元素操作的时间复杂度为 $O(n)$，进行头部插入、头部删除元素操作的时间复杂度是 $O(1)$，进行尾部插入、尾部删除操作的时间复杂度是 $O(n)$。普通情况下进行插入、删除元素操作的时间复杂度为 $O(n)$。

## Class ListNode

Define a ListNode class, with defalut value val=0 and next= None.

Notice that no need to pass parameter to self.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

## Class LinkedList

Define a LinkedList class:

```python
class LinkedList:
    def __init__(self):
        self.head=None
```

## Operation

### Create

```python
def create(self, data):
    self.head=ListNode(0) #val=0, next=None?
    cur = self.head
    for i in range(len(data)):
        node = ListNode(data[i])
        cur.next = node
        cur = cur.next
```

### Length of LinkedList

```python
def length(self):
    count = 0;
    cur = self.head
    while cur:
        count += 1
        cur = cur.next
    return count
```

### Find element

```python
def find(self,val):
    cur = self.head
    while cur:
        if val == cur.val:
            return cur
        cur = cur.next
    return None
```

### Insert

#### InsertFront (Insert on the front)

```python
def insertFront(self,val):
    node = ListNode(val)
    node.next = head
    self.head = node #不要漏掉"self."
```

#### InsertRear (Insert in tail)

```python
def insertRear(self,value):
    cur = self.head
    while cur.next:
        cur = cur.next
    node = ListNode(val)
    cur.next = node
    # node.next = None  #没必要，因为c'tr默认新建的node的next=None！！
```

#### InsertInside (Insert in the middle)

```python
def insertInside(self,index,val):
    cur = self.head
    count = 0
    #原先这么写，写差很多细节！！
    #     while count < index-1:
    #         cur = cur.next
    #         count = count +1
    while cur and count < index-1:
        cur = cur.next
        count = count +1
    if not cur:
        return 'Error'

    node = ListNode(val)
    node.next = cur.next
    cur.next = node
```

### change

```python
def change(self,index,val):
    cur = self.head
    count = 0
    while cur and count < index:
        cur = cur.next
        count = count + 1
    if not cur:
        return 'Error'

    cur.val = val
```

### Remove

#### removeFront

```python
def removeFront(self):
    if self.head: #这一行记得加！！
        self.head = self.head.next
```

#### removeRear

```python
def removeRear(self):
    cur = self.head
    if not cur.next: #不要写为 if cur.next == None:
        self.head = None
    # if not self.head.next:
    #     return 'Error'

    while cur.next:
        prev = cur
        cur = cur.next

    prev.next = None

    # 别人的removeRear
    # def removeRear(self):
    #     if not self.head.next:
    #         return 'Error'
    #
    #     cur = self.head
    #     while cur.next.next:
    #         cur = cur.next
    #     cur.next = None
```

#### removeInside

```python
def removeInside(self,index):
    cur = self.head
    count = 0
    while cur and count <index :
        prev = cur
        cur = cur.next
        count += 1
    if not cur:
        return 'Error'
    prev.next = cur.next
```

