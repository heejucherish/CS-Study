# 우선순위 큐 (Priority Queue)
* 가장 우선순위가 높은 데이터부터 삭제
* 배열, 연결리스트, 힙으로 구현 가능 => 힙이 가장 효율적

# Binary Heap

* 완전 이진 트리의 일종, 우선순위 큐를 위해 만들어진 자료구조
* 최댓값 or 최솟값 찾는 연산을 빠르게 하기 위해 고안된 자료구조 => 반정렬 상태
* 부모노드의 키값과 자식노드의 키값 사이 대소관계 성립
* 왼쪽 자식 인덱스 = 부모 인덱스 * 2
* 오른쪽 자식 인덱스 = 부모 인덱스 * 2 + 1
* 부모 인덱스 = 자식 인덱스 // 2



## 최소 힙 & 최대 힙

| 최소 힙 (Min heap)                                                                                                       | 최대 힙 (Max heap)                                                                                                       |
|:---------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------:|
| key(parent) <= key(child)                                                                                             | key(parent) >= key(child)                                                                                             |
| root node = 가장 작은 값                                                                                                   | root node = 가장 큰 값                                                                                                    |
| <img src="https://blog.kakaocdn.net/dn/Lulip/btq66t3mygU/XhwpPwIBf7gl580EV5cLa0/img.png" title="" alt="" width="273"> | <img src="https://blog.kakaocdn.net/dn/yXt2a/btq7ddSvksp/abjtbzX0kb5mbKWHgS84d1/img.png" title="" alt="" width="290"> |



## Heapify

* 이진트리에서 힙 속성을 유지하는 작업

![](https://blog.kakaocdn.net/dn/Y4nXi/btq7bht5z6Q/mXCNuinbNgPwx9Y399Slo0/img.png)

* max heap 에서 heapify example

```python
def max_heapify(arr, i):
    left = 2 * i            # 노드 i의 왼쪽 자식 인덱스
    right = 2 * i + 1       # 노드 i의 오른쪽 자식 인덱스
    
    if arr[left] > arr[rigt]:       # 자식 노드 중 max값
        max_child = left
    else:
        max_child = right

    if arr[i] < arr[max_child]:      # 자식 max보다 작으면 체인지
        arr[max_child], arr[i] = arr[i], arr[max_child]
    return arr

arr = [0, 8, 15, 20, 5, 7, 13, 4]

for i in range(1, len(arr)//2):
    max_heapify(arr, i)
print(*arr[1:])

```

```python
def min_heapify(arr, i):
    left = 2 * i            # 노드 i의 왼쪽 자식 인덱스
    right = 2 * i + 1       # 노드 i의 오른쪽 자식 인덱스
    
    if arr[left] < arr[right]:       # 자식 노드 중 min값
        min_child = left
    else:
        min_child = right

    if arr[i] > arr[min_child]:      # 자식 min보다 크면 체인지
        arr[min_child], arr[i] = arr[i], arr[min_child]
    return arr

arr = [0, 8, 15, 20, 5, 7, 13, 4]

for i in range(len(arr)//2-1, 0, -1):
    min_heapify(arr, i)
print(*arr[1:])
```

* 모듈 사용

```python
import heapq    # 기본적으로 min-priority-queue

arr = [0, 8, 15, 20, 5, 7, 13, 4]
heapq.heapify(arr)    # heapify
print(arr)

heapq.heappush(arr, 1)   # heap 요소 추가 'heappush'
heapq.heappop(arr)       # heap 요소 삭제 'heappop'
```


## Extract

* heap의 최대 요소를 추출하는 작업

![](https://blog.kakaocdn.net/dn/biLr9R/btq7bgWfv1J/eqB3zOK1DgZJZgimrXkr01/img.png)

* max heap 에서 extract example

```python
def max_extract(arr):
    global root
    root = arr[1]           # max heap 에서 최대값은 루트에 있음
    arr[1] = arr[len(arr)-1]   # 루트자리에 마지막 값 삽입
    arr.pop()                  # 마지막 값 삭제
    return arr

arr = [0, 20, 15, 17, 5, 7, 13]
arr = max_extract(arr)

for i in range(1, len(arr)//2):
    max_heapify(arr, i)
print(root, arr[1:])
```

* 내장 함수 사용
```python
import heapq   

arr = [0, 8, 15, 20, 5, 7, 13, 4]
heaparr = []
for i in arr:
    heapq.heappush(heaparr, -i)   # heapq가 기본적으로 min-priority-queue라서 => -20, -15, -13, -4, -5, -7, -8, 0

for i in range(len(arr)):
    print(-heapq.heappop(heaparr), end=' ')  # maxheap 용도로 사용 가능
```
