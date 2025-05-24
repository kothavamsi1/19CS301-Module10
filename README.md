# 19CS301-Module10
### EX: 10.a  STACK
### Aim:
To Write a python programming to sort the stack using recursion
### Algorithm:
STEP 1: Start.

STEP 2: Define sortStack(stack) to sort recursively by popping all elements.

STEP 3: Recursively call sortStack until the stack is empty.

STEP 4: Use sortedInsert(stack, key) to insert each popped element back in sorted order.

STEP 5: In sortedInsert, if the stack is empty or key > top, push key.

STEP 6 : Else, pop top, recursively insert key, then push top back.

STEP 7: Read input, call sortStack, and print the result.

STEP 8: Stop.

### Program:
```
def sortedInsert(stack, key):
    if not stack or key > stack[-1]:
        stack.append(key)
        return
    top = stack.pop()
    sortedInsert(stack, key)
    stack.append(top)
def sortStack(stack):
    if not stack:
        return
 
    top = stack.pop()
    sortStack(stack)
    sortedInsert(stack, top)

 
A = eval(input())
sortStack(A)
print(list(A))
```
### Output:
 ![image](https://github.com/gokulkrishnan2005/19CS301-Module10/blob/main/module10-1.png)

### Result: Thus, the given program is implemented and executed successfully .
 


### EX: 10.2 IMPLEMENTATION OF STACK
###
Aim: To Write a  python program to add only the even unique numbers using appendleft() from n given numbers.
### Algorithm:

STEP 1: Start.

STEP 2: Import collections and import deque.

STEP 3: Create an empty queue using deque.

STEP 4: Read n numbers from input.

STEP 5 : For each number, check if it is even and not already in the queue.

STEP 6: If valid, insert it at the front using appendleft().

STEP 7 : Print the result. 

STEP 8 : Stop.
### Program: 
```
from collections import deque
class Queue:  
  def __init__(self):  
      self.queue = deque()  
  def add_element(self,val):
      if val%2==0 and val not in self.queue:  
          self.queue.appendleft(val)  
          return True  
      return False  
TheQueue = Queue()  
n=int(input())
for i in range(n):
    TheQueue.add_element(int(input())) 
print(TheQueue.queue)
```
### Output:
![image](https://github.com/user-attachments/assets/f42c4ec6-578c-418a-8f66-cf70abe7dc54)

### Result: Thus, the given program is implemented and executed successfully .
 


EX: 10.3 QUEUE
### Aim: 
To Write a python program to implement the stack using deque method for rotating the stack.
### Algorithm:

STEP 1: Start.

STEP 2: Import collections and import deque.

STEP 3: Create a stack and a variable n.

STEP 4: Get the number of inputs from user.

STEP 5: Using a loop get the inputs from user.

STEP 6: Append the even and unique elements in the stack.

STEP 7: Print the result.
### Program:
```
import collections
stack = collections.deque([])
n = int(input())
for i in range(n):
       x = int(input())
        if x not in stack:
          if x%2==0:
             stack.appendleft(x)
print(stack)
```
### Output:
![image](https://github.com/user-attachments/assets/de6e3e09-b10b-42d4-9faf-32fcf990f29a)
 
### Result: Thus, the given program is implemented and executed successfully .


### EX: 10.4 IMPLEMENTATION OF QUEUE
### Aim:
To Develop a python program to get the 4 integer values from user and display the values using multiprocessing library
### Algorithm:

STEP 1: Start.

STEP 2: From Multiprocessing Import Queue.

STEP 3: Create a list and get the input from user.

STEP 4 : Append the elements in the list.

STEP 5: Using 'get' built-in function print the list.

STEP 6 : Print the result.

STEP 7 : Stop.
### Program:
```
from multiprocessing import Queue
queue = Queue()
for i in range(4):
    queue.put(int(input()))
for i in range(4):
     print(queue.get())
```
### Output:
 ![image](https://github.com/user-attachments/assets/26a380ff-118e-43f4-8178-83a5417262b5)
 

### Result: Thus, the given program is implemented and executed successfully .


 # 19CS301-Module10
### EX: 10.e SEB- Circular Queue
### Aim:
To Write a python program to get string values from the user and display the values using circular queue
### Algorithm

**1 .  Start**

**2 .  Initialize a circular queue**

* Input the maximum capacity `k` (in the given code it is fixed to `5`).
* Create an array `queue` of length `k`, filled with `None`.
* Set both `head` and `tail` indices to `–1` to mark an empty queue.

**3 .  Read the number of elements to insert**

* Read an integer `n`.

**4 .  Repeat steps 5–7 for each of the `n` data items**

#### 5 .  Read `data`

* Read one item from input.

#### 6 .  **Enqueue** `data`

1. **Overflow test**

   * If `(tail + 1) mod k == head`, the queue is full → report *“The circular queue is full”* and skip the insertion.
2. **First insertion (queue empty)**

   * If `head == –1`, set `head = 0`, `tail = 0`, and store `data` at `queue[0]`.
3. **Normal insertion**

   * Otherwise, advance `tail = (tail + 1) mod k` and store `data` at `queue[tail]`.

#### 7 .  Loop back for the next data item

**8 .  **Print** the circular queue**

1. If `head == –1`, output *“No element in the circular queue”* (the queue is empty).
2. If `tail ≥ head`, the valid segment is contiguous:

   * Print elements from `queue[head]` to `queue[tail]`.
3. Otherwise the queue is wrapped:

   * Print elements from `queue[head]` to `queue[k – 1]`, then from `queue[0]` to `queue[tail]`.

**9 .  End**

This algorithm covers initialization, safe insertion with overflow detection, and traversal-based printing for a fixed-size circular queue.


### Program:
```

class MyCircularQueue():
    def __init__(self, k):
        self.k = k
        self.queue = [None] * k
        self.head = self.tail = -1
    def enqueue(self, data):
        if ((self.tail + 1) % self.k == self.head):
            print("The circular queue is full\n")
        elif (self.head == -1):
            self.head = 0
            self.tail = 0
            self.queue[self.tail] = data
        else:
            self.tail = (self.tail + 1) % self.k
            self.queue[self.tail] = data
    def printCQueue(self):
        if(self.head == -1):
            print("No element in the circular queue")
        elif (self.tail >= self.head):
            for i in range(self.head, self.tail + 1):
                print(self.queue[i], end=" ")
            print()
        else:
            for i in range(self.head, self.k):
                print(self.queue[i], end=" ")
            for i in range(0, self.tail + 1):
                print(self.queue[i], end=" ")
            print()
obj = MyCircularQueue(5)
n=int(input())
for i in range(n):
    obj.enqueue(input())
obj.printCQueue()
```
### Output:
 ![image](https://github.com/gokulkrishnan2005/19CS301-Module10/blob/main/10th.png)

### Result: Thus, the given program is implemented and executed successfully .
 

