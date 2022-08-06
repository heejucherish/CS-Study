---
# 자료구조 array, linked list

----
---

## 자료구조란?

데이터에 효율적으로 접근하고 조작하기 위한 데이터의 조직,관리, 저장 구조

------

## array

- 데이터들과 데이터들에 대응하는 인덱스로 이루어진 자료구조

- 정적 배열
  
  - 데이터가 순차적으로 저장

- 같은 종류의 데이터들이 저장

## python의 list와 array와 차이점

- python list 는 서로 다른 자료형도 저장할 수 있다.

- python list는 동적 배열, array는 정적 배열
  
  - 동적 배열 : 배열의 크기를 바꿀수 있음 즉 값을 추가, 삭제 할 수 있음
  
  - 정적 배열 : 배열의 크기가 고정 즉 값을 추가 삭제 할 수 없음

  [참고]  (https://seongonion.tistory.com/18)

----

## linked list

- 데이터의 선형 집합

- 데이터 순서가 메모리에 물리적 순서대로 저장 되지 않는 다.
  
  <img src="file:///C:/Users/g2c10/AppData/Roaming/marktext/images/2022-08-07-03-00-04-image.png" title="" alt="" width="104"> 
  
  <그림 출처 파이썬 알고리즘 인터뷰_박상길>

- 개별 값들이 노드를 이룸
  
  - 자신이 가지고 있는 값
  
  - 다음 노드를 가리키는 포인터
  
  - 첫 번째 값을 가지고 있는 노드를 head node라고 함

- 동적 메모리
  
  - 새로운 노드 삽입, 삭제 용이

- 특정 인덱스에 접근 하려면 모든 값을 봐야 함으로 O(n)
  
  - 단, 시작과 끝 인덱스의 경우 삽입,삭제 시 O(n)

- 연결 위해 별도 데이터 공간 이 필요함.

- 리스트 변형
  
  - 원형 연결 리스트: 마지막 노드가 첫 번째 노드를 가리키는 형태
  
  - 이중 연결 리스트: 노드다 이전 값도 가리킴
    
    - 즉, 노드탐색이 양쪽으로 모두 가능
  
  

- 구현
  
  ```python
  #노드 구현
  class Node(self, data):
      self.data = data
      self.next = None
  
  # 링크드 리스트 구현
  class linked_list:
      def __int__(self,data):
          self.head = Node(data)
  
  # 새로운 노드 추가
      def append(self, data):
          cur = self.head
          while cur.next is not None:
              cur = cur.next
          cur.next = Node(data)
  	
  # 노드 값 출력 
      def print_all(self):
          cur = self.head
          while cur is not None:
              print(cur.data)
              cur = cur.next    
  # 인덱스로 값 알아내기
      def get_node(self, index):
          cnt = 0
          node = self.head
          while cnt < index:
              cnt += 1
              node = node.next
          return node
  
  # 값 삽입
      def add_node(self, index, value):
          new_node = Node(value)
          if index == 0:
              new_node.next = self.head
              self.head = new_node
              return
          node = self.get_node(index-1)
          next_node = node.next
          node.next = new_node
          new_node.next = next_node
  ```
  
  ```python
   # 값 삭제
   def delete_node(self, index):
          if index == 0:
              self.head = self.head.next
              return
          node = self.get_node(index-1)
          node.next = node.next.next
  ```
