# Full Binary Tree ( 정 이진 트리 )

  <img title="" src="Full%20Binary%20Tree_assets/2022-08-13-22-37-48-image.png" alt="" width="630"> 

* Full Binary Tree는 leaf 노드 제외한 모든 노드들이 2개의 자식을 가지는 Binary Tree

* 모든 노드가 0개 or 2개의 자식을 가지고 있는 Binary Tree는 Full이다.

* Full Binary Tree Theorems
  
  1. leaf nodes 개수 (하늘색)
     
     * i + 1   [1]
       
       * 증명 참고 [Handshaking Lemma and Interesting Tree Properties - GeeksforGeeks](https://www.geeksforgeeks.org/handshaking-lemma-and-interesting-tree-properties/)
     
     * (n + 1) / 2    [1-4]
  
  2. nodes 총 개수  
     
     * 2i + 1   [1-2] 
     
     * 2l - 1    [1-5]
  
  3. internal nodes 개수 (보라색)
     
     * (n - 1) / 2     [1-3]
     
     * l - 1    [1-2]
  
  4. 최대 nodes 개수
     
     * 2^h - 1     [2]

# Perfect Binary Tree ( 포화 이진 트리 )

<img title="" src="https://t1.daumcdn.net/cfile/tistory/2153514657BBF9B428" alt="자료구조 - 트리란?" width="696">

* 모든 레벨의 노드가 가득 차있는 트리

* 노드가 2개의 자식을 가짐

* nodes 총 개수 = 2^h - 1
