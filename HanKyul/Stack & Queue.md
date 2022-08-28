# Stack & Queue

----

## Stack

### stack의 정의

* #### 사전적 의미
  
  쌓다[포개다]; 쌓이다, 포개지다

* #### 컴퓨터 과학에서의 [의미](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))
  
  **"컴퓨터 과학에서 stack은 요소(데이터)를 다루며, Push & Pop이라는 두 가지의 동작을 수행하는 추상적 데이터 구조입니다."**

* #### 그럼 Push & Pop이 뭔가요?
  
  * 다른 말로는 **LIFO (Last In First Out)**, 후입선출 이라고도 합니다.
  
  * 잘 이해가 안되면 프링글스를 떠올립시다
  
  * <img src="./IMG_STACK_QUEUE/pringles6_434.jpg" title="" alt="pringles" width="276">
    
    * 프링글스는 생산될 때 가장 마지막에 넣어진 조각을
    
    * 구매자가 제일 먼저 먹게 됩니다.
  
  * #### **즉 데이터의 입-출력이 한 방향에서만 이루어지는 특성이 있습니다.**

* #### Peek
  
  * 추가적으로 peek라는 동작도 있습니다
    
    * stack의 맨 위에 뭐가 있는지 보는...

* #### 구현
  
  * 먼저 그림을 보면서..
    
    * <img src="./IMG_STACK_QUEUE/stack_push_operation.jpg" title="" alt="push" width="276">
    * <img src="https://www.edureka.co/blog/wp-content/uploads/2019/08/pop-up-300x200.png" title="" alt="Stack in Python | What is Python Stack and how to Implement it | Edureka" width="399">
  
  * 배열을 활용한 구현   
    
    * ```python
        # Stack Size는 10
        # 1 이상의 데이터만 들어온다고 간주
        MAX_SIZE = 10
        stack = [0] * 10
        top = -1
      
        # Data를 밀어넣는 함수
        def push(data):
            if not isFull():
                stack[top] = data
                top += 1
      
        # Data를 peek, 즉 열람할 수 있는 함수
        def peek():
            if stack is not isEmpty():
                return stack[top]
            else:
                return -1
      
        # 데이터를 꺼내는 함수
        def pop():
            item = -1
            if stack is not isEmpty():
                item = stack[top]
                top -= 1
      
            return item
      
        # 비었는지 확인
        def isEmpty():
            if top == -1:
                return True
            else:
                return False
      
        # 꽉 찼는지 확인
        def isFull():
            if top == MAX_SIZE - 1:
                return True
            else:
                return False
      ```
  
  * 파이썬이 지원하는 API를 활용한 구현
    
    * DFS 구현시 사용되니 알아둡시다!
    
    * ```python
      stack = list()
      
      # push** 
      # 배열의 끝에 데이터를 자동으로 집어넣음
      stack.append(data)
      # peek
      stack[-1]
      # pop
      # 자동적으로 마지막 데이터를 pop 후 delete함.
      stack.pop()
      ```
  
  * java의 라이브러리
    
    * ```java
      import java.util.Stack; //import
      Stack<Integer> stack = new Stack<>();
      stack.push(1);
      stack.peek(); 
      stack.pop();
      stack.clear();
      ```

* #### 주의할 점
  
  * 자료구조의 Stack != 메모리의 Stack
    
    * 위에서 설명한 자료구조 Stack
    
    * (컴퓨터 구조에서 다룰) 메모리에서의 Stack
      
      * A stack is a special area of computer’s memory which stores temporary variables created by a function. In stack, variables are declared, stored and initialized during runtime.
      
      * ![memory management - Stack and Heap locations in RAM - Stack Overflow](https://i.stack.imgur.com/HOY4C.png)

## Queue

* #### 사전적 의미
  
  * (서는)줄

* #### 컴퓨터 과학에서의 [의미](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))
  
  * **"Queue는 한 쪽 끝에서 데이터를 추가하고, 다른 끝에서 데이터를 제거하는 동작으로 관리되는 데이터의 모음을 말합니다."**

* #### 이게 무슨 뜻인가요?
  
  * <img src="./IMG_STACK_QUEUE/2506923E561B006C01.jpg" title="" alt="T-Express" width="368">
    
    * T-익스프레스를 타기 위한 줄
  
  * FIFO (First In First Out)
    
    * 먼저 온 데이터가 먼저 나간다
    
    * 우리가 평소 생각하는 "줄서기"의 개념이다
    
    * #### **즉 데이터가 한쪽 방향에서는 들어가기만 하고, 다른 한 쪽 방향에서는 나가기만 하는 특성을 가집니다**

* #### 구현
  
  * 역시 먼저 그림을 보면서....
    
    * <img src=".\IMG_STACK_QUEUE\queue_enqueue_diagram.jpg" title="" alt="Enque" width="368">
    
    * <img src=".\IMG_STACK_QUEUE\queue_dequeue_diagram.jpg" title="" alt="Deque" width="368">
  
  * 배열을 활용한 구현
    
    * ```python
      MAX_SIZE = 10
      queue = [0] * 10
      front = 0
      rear = 0
      # Data를 peek, 즉 열람할 수 있는 함수
      def peek():
          if queue is not isEmpty():
              return queue[front]
          else:
              return -1
      
        # Data를 밀어넣는 함수
      
      def enqueue(data):
          if not isFull():
              rear += 1
              stack[rear] = data
              
      
        # 데이터를 꺼내는 함수
      def dequeue():
          item = -1
          if queue is not isEmpty():
              item = queue[front]
              front += 1
          return item
        # 비었는지 확인
      
      def isEmpty():
          if front < 0 or front > rear:
              return True
          else:
              return False
        # 꽉 찼는지 확인
      
      def isFull():
          if rear == MAX_SIZE - 1:
              return True
          else:
              return False
      ```
  
  * 파이썬 API를 활용한 구현
    
    * 나중에 BFS를 구현할 때 쓰이니 기억해두세요!
    
    * ```python
      queue = list()
      # enqueue
      # 배열의 끝에 데이터를 자동으로 집어넣음
      queue.append(data)
      # peek
      queue[0]
      # dequeue
      # 맨 앞 데이터를 빼낸 후 delete함
      queue.pop(0)
      ```
  
  * Java API를 활용한 구현
    
    * ```java
      import java.util.LinkedList; //import
      import java.util.Queue; //import
      Queue<Integer> queue = new LinkedList<>(); //int형 queue 선언, linkedlist 이용
      queue.add(1);     // queue에 값 1 추가
      queue.add(2);     // queue에 값 2 추가
      queue.remove();     // queue에 첫번째 값 제거
      queue.clear();      // queue 초기화
      queue.peek();       // queue의 첫번째 값 참조
      ```
