[Blocking and Non-Blocking](#blocking-and-non-blocking)

* [IPC](#ipc)
* [Synchronization for IPC](#--synchronization-for-ipc--)
  + [Synchronous](#synchronous)
  + [Asynchronous](#asynchronous)
* [References](#references)

# Blocking and Non-Blocking

## IPC

[Inter-Process Communication](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EA%B0%84_%ED%86%B5%EC%8B%A0) 프로세스 간 통신. 메시지 전달

## **Synchronization for IPC**

### Synchronous

동기식 통신 - Blocking 송수신

- **동기식 통신이 프로그래머가 사용하기가 더 쉽다.**

- 동작이 상대편 동작에 영향을 받음

  - Blocking send 봉쇄형 보내기 
    - 상대 프로세스의 receive 가 완료될 때까지 send의 완료가 block
    - 송신 프로세스는 수신 프로세스나 메일박스가 메시지를 받을 때까지 block 되어 있음
    - 송신 프로세스는 메시지가 수신 프로세스 또는 메일 박스에 의해 수신될 때까지 봉쇄된다.

  - Blocking receive 봉쇄형 받기
    - receive 할 메시지가 있는 경우에만 receive가 수행되고 완료
    - 수신 프로세스는 수신 메시지가 있을 때까지 block 되어 있음
    - 메시지가 이용 가능할 때까지 수신 프로세스가 봉쇄된다.

### Asynchronous

비동기식 통신 - Non-blocking 송수신

- 동작이 상대편 동작에 영향을 받지 않음

  - Non-blocking send 비봉쇄형 보내기
    - send하고 바로 다음 작업 수행
    - 송신 프로세스는 메시지를 보내고 바로 return. 작업을 계속 수행함 (수신 여부와 관계없이)
    - 송신하는 프로세스가 메시지를 보내고 작업을 재시작한다

  - Non-blocking receive 비봉쇄형 받기
    - 송신 프로세스가 유효한 메시지 또는 널을 받는다. 
    - receive가 호출되면 메시지를 받든지 (받을 메시지가 있으면) null을 수신
    - 수신 프로세스는 유효한 메시지를 받거나 널(null)을 받고 바로 return. 작업을 계속 수행함

[이해가 어렵다면?](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/OS#%EB%8F%99%EA%B8%B0%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0%EC%9D%98-%EC%B0%A8%EC%9D%B4)

## References

[2020 / 프로세스 / 운영체제 / 연세대학교 미래캠퍼스 컴퓨터시스템 연구실 유수연](http://csys.yonsei.ac.kr/lect/os/o3-4.pdf)

[2016 / 프로세스와 쓰레드 / 운영체제 / 부산가톨릭대학교 컴퓨터공학과 변상선 교수](http://vod3.kocw.net/KOCW/document/2016/cup/byunsangseon/6.pdf)

[2011 / 프로세스 개념: Thread / 운영체계 / 충북대학교 컴퓨터교육과 이종연 교수](http://contents.kocw.or.kr/document/lec/2011_2/chungbuk/LeeJongyun_03.pdf)