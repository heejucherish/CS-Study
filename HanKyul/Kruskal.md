# Kruskal 알고리즘

## Union-Find

#### 무엇인가?

* 집합을 효율적으로 표현하기 위해 만들어진 알고리즘이다.

* Union-Find 알고리즘에서의 집합의 모습
  
  ![desc](.\IMG_KRUSKAL\union-find-union3.png)
  
  #### 코드를 보기 전에 그림으로 살펴봅시다
  
  1. 초기 상태 (자기 자신을 멤버로 하는 집합)
  
  ![desc](.\IMG_KRUSKAL\039a333.jpg)
  
  ![desc](.\IMG_KRUSKAL\1539ad6.jpg)
  
  #### P배열 == Arr입니다
  
  #### P 배열은 각 원소가 어떤 집합인지, 즉 각 원소의 부모가 누구인지에 대한 정보를 가지고 있습니다.
  
  2. Union(2,1)
  
  ![desc](.\IMG_KRUSKAL\28e2d55.jpg)
  
  ![desc](.\IMG_KRUSKAL\32f6a91.jpg)
  
  3. Union(4,3) -> Union(8,4) -> Union(9,3)
  
  ![desc](.\IMG_KRUSKAL\4c11a99.jpg)
  
  ![desc](.\IMG_KRUSKAL\6a7bc9a.jpg)
  
  4. Union(6,5)
  
  ![desc](.\IMG_KRUSKAL\66d9b5d.jpg)
  
  ![desc](.\IMG_KRUSKAL\7439d01.jpg)
  
  #### 코드와 함께 살펴봅시다
  
  ```python
  n = 6
  
  p = [0] * n # 부모 리스트
  r = [0] * n # rank 리스트
  
  def makeSet():
      for i in range(0,n):
          p[i] = i # 맨 처음엔 union되지 않았으므로. 자기 자신을 부모로 하는 집합을 생성합니다.
          r[i] = 1 
  
  def union(x,y):
      x = find(x) 
      y = find(y) # union을 하려면 각 원소의 부모를 알아야 합니다.
  
      if x == y: # 두 원소의 부모가 같다는 뜻은, 같은 집합이란 뜻입니다.
          return False # 그러므로 union 불가입니다.
  
      if r[x] < r[y]: # 만약 y원소의 가중치가가 더 높다면
          r[y] += r[x] # y원소가 부모일 확률이 높게 만들어야 하므로 y 가중치 +
          p[x] = y # y원소에 x를 붙일거임
      else:
          r[x] += r[y]
          p[y] = x
      return True
  
  def find(x):
      if x == p[x]: # 제일 윗 부모를 찾았다면 (자기 자신을 가리키고 있다면)
          return x # 그 값 return
      else:
          #주의! find의 인자로 x를 넘기게 되면, 계속 같은 과정을 반복합니다. 잘 외우세요.
          p[x] = find(p[x]) # 부모를 찾지 못했다면,  
          return p[x] # 부모를 찾아 return
  
  makeSet()
  
  union(0, 1)
  print('union 0,1')
  print('p1 ', p)
  print('r1 ', r)
  print()
  
  union(1, 2)
  print('union 1,2')
  print('p2 ', p)
  print('r2 ', r)
  print()
  
  union(3,2)
  print('union 3,2')
  print('p3 ',p)
  print('r3 ',r)
```
  
1. ### MakeSet();
  
  ```python
  ddef makeSet():
      for i in range(0,n):
          p[i] = i # 맨 처음엔 union되지 않았으므로. 자기 자신을 부모로 하는 집합을 생성합니다.
          r[i] = 1 
  ```
2. ### find(int x)

재귀적 구현

![desc](.\IMG_KRUSKAL\집합ㅈ.JPG)

8의 부모를 찾아가려면...

- 만약 4-8의 집합이 있었고, 3-4를 union 했다면

- 실제 집합은 3-4-8이지만

- 8은 4를 부모로 가지고 있음

- 8의 진짜 부모를 찾아가려면 4를 통해 찾아가야 함.

```python
def find(x):
    if x == p[x]: # 제일 윗 부모를 찾았다면 (자기 자신을 가리키고 있다면)
        return x # 그 값 return
    else:
        #주의! find의 인자로 x를 넘기게 되면, 계속 같은 과정을 반복합니다. 잘 외우세요.
        p[x] = find(p[x]) # find하면서 만난 모든 값의 부모 노드를 root로..
        # 재귀로 부모값을 갱신시켜줌 : Path Compression
        return p[x] # 부모를 찾아 return
```

3. ### union(a,b)
   
   a. a,b의 부모를 찾음
   
   b. a의 부모 == b의 부모 -> 같은 집합이므로 이미 union되어있음. union 불가능!
   
   c. 아니라면 union

```python
def union(x,y):
    x = find(x) 
    y = find(y) # union을 하려면 각 원소의 부모를 알아야 합니다.

    if x == y: # 두 원소의 부모가 같다는 뜻은, 같은 집합이란 뜻입니다.
        return False # 그러므로 union 불가입니다.

    if r[x] < r[y]: # 만약 y원소의 가중치가가 더 높다면
        r[y] += r[x] # y원소가 부모일 확률이 높게 만들어야 하므로 y 가중치 +
        p[x] = y # y원소에 x를 붙일거임
    else:
        r[x] += r[y]
        p[y] = x
    return True
```

### 근데... r배열은 뭐죠?

![desc](./IMG_KRUSKAL/weighted-quick-union-overview.png)

Tree의 크기를 관리하기 위함입니다.

무조건 왼쪽 원소를 오른쪽으로 붙이게 했다고 쳐 봅시다

```python
def union(x,y):
    x = find(x) 
    y = find(y) # union을 하려면 각 원소의 부모를 알아야 합니다.

    if x == y: # 두 원소의 부모가 같다는 뜻은, 같은 집합이란 뜻입니다.
        return False # 그러므로 union 불가입니다.

    p[y] = x # 랭크 관리 하지않고.... 그냥 오른쪽
    return True
```

![enter image description here](.\IMG_KRUSKAL\a1f5858.jpg)

* 오른쪽 트리가 더 크기 때문에
  
  * 왼쪽 트리를 오른쪽에 붙임

* 반대로 붙었을 경우
  
  * 부모 갱신을 더 많이 해 줘야함
  
  * 자식들의 부모를 다 바꿔줘야 하니까

![performance of union-find algorithms](.\IMG_KRUSKAL\uf-performance.png)

속도 면에서도 훨씬 유리하기 때문에, Path Compression과 Weighted Quick Union은 꼭 외우도록 합시다.

## Kruskal

### MST (Minimal Spanning Tree), 최소 신장 트리

### 1. spanning Tree(신장 트리)란?
   
   ![](.\IMG_KRUSKAL\spanning-tree.png)

연결 그래프에서 순환 요소를 삭제하고, 

모든 정점을 방문할 수 있는 

트리 모양으로 만든 것을 신장 트리라 한다.

### 2. Minimal Spanning Tree(최소 신장 트리)란?
   
   가중치 그래프에서 **최소 가중치**값을 가지도록 만든 신장 트리이다.
   
   ![](.\IMG_KRUSKAL\MST_before.png)
   
   가중치 그래프
   
   ![](.\IMG_KRUSKAL\MST_after.png)

위의 가중치 그래프로 만든 Minimal Spanning Tree

### 위의 그래프에서 최소 신장 트리를 어떻게 만들 수 있을까요?



1. 최소 가중치 순서대로 간선을 정리하고, 간선을 하나씩 골라봄

2. 만약 그 간선이 연결됨으로써 Cycle이 발생하는지 여부를 체크한다
   
   * 즉 Union-Find를 통해, 같은 집합인지 확인하면 된다

![](.\IMG_KRUSKAL\가중치정리.JPG)

* 가중치를 무게순으로 정리한다

![](.\IMG_KRUSKAL\크루스칼완료.JPG)

* 사이클을 이루지 않는 조건으로, 하나씩 간선을 고른다
  
  * 이 점이 그리디 알고리즘이라 할 수 있음
  
  * 모든 간선을 골라보지 않고
  
  * 가중치 적은 순으로 간선을 고르는 것이 최적의 해임이 증명되었기 때문

* E = V-1일 때 종료한다.



Kruskal 알고리즘 일부 (위의 Union-Find와 함께 쓰세요)

```python
V = [1,2,3,4,5,6,7,8,9]
E = [(9,4,5), (7,2,6), (8,3,6), (5,3,4), (4,1,5), (3,2,4), (3,2,3), (2,1,2), (1,1,4)] # Weight Start End
n = len(V)

p = [0] * n # 부모 리스트
r = [0] * n # rank 리스트

makeSet()
E.sort() # 가중치 순서대로 정렬

result = []
minimum = 0
edgecount = 0
for edge in E: # 모든 간선을 돌면서..
    w = edge[0] # 간선의 가중치
    s = edge[1] # 간선의 시작점
    e = edge[2] # 간선의 끝점
    if union(s, e): # union 할 수 있다면
        result.append((w,s,e)) # 해당 간선 선택
        minimum += w
        edgecount += 1
    if edgecount == len(V) - 1: # 고른 간선이 V-1 개라면
        break # 종료

print(result)
print(minimum)
```

### Kruskal 알고리즘의 속도

* Weighted Union-Find with Path Compression : Amortized 1

* Edge들을 가중치 순으로 정렬하려면
  
  * 효율적인 배열 정렬 알고리즘은 n log n
    
    * 즉, 가중치와 정점 으로 이루어진 배열 정렬 알고리즘에 영향을 받음
  
  * 따라서 1 x e log e 정도의 효율을 가짐
    
    * 그렇기 때문에, 적은 수의 간선을 가지는 희소 그래프(Sparse Graph)의 경우 적합
    
    * 간선 수가 많다면 Prim 알고리즘 선택이 유리
