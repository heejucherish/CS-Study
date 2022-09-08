- [Hash Table](#hash-table)
  * [Resolve Collision Scheme 충돌 처리 기법](#resolve-collision-scheme-충돌-처리-기법)
    + [Open Addressing](#open-addressing)
      - [1. Linear Probing Scheme 선형 검색 기법](#1-linear-probing-scheme-선형-검색-기법)
        * [a. 선형 검색 기법의 최대 단점](#a-선형-검색-기법의-최대-단점)
        * [b. 선형 검색 기법의 태그 필요성](#b-선형-검색-기법의-태그-필요성)
        * [c. 부하율 : 해시 테이블의 부담](#c-부하율--해시-테이블의-부담)
      - [2. Quadratic Probing Scheme 2차 검색기법](#2-quadratic-probing-scheme-2차-검색기법)
        * [a. 2차 검색기법의 빈 칸](#a-2차-검색기법의-빈-칸)
        * [b. 1차 클러스터, 2차 클러스터](#b-1차-클러스터-2차-클러스터)
      - [3. Random Probing Scheme 무작위 검색 기법](#3-random-probing-scheme-무작위-검색-기법)
      - [4. Double Hashing 이중 해싱](4-double-hashing-이중-해싱)
  * [참고자료](#참고자료)

# Hash Table

**해시** 

- 주어진 키를 사용해서 실제 레코드의 주소를 직접적으로 계산해 내는 것
- 원소가 저장될 자리가 원소의 값에 의해 결정되는 자료구조
- 적절한 가정 하에서 평균 $O(1)$ 상수 시간에 탐색, 삽입, 삭제 
  - 데이터 개수 $N$ 과 무관하게 단번에 찾아내겠다는 것 
  - 매우 빠른 응답을 요하는 응용에 유용

**Hash Table 해시 테이블**

hash function 해시 함수 `h` 를 사용하여 키 `k` 를 `T[h(k)]` 에 저장

- `h : U → ({0, 1, ..., TableSize -1})`

  여기서 `U` 는 모든 가능한 키들의 집합

- 키 `k` 가 `h(k)` 로 해싱되었다고 말함.

해시테이블은 일반적으로 하나의 배열

즉 각 키에 대한 해시함수값을 그 키를 저장할 배열 인덱스로 사용

**Collision 충돌**

- Hash table의 한 주소를 놓고 두 개 이상의 원소가 자리를 다투는 것
  - Hashing을 해서 삽입하려 했으나 이미 다른 원소가 자리를 차지하고 있는 상황

- 즉, 서로 다른 두 키 `k_1` 과 `k_2` 에 대해서 `h(k_1)=h(k_2)` 인 상황
- 일반적으로 `|U| >> TableSize` 이므로 항상 발생 가능 (즉 일대일 함수(단사 함수)가 아님)
  - 여기서 $U$ 는 모든 가능한 키들의 집합

- 만약 `|K|>TableSize` 라면 당연히 발생
  - 여기서 `K` 는 실제로 저장된 키들의 집합




## Resolve Collision Scheme 충돌 처리 기법

**Closed Addressing 폐쇄 주소 방식**

- 자기자리가 아니면 절대로 못 들어가게 함
- 버켓, 별도 체인

**Open Addressing 개방 주소 방식**

- 충돌이 일어나면 자기 자리가 아닌 곳으로 들어갈 수 있도록 허용
- 다른 키를 가진 레코드가 해시 되어 들어가야 할 자리까지도 오픈
- 빈자리가 생길 때까지 해시값을 계속 만들어낸다.
  - 충돌이 일어나도 어떻게든 주어진 테이블 공간에서 해결한다.
  - $h_0(x), h_1(x), h_2(x), h_3(x), \ldots $
  - 단점: 모든 원소가 반드시 자신의 해시값과 일치하는 주소에 저장된다는 보장이 없음


- 충돌 시 다음 주소를 결정하는 방법

  1. Linear Probing Scheme 선형 검색 기법

  2. Quadratic Probing Scheme 2차 검색기법

  3. Random Probing Scheme 무작위 검색 기법

  4. Double Hashing 이중해싱

### Open Addressing

#### 1. Linear Probing Scheme 선형 검색 기법

충돌이 일어나면 그 다음 빈 곳

`T[h(KEY)]` 가 점유되어 있을 때, `T[h(KEY) + 1], T[h(KEY) + 2], ...` 의 순서로 빈 곳이 있을 때까지 찾아감.

배열의 끝을 만나면 다시 처음으로 되돌아와서 거기서부터 빈자리를 찾음

`h(key) = h % Prime Number`

##### a. 선형 검색 기법의 최대 단점

선형 검색 기법는 순차탐색으로 empty 원소를 찾아 충돌된 키를 저장하므로 해시테이블의 키들이 빈틈없이 뭉쳐지는 현상이 발생[**Primary Clustering 1차 군집화**]

이러한 군집화는 탐색, 삽입, 삭제 연산 시 군집된 키들을 순차적으로 방문해야 하는 문제점을 야기

군집화는 해시테이블에 empty 원소 수가 적을수록 더 심화되며 해시성능을 극단적으로 저하시킴

##### b. 선형 검색 기법의 태그 필요성

레코드의 삭제로 빈 슬롯이 생겼을 때 군집현상의 끝인지 아니면 하나의 빈 슬롯인지 확인할 수 없는 단점도 있다.

배열 아이템을 세 가지 상태로 분류 

- Occupied 사용 중, Deleted 삭제 됨, Empty 미 사용

탐색 도중 `Empty 미 사용` 칸을 만나면 탐색을 중지하고 찾는 레코드가 없다고 결론 

탐색 도중 `Deleted 삭제 됨` 칸을 만나면 탐색을 계속함. 

##### c. 부하율 : 해시 테이블의 부담

$$
Load Factor\quad 부하율\quad Lambda\quad λ\quad =\quad \frac { 레코드 개수\quad N } { 테이블 크기\quad M }
$$

테이블 크기가 클수록, 또 레코드 수가 적을수록 부하율은 낮아짐

부하율이 커질수록 클러스터가 형성될 확률이 높아짐

**[Knuth 크누스 (1962)](https://jeffe.cs.illinois.edu/teaching/datastructures/2011/notes/knuth-OALP.pdf)**

$$
선형\quad검색 기법의\quad삽입\quad시\quad비교회수는\quad \frac {1} {2} ( 1 + \frac {1} {(1 - λ) ^ 2 )} )\quad 에\quad접근
$$


$$
선형\quad검색 기법의\quad탐색\quad시\quad비교회수는\quad \frac {1} {2} ( 1 + \frac {1} {(1 - λ) )} ) \quad 에\quad접근
$$

따라서 부하율이 1에 가까울수록 비교 회수는 급증

테이블 크기 `M` 을 늘리면 배열의 빈 공간이 많아져 메모리가 낭비

`M` 이 너무 작으면 작은 클러스터끼리 서로 붙어 큰 클러스터가 형성

선형탐사에서 `M ≈ N` 정도로 할 때 대략 Constant Time 상수시간에 삽입과 탐색이 가능

<div class="tg-wrap"><table class="tg">
<thead>
  <tr>
    <th class="tg-l0ih" colspan="2" rowspan="2">효율 비교</th>
    <th class="tg-uzvj" colspan="4">부하율</th>
  </tr>
  <tr>
    <th class="tg-uzvj">50%</th>
    <th class="tg-uzvj">66%</th>
    <th class="tg-uzvj">75%</th>
    <th class="tg-wa1i">90%</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-uzvj" rowspan="2">선형탐사</td>
    <td class="tg-uzvj">탐색</td>
    <td class="tg-9j3s">1.5</td>
    <td class="tg-9j3s">2.0</td>
    <td class="tg-9j3s">3.0</td>
    <td class="tg-zt7h">5.5</td>
  </tr>
  <tr>
    <td class="tg-uzvj">삽입</td>
    <td class="tg-9j3s">2.5</td>
    <td class="tg-9j3s">5.0</td>
    <td class="tg-9j3s">8.5</td>
    <td class="tg-zt7h">55.5</td>
  </tr>
  <tr>
    <td class="tg-wa1i" rowspan="2">이중 해싱</td>
    <td class="tg-wa1i">탐색</td>
    <td class="tg-zt7h">1.4</td>
    <td class="tg-zt7h">1.6</td>
    <td class="tg-zt7h">1.8</td>
    <td class="tg-zt7h">2.6</td>
  </tr>
  <tr>
    <td class="tg-wa1i">삽입</td>
    <td class="tg-zt7h">1.5</td>
    <td class="tg-zt7h">2.0</td>
    <td class="tg-zt7h">3.0</td>
    <td class="tg-zt7h">5.5</td>
  </tr>
</tbody>
</table></div>

#### 2. Quadratic Probing Scheme 2차 검색기법

2차 검색기법은 선형 검색 기법과 근본적으로 동일한 충돌 처리 기법

충돌이 일어날 때 바로 그 뒤에 넣지 않고 조금 간격을 두고 삽입

`T[h(KEY)]` 가 점유되어 있을 때, `T[h(KEY) + 1**2], T[h(KEY) + 2**2], T[h(KEY) + 3**2], ...` 의 순서로 제곱 간격을 두고 빈 곳을 찾아감.

`h(x), h(x)+1, h(x)+4, h(x)+9, ...`

- 선형 검색 기법에서처럼 특정 영역에 원소가 몰려도 그 영역을 빨리 벗어날 수 있기를 기대함.
- 단점: 여러 개의 원소가 같은 초기 해시값을 갖게 되면 모두 같은 순서로 탐사할 수 밖에 없음

##### a. 2차 검색기법의 빈 칸

중간에 빈 칸을 두는 이유는 그 곳으로 해시 되는 레코드들이 들어갈 공간을 비워 둠으로서 오른쪽 끝에 가서 붙는 클러스터를 방지

2차 검색기법은 이웃하는 빈 곳이 채워져 만들어지는 1차 군집화 문제를 해결하지만,

같은 해시값을 같는 서로 다른 키들인 Synonym 동의어들이 똑같은 Jump Sequence 점프 시퀀스를 따라 empty 원소를 찾아 저장하므로 결국 또 다른 형태의 군집화인 **Secondary Clustering 2차 군집화**를 야기

점프 크기가 제곱만큼씩 커지므로 배열에 empty 원소가 있는데도 empty 원소를 건너뛰어 탐색에 실패하는 경우도 피할 수 없음

##### b. 1차 클러스터, 2차 클러스터

인덱스 X 로 해시 될 레코드가 충돌에 의해 Y 로 밀려나면 X, Y가 클러스터를 형성

- 1차 클러스터
  - X, Y 둘 중 하나로 해시 되는 모든 것이 클러스터 되는 것
  
- 2차 클러스터
- X 로 해시 되는 레코드는 다음 빈 곳을 찾기 위해 동일한 곳을 찾아나가기 때문에 그 순서를 따라서 형성되는 클러스터
  
- 1차 클러스터보다는 완화된 모습

#### 3. Random Probing Scheme 무작위 검색 기법

무작위 검색 기법은 선형 탐사와 제곱 탐사의 규칙적인 점프 시퀀스와는 달리 점프 시퀀스를 무작위화하여 empty 원소를 찾는 충돌 처리 기법

무작위 검색 기법은 의사 난수 생성기를 사용하여 다음 위치를 찾음

무작위 검색 기법도 동의어들이 똑같은 점프 시퀀스에 따라 empty 원소를 찾아 키를 저장하게 되고, 이 때문 **Tertiary Clustering 3차 군집화**가 발생

#### 4. Double Hashing 이중 해싱

이중해싱은 서로 다른 두 개의 해시 함수 `h1`, `h2` 를 이용

하나는 기본적인 해시함수 `h(key)` 로 키를 해시테이블의 인덱스로 변환하고, 제2의 함수 `d(key)` 는 충돌 발생 시 다음 위치를 위한 점프 크기를 다음의 규칙에 따라 정함

`(h(key) + j … d (key)) mod M,  j = 0, 1, 2, …`

이중해싱은 동의어들이 저마다 제2 해시함수를 갖기 때문에 점프 시퀀스가 일정하지 않음

따라서 이중해싱은 모든 군집화 문제를 해결

제 2의 함수 `d(key)` 는 점프 크기를 정하는 함수이므로 0을 리턴해선 안됨

- 그 외의 조건으로 `d(key)` 의 값과 해시테이블의 크기 `M` 과 Relatively Prime 서로소 관계일 때 좋은 성능을 보임

- 만약 `d(key)` 와 `M` 이 1보다 큰 최소공배수 를 가진다면?

  – `key` 의 자리를 찾기 위해 해시 테이블 전체 중 기껏해야 `M / 최소공배수` 밖에 보지 못함. 

- 해시 테이블 크기 `M` 을 소수로 잡고, `d(key)` 의 값이 항상 `M` 보다 작은 자연수가 되게 하면, 이들이 항상 서로소가 될 수 있음

## 참고자료

[NAND Flash 메모리 기반 해시 충돌 처리 기법에 관한 연구, 내장형시스템, 대한임베디드공학회논문지](https://koreascience.kr/article/JAKO201708733754217.pdf)

[해시 테이블, 알고리즘, KOCW, 건양대학교 정보통신공학 최진명 교수](http://kocw-n.xcache.kinxcdn.com/data/document/2021/konyang/choijinmyung0121/10-2.pdf)

[해싱의 이해, 알고리즘, KOCW, 부경대학교 컴퓨터공학 권오흠 교수](http://contents2.kocw.or.kr/KOCW/document/2015/pukyong/kwonoeum/5.pdf)

[탐색 알고리즘, 자료구조, 전북대학교 인지컴퓨팅 연구실](https://nlp.jbnu.ac.kr/DS/ch12.pdf)

[해시 테이블, 알고리즘, KOCW, 부산가톨릭대학교 소프트웨어학과 황소영 교수](http://contents2.kocw.or.kr/KOCW/document/2017/cup/hwangsoyoung/9.pdf)

[해시 테이블, 알고리즘, 전북대학교 인지컴퓨팅 연구실](https://nlp.chonbuk.ac.kr/AL/ch06.pdf)

[해시 테이블, 알고리즘기초, 숙명여자대학교 멀티미디어과학과 이종우 교수](http://mm.sookmyung.ac.kr/~bigrain/class/2011/algorithm/ch06.pdf)
