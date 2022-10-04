[Computer_Architecture](#computer_architecture)

* [basic configuration](#basic-configuration)

* [Software](#software)

* [Hardware](#hardware)

  1. [Bus](#1-bus)

  2. [Processor](#2-processor)

  3. [Main Memory](#3-main-memory)

  4. [auxiliary storage device](#4-auxiliary-storage-device)

  5. [Graphic Processing Unit](#5-graphic-processing-unit)
  6. [Input Device](#6-input-device)
  7. [Output Device](#7-output-device)

# Computer_Architecture

## basic configuration

기본 기능: 프로그램 코드(명령어)를 정해진 순서대로 실행하는 것

컴퓨터 시스템은 기본적으로 소프트웨어와 하드웨어로 구분됨 

## Software

활용할 수 있는 기본적인 프로그램이나 이에 따르는 기술들

정보들이 이동하는 방향과 정보 처리의 종류를 지정

하드웨어를 제어하여 작업을 수행하는 프로그램

동작들이 일어나는 command들의 집합

사람이 이해하기 쉬운 고급 언어로 작성

- application software 응용 소프트웨어
  - 워드프로세서, 웹 브라우저, MS Excel 등

- system software 시스템 소프트웨어

  - 사용자가 컴퓨터와 대화할 수 있는 user interface를 제공함 

  - OS 운영체제는 컴퓨터의 전체적인 작동을 관리하는 프로그램 
    - 사용자가 컴퓨터 시스템을 편리하고 효율적으로 사용할 수 있는 방법을 제공 
    - Windows, Unix, Linux 등
  - 언어 번역 프로그램은 프로그래밍 언어로 작성된 프로그램을 컴퓨터가 이해할 수 있는 기계어로 번역하는 프로그램 
    - 고급 언어를 번역하는 프로그램을 Compiler라고 부름 
    - 어셈블리 프로그램을 번역하는 프로그램을 Assembler라고 함 

  - 유틸리티 프로그램은 컴퓨터의 조작을 편리하게 해주는 프로그램 
    - 기억 장치에 저장되어 사용자가 필요로 할 때 호출하여 사용함
    - 대부분의 유틸리티 프로그램은 컴퓨터 제작 회사에서 제공하고 있음

**Device Driver 장치 구동기** 

- 하드웨어와 운영체제의 중간에 위치 

- 장치를 동작시키는 일을 함

**Firmware**

- 시스템의 효율을 높이기 위해 들어 있는 기본적인 프로그램 
- 하드웨어에 장착된 칩 속에 내장된 프로그램이란 점에서 일반적인 소프트웨어와는 다름 
- 소프트웨어를 하드웨어화시킨 것으로서 소프트웨어와 하드웨어의 중간에 해당됨 

- 하드웨어의 특성도 가지고 있으나, 실제로는 소프트웨어에 더 가깝다고 볼 수 있음 

- 전형적인 처리 루틴, 비휘발성, 변경불가 등의 특징으로 특수한 영역에 많이 사용되고 있음

## Hardware

정보에 대한 처리가 실제 일어나게 해주는 물리적인 장치들

전자회로와 그 밖의 물리적인 장치들로 이루어짐 

컴퓨터 정보들의 전송 통로를 제공

- CPU와 같은 핵심 부품들을 장착한 main board로 이루어짐 
- 입출력 장치, CPU, Memory 등으로 이루어져 있음

- 부품에 전기를 공급하는 전원 공급 장치와 입력 장치 그리고 출력 장치도 하드웨어에 속함

### 1. Bus

- 데이터의 통로 역할을 함

  - 칩 내부의 연결 통로

  - 칩 외부의 연결 통로

### 2. Processor

- **C**entral **P**rocessing Unit 중앙 처리 장치

  - 실제적으로 컴퓨터 명령어들을 수행

  - 컴퓨터의 모든 처리를 수행하는 곳

  - 입력, 출력, 저장 장치 제어

  - 케이스 안의 메인보드 또는 마더보드에 존재

### 3. Main Memory

- 주 기억 장치 (일차 기억 장치)

  - 프로그램과 데이터는 메모리에 저장이 되어 있어야 프로세서에 의해 처리될 수 있음.
    - 컴퓨터 내에서 명령어와 데이터들을 기억

  - 입력 장치로부터 들어온 자료가 저장됨

  - 영구 저장 능력이 없음, 일시적 저장장치로만 사용

  - 고속 액세스, 가격이 높고 면적을 많이 차지 -> 저장 용량의 한계

### 4. auxiliary storage device

- 보조 기억 장치(이차 기억 장치)
  - 주 기억 장치를 보조해주는 장치 

- 비휘발성: 프로그램이나 자료를 영구적으로 기억

- 읽기/쓰기 속도가 느리지만, 저장 밀도가 높고, 비트 당 가격이 낮음

- 현재 사용하지 않는 프로그램을 저장
  - 작업이 수행될 때, program loading
    - 보조 기억 장치에서 주 기억 장치로 정보를 이동함

- flash memory

  - 전자적으로 데이터를 지우고 쓸 수 있는 비휘발성 메모리.

  - 움직임 충격에 강하여 휴대용 기기에 널리 쓰인다

  - USB flash drive 
    - USB 인터페이스를 장착한 NAND타입의 메모리

  - **S**ecure Digital, microSD

- **S**olid **S**tate **D**rive

  - 디스크/헤더와 같은 기계적 장치가 빠짐

  - 저전력, 저소음, 저중량

### 5. Graphic Processing Unit

- 2D/3D 그래픽 처리에 특화된 마이크로프로세서
- 주기억장치에서 만들어진 글자나 그림을 모니터에 나타내기 위한 전자신호로 변환하는 카드
- 사용하는 카드의 종류에 따라 최대 해상도, 재생주기, 표현할 수 있는 색상의 수가 결정됨
- 비디오 메모리
  - 그래픽 카드가 가지고 있는 자체 기억장치
  - 모니터에 나타낼 자료를 미리 만드는데 사용됨

- **G**eneral Purpose **GPU**
  - GPU를 CPU처럼 ‘범용’ 처리장치로 활용

### 6. Input Device

문자나 기호 같은 데이터를 컴퓨터가 이해하도록, 전기적 신호장치로 변환시켜 주는 장치 

- typing 키보드
  - 키보드 제어 회로와 시스템 버스를 통해 CPU와 연결

- pointing 마우스
  - 이동을 감지하여 감지된 이동을 이진 코드로 변환

- scanning 스캐너
  - 레이저 광선을 이용하여 문서, 기호, 사진 등의 인쇄물을 직접 읽어 들임
    - Barcode reader, handheld/flatbed scanner

- terminal 단말기
  - 입력 장치 + 화면 + 대형 컴퓨터와의 연결 장치

- 스타일러스
- 터치 패드
- 터치 스크린

### 7. Output Device

처리된 데이터를 사람이 이해할 수 있는 형태로 출력

외부 세계와 통신하는 능력

중앙처리 장치가 처리한 결과를 출력하는 장치 

- 모니터

  - 컴퓨터에서 나오는 글자, 그림 등의 결과를 화면에 보여주는 장치

  - 크기: ‘Inch’로 나타냄

  - resolution

    - 화면에 나타나는 그림이나 글자의 선명도를 결정하는 요소

    - 화면에서 가로와 세로로 각각 몇 개의 pixel을 나타낼 수 있는 가를 의미

    - 실제 화면의 해상도: 모니터 + 그래픽 카드에 의해서 결정됨

  - **L**iquid **C**rystal **D**isplay

    - 전압이 걸리면 빛을 막는 소형 트랜지스터를 사용
    - 디스플레이의 질은 해상도와 주사율에 의해 정의

  - **L**ight **E**mitting **D**iode

- 프린터

  - 전자장비에 저장되어 있는 문서를 입력 받아 종이 등에 인쇄하는 장치

  - 프린터 출력의 질은 수평과 수직 방향 모두에 대한 해상도로 측정

  - 내용물의 색상
    - 흑백, 컬러

  - 인쇄방식
    - 레이저, 잉크젯

## References

[2018 / 강원대학교 컴퓨터공학과 이창기 교수 / 컴퓨터개론 / 컴퓨터 시스템의 구조](https://cs.kangwon.ac.kr/~leeck/intro_computer/IC_03.pdf)

[2015 / 신한대학교 IT융합공학부 이동규 교수 / 컴퓨터구조 / 컴퓨터시스템 개요](http://contents.kocw.or.kr/KOCW/document/2015/shinhan/leedonggyu/1.pdf)

[2014 / 덕성여자대학교 컴퓨터공학전공 유견아 교수 / 컴퓨터 입문 / 컴퓨터 구조](http://contents.kocw.or.kr/KOCW/document/2014/deoksung/Yugyeona/3.pdf)

[2010 / 써로마인드 CTO 김병희 / 컴퓨터의 개념 및 실습 / 컴퓨터의 구조](https://bi.snu.ac.kr/~bhkim/lectures/digi_com_10f_snu/02.Architecture.pdf)
