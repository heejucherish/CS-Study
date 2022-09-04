# Graph 기본 용어

## Graph

* `노드(vertex) 집합` V 과 `엣지(edge) 집합` E 로 구성된 자료구조
* 노드 : 데이터
* 엣지 : 노드와 노드 사이의 정보

![](https://i.imgur.com/SYsNnEB.png)



## sparse / dense graph

* sparse graph : 노드 수 > 엣지  수 그래프
  
  * 연결 되지 않은 노드 발생

* dense graph : 노드 수 < 엣지 수 그래프 
  
  * 노드가 입체적으로 연결

![](https://i.imgur.com/Hke3iQl.png)



## incident / adjacent

* incident : 두 노드가 하나의 엣지로 연결 => 두 노드는 서로 `인접`해있다.

* adjacent : 두 노드가 하나의 엣지로 연결 => 엣지는 두 노드에 `부속`한다.



## degree

* 노드에 연결된 엣지의 수



## loop / isolated

* loop : 하나의 엣지가 같은 노드에 부속된 상황

* isolated : 노드에 부속된 엣지가 없는 상황



## subgraph

* 노드는 같고 일부 엣지만 포함된 부분 그래프 

![](https://i.imgur.com/ItSKR4t.png)



## complete graph / multigraph

* complete graph : 모든 노드들이 엣지로 연결된 그래프

* multigraph : 엣지가 하나 이상인 그래프

![](https://i.imgur.com/4Wrz9qX.png)



## directed graph

* 엣지가 방향성을 가지는 그래프

* degree = incoming degree + outgoing degree

![](https://i.imgur.com/9uLuafn.png)



## path

* 인접한 노드들로 구성된 시퀀스
  
  * 엣지가 겹치지 않는 경로 => simple
  
  * 노드가 겹치지 않는 경로 => elementary

* 경로의 길이 : 경로 내 존재하는 엣지

![DdTKBkL.png](C:\Users\dbwls\Desktop\DdTKBkL.png)

* [v1, v2, v3, v4, v5, v3, v4, v5] 
  
  * path

* [v1, v2, ,v3, v4, v5, v8, v6, v4, v7]
  
  * path 
  
  * simple



## cycle

* 시작 노드와 종료 노드가 같은 경로

* [v1, v2, v3, v4, v5, v9, v1]
  
  * path
  
  * cycle
  
  * simple
  
  * elementary



## connected

* 두 노드 사이에 경로가 존재한다는 것

* 방향 그래프에서 a => b, b => a 경로가 존재하면 `strongly connected`



## edge complement

* 노드는 서로 같고 엣지 존재 양상이 정반대인 그래프

![](https://i.imgur.com/0Dl03ux.png)



## releative complement

* 부그래프에서 엣지를 제거한 그래프

![](https://i.imgur.com/0mkyi2a.png)



## graph representation

| 인접 행렬                                                                   | 인접 리스트                                                                  |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| <img title="" src="https://i.imgur.com/A1qMCWH.png" alt="" width="304"> | <img src="https://i.imgur.com/VRoE2Rv.png" title="" alt="" width="294"> |