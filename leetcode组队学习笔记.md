# leetcode组队学习笔记

(update 2022/01/11 by Wei)

链表是最基础、最简单的数据结构。**「链表」** 是实现线性表的链式存储结构的基础。它使用一组任意的存储单元（可以是连续的，也可以是不连续的），来存储一组具有相同类型的数据。

链表最大的优点在于可以灵活的添加和删除元素。链表进行访问元素、改变元素操作的时间复杂度为 $O(n)$，进行头部插入、头部删除元素操作的时间复杂度是 $O(1)$，进行尾部插入、尾部删除操作的时间复杂度是 $O(n)$。普通情况下进行插入、删除元素操作的时间复杂度为 $O(n)$。
## Basics about Singly Linked List

### Class ListNode

Define a ListNode class, with defalut value val=0 and next= None.

Notice that no need to pass parameter to self.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

### Class LinkedList

Define a LinkedList class:

```python
class LinkedList:
    def __init__(self):
        self.head=None
```

### Operation

#### Create

```python
def create(self, data):
    self.head=ListNode(0) #val=0, next=None?
    cur = self.head
    for i in range(len(data)):
        node = ListNode(data[i])
        cur.next = node
        cur = cur.next
```

#### Length of LinkedList

```python
def length(self):
    count = 0;
    cur = self.head
    while cur:
        count += 1
        cur = cur.next
    return count
```

#### Find element

```python
def find(self,val):
    cur = self.head
    while cur:
        if val == cur.val:
            return cur
        cur = cur.next
    return None
```

#### Insert

##### InsertFront (Insert on the front)

```python
def insertFront(self,val):
    node = ListNode(val)
    node.next = head
    self.head = node #不要漏掉"self."
```

##### InsertRear (Insert in tail)

```python
def insertRear(self,value):
    cur = self.head
    while cur.next:
        cur = cur.next
    node = ListNode(val)
    cur.next = node
    # node.next = None  #没必要，因为c'tr默认新建的node的next=None！！
```

##### InsertInside (Insert in the middle)

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

#### change

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

#### Remove

##### removeFront

```python
def removeFront(self):
    if self.head: #这一行记得加！！
        self.head = self.head.next
```

##### removeRear

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

##### removeInside

```python
def removeInside(self,index):
    cur = self.head
    count = 0
    if index == 0: #别漏x
        self.head = self.head.next
    while cur and count <index :
        prev = cur
        cur = cur.next
        count += 1
    if not cur:
        return 'Error'
    prev.next = cur.next
```

##  Sorting Singly Linked List

source: https://algo.itcharge.cn/02.%E9%93%BE%E8%A1%A8/02.%E9%93%BE%E8%A1%A8%E6%8E%92%E5%BA%8F/01.%E9%93%BE%E8%A1%A8%E6%8E%92%E5%BA%8F/#31-%E9%93%BE%E8%A1%A8%E9%80%89%E6%8B%A9%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95%E6%8F%8F%E8%BF%B0

### 1. Insertion Sort (插入排序)

two cases when this method will be quick:

1. most elements iSn the array are sorted.
2. num of elements is small

we can work on these two --> Shell Sort 

Pseudocode:

```
Insertion-sort(A)
	for j = 2 to A.length
		key = A[1]
		i = j - 1
		while i > 0 and A[i]> key
			A[i+1] = A[i]
			i = i - 1
		A[i+1] = key
		
```





### 2. Shell Sort (希尔排序)

1. 分组粗调, using gap (步长) lenght/2, length/4, ...,1, respectively
2. in each group, use Insertion Sort
3.  done

 ![Step-by-step visualisation of Shellsort](https://upload.wikimedia.org/wikipedia/commons/d/d8/Sorting_shellsort_anim.gif)

### 3. Bubble Sort (冒泡排序)



### 4. Selection Sort (选择排序)



### 5. Merge Sort (归并排序)

use "Divide and Conquer"



### 6. Quick Sort (快速排序)



### 7. Counting sort (计数排序)



### 8. Bucket sort (桶排序)





### 9. Radix sort (基数排序)

How?

given a array of integers of size n, let m = number of digits in maximal integer, add 0 to the left of other integers to let them have m digits.

possible digits are 0~9 -> Use bucket 0, bucket 1, ... , bucket 9 to hold numbers (i think queue would be better for understanding).

Need m pass (or runs):

first put number into these 10 queues, according to unit digits(个位数), takes these numbers out and put it in an array, from the queue 0 to queue 9.

Now put numbers in queues according to tens digit(十位数), do the same thing as above.

Repeat the remaining m-2 pass and we can get a sorted array.

## Two-Pointer in Linked List

source:

1. https://algo.itcharge.cn/02.%E9%93%BE%E8%A1%A8/03.%E9%93%BE%E8%A1%A8%E5%8F%8C%E6%8C%87%E9%92%88/01.%E9%93%BE%E8%A1%A8%E5%8F%8C%E6%8C%87%E9%92%88%E7%9F%A5%E8%AF%86/#34-%e9%93%be%e8%a1%a8%e7%9a%84%e4%b8%ad%e9%97%b4%e7%bb%93%e7%82%b9
2. https://leetcode.com/explore/learn/card/linked-list/214/two-pointer-technique/1214/

### 1

### 2





## extra notes

### Is a Hashtable a set?

So basically a **set uses a hashtable as its underlying data structure**. This explains the O(1) membership checking, since looking up an item in a hashtable is an O(1) operation, on average.

(from https://stackoverflow.com/questions/3949310/how-is-set-implemented)

## Stack
见另外的文件


## Queue

