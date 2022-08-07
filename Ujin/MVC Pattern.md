# MVC Pattern

## Model + View + Controller로 이루어진 디자인 패턴

![](MVC%20Pattern_assets/2022-08-07-00-48-09-mvc.png)

* 애플리케이션의 구성 요소를 세 가지 역할로 구분

* 사용자 인터페이스로부터 비즈니스 로직을 분리



## Model

* 데이터를 가진 객체

* View에서 데이터를 생성, 수정 => Controller를 통해 모델을 생성 , 업데이트

* 모델의 규칙
  
  * 1. 사용자가 편집하길 원하는 모든 데이터를 가지고 있어야 한다.
    
    2. 뷰나 컨트롤러에 대해 어떤 정보도 알면 안된다.
    
    3. 변경이 일어나면, 변경 통지에 대한 처리 방법을 구현해야 한다.



## View

* 사용자 인터페이스 요소 (inputbox, checkbox 등)

* 모델을 기반으로 사용자가 볼 수 있는 화면

* 뷰의 규칙
  
  * 1. 모델이 가지고 있는 정보를 따로 저장해서는 안된다.
    
    2. 모델이나 컨트롤러와 같이 다른 구성요소들을 몰라야 한다.
    
    3. 변경이 일어나면 변경통지에 대한 처리 방법을 구현해야 한다.



## Controller

* 하나 이상의 모델과 뷰를 잇는 다리 역할

* 메인 로직 담당 / 모델, 뷰의 생명주기 관리

* 컨트롤러의 규칙
  
  * 1. 모델이나 뷰에 대해서 알고 있어야 한다.
    
    2. 모델이나 뷰의 변경을 모니터링 해야 한다.





# MVC Pattern 방식

## Model 1

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR-c9ZZPvVDLEcpn-YFZrqndD5x3S07A97FYQ&usqp=CAU" title="" alt="모델-뷰-컨트롤러 패턴 - 해시넷" width="716">

* JSP에서 출력과 로직을 전부 처리

* Controller 영역에 View 영역을 같이 구현하는 방식

* 장점 : 빠르고 쉽게 개발 가능

* 단점 : JSP파일이 너무 비대해지고 유지보수 어려움



## Model 2

<img title="" src="https://user-images.githubusercontent.com/67519366/100101189-43636100-2ea5-11eb-8bfd-1a63e145f22c.PNG" alt="MVC Model1과 MVC Model2" width="693">

* JSP에서 출력만 처리

* 사용자의 요청을 Servlet이 받고 Servlet은 View로 보여줄 건지, Model로 보낼 건지 판단&전송

* HTML, JAVA소스 분리 => 상대적으로 확장, 유지보수 쉬움

* 장점 : 디자이너와 개발자의 분업이 가능하며 유지보수 및 확장이 쉬움

* 단점 : 설계 어려움, 개발 난이도 높음





# MVC Pattern의 필요성

* 비즈니스 로직과 UI 로직 분리 => 독립적인 유지보수 가능

* Model, View가 다른 컴포넌트들에 종속되지 않음 => 확장성, 유연성에 유리



# MVC Pattern의 한계

* Controller에 다수의 Model과 View가 복잡하게 연결되어 있는 상황이 발생할 수 도 있다.







JSP, Servlet [[JSP] JSP (JavaServer Pages ) 란 무엇인가?](https://javacpro.tistory.com/43)
