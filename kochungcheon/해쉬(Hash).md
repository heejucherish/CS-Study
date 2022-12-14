# 해쉬(Hash)

----

- ## 정의
  
  키(key)와 값(value)로 이루어진 데이터 구조

- ## 특징
  
  key를 사용하여 데이터를 빠르게 찾을 수 있다

- ## 용어
  
  - 해쉬 함수
    
    키를 해쉬로 변환하는 함수.
  
  - 키(key)
  
  - 해쉬(hash)
  
  - 해쉬테이블(hash table)
  
  - 버킷(bucket)
  
  - 슬롯(slot)
  
  - 기억장소 활용률
    
    해시테이블 전체 기억장소에 데이터가 담겨있는 비율이다. 식별자 밀도(Identifier density), 부하율, 적재 밀도(Load factor, Loading density)라는 단어들과 혼용되서 사용되는 것으로 보인다. 기억장소 활용률은 슬롯이 배열인 경우는 '저장된 데이터수 / (슬롯의 수 * 버킷의 수)', 슬롯이 연결리스트 등 공간이 동적할당되는 경우는 '저장된 데이터 수 / 버킷의 수' 로 계산된다. 
    
      해시 테이블은 기억장소의 활용률에 따라 성능에 차이가 있다. 일반적으로 기억장소 활용률이<mark> 25~75% 일 때 가장 성능이 좋으며</mark>, 해시 테이블에 데이터 입력/삭제가 발생할 때 기억장소 활용률을 계산하여 25~75% <mark>범위를 벗어나면 해시 테이블의 크기를 리사이징</mark> 하기도 한다.

- ## 해쉬 테이블
  
  - 데이터 저장
  
  - 데이터 삭제
  
  - 데이터 검색
  
  - 단점
    
    해쉬 충돌이 일어날 수 있다.,
    
    O(n) 이 걸린다.

                     
