[OS/CPU Scheduling/FCFS](#os-cpu-scheduling-fcfs)

1. [Scheduling](#1-scheduling)

2. [Scheduling Types](#2-scheduling-types)

3. [Scheduling Criteria](#3-scheduling-criteria)
   + [Cycle](#cycle)

4. [Scheduling Algorithms](#4-scheduling-algorithms)
   + [FCFS Scheduling](#fcfs-scheduling)

* [References](#references)

# OS/CPU Scheduling/FCFS

## 1. Scheduling

- CPU 스케줄링 

  - 어떻게 프로세스에게 CPU의 사용을 분배할 것인가 

  - Multiprogramming 다중 프로그래밍 운영체제
    - 시분할시스템
    
    - CPU의 사용률을 높일 수 있다
    
        <details>
        <summary>자세히</summary>
        <ul>
            <li>여러 개의 프로세스를 주기억장치에 적재하여 실행 중이던 프로세스가 중앙처리장치 동작이 아닌 다른 사건(입출력 동작)이 발생하기를 기다리는 동안 다른 프로세스가 중앙처리장치에 의해 실행되도록 하여 <strong>중앙처리장치 이용률을 최대화</strong>하는 개념</li>
            <br>
            <li>실행 상태에 있던 프로세스의 실행이 종료되거나 다른 사건이 발생하기를 기다리기 위해 대기 상태가 되면 <strong>다음에 실행할 새로운 프로세스</strong>를 정해야 함</li>
        </ul>
        </details>
    
  - 메모리 내 실행 준비된 프로세스들 가운데 하나를 선택하여 CPU를 할당함
  
    - Ready queue 안에 있는 프로세스들 가운데 CPU를 사용할 (스케줄링 정책에 따라) 프로세스를 선택하는 것
  
      > **멀티코어는 어떻게 할까?**
  
- CPU 스케줄링의 목표

  - CPU 를 최대로 활용하는 것: idle 최소화

    > **커널이 사용하는 CPU 시간은?**

## 2. Scheduling Types

- 선점형 스케줄링 先占 (Preemptive Scheduling)

  - OS가 현재 CPU를 사용하고 있는 프로세스의 수행을 강제적으로 정지할 수 있음

  - 프로세스간 데이터 공유시 경쟁상태 유발
  - 타임퀀텀을 소진한 상황에서 스케줄링

- 비선점형 스케줄링 非先占 (Non-preemptive Scheduling)

  - Multiprogramming의 기본 스케줄링 – OS가 강제로 CPU 사용을 중단시키지 않음.
  - 모든 프로세스에게 공정한 CPU 사용 기회 부여
  - 프로세스가 I/O를 하는 상황에서만 수행되는 스케줄링
  - 프로세스 상태 변화
    - running => wait
    - running => ready (할당된 time slice를 모두 사용 후 자발적으로 반납)
    - waiting => ready
    - terminates

## 3. Scheduling Criteria

- CPU utilization 활용률
  - 전체 시스템 시간 중 CPU가 작업을 처리하는 시간의 비율을 최대화. 
    - 최대한 CPU가 유휴 상태에 있지 않게 함
  
- Throughput 처리량
  - CPU가 단위 시간 당 처리하는 프로세스의 개수를 최대화. 

- Response time 응답 시간

  - 프로세스가 입출력을 시작해서 첫 결과가 나오는데 까지 걸리는 시간을 최소화

  - 프로세스에게 계산 요청이 들어갔을 때, 그 요청을 처리하여 결과가 출력되기 시작하는데 까지 걸리는 시간

    > **Queue 로 설명해 보기**

- Waiting time 대기 시간
  - 프로세스가 Ready Queue 내에서 대기하는 시간의 총합을 최소화. 

- Turnaround time - I/O 시간
  - 개별 프로세스가 시작해서 끝날 때까지 필요한 총 시간 (대기시간+실행시간+I/O시간)을 최소화

**Scheduler – design**

- 모든 조건을 만족 시키는 스케줄러를 만드는 것은 현실적으로 불가능

- 시스템의 용도에 따른 요구사항이 달라짐. 

  - 슈퍼 컴퓨터 – CPU 사용률

  - 개인용 컴퓨터 – 응답시간 

  - GPU – 처리량

### Cycle

**프로세스 수행 사이클의 구성**

- CPU-I/O Burst Cycle 

  - CPU Burst : CPU로 연산을 수행하는 시간.

  - I/O Burst : I/O 처리를 위해 기다리는 시간. 

  - 일반적인 프로세스는 두 burst를 번갈아 가며 수행 반복
    - 한 프로세스의 I/O burst가 발생하는 동안 CPU burst 상태의 다른 프로세스에게 CPU를 할당
    - CPU-burst distribution is of main concern

- 프로세스 분류에 따른 CPU Burst의 특징 

  - CPU-bound 프로세스 : 긴 CPU burst 

  - I/O-bound 프로세스 : 짧은 CPU burst 

  - 어떤 종류의 프로세스가 많은 지에 따라 스케줄링 기법의 효율성이 달라짐.

## 4. Scheduling Algorithms

- **F**irst-**C**ome, **F**irst-**S**erved Scheduling 

- **S**hortest-**J**ob-**F**irst Scheduling 

- **P**riority Scheduling 

- **R**ound-**R**obin Scheduling 

- **M**ultilevel **Q**ueue Scheduling 

- **M**ultilevel **F**eedback **Q**ueue Scheduling

### FCFS Scheduling

First-Come First-Served 먼저 도착한 프로세스를 먼저 서비스(실행)하는 방법

- Ready 큐에 있는 순서대로 CPU를 할당한다. 
  - FIFO 큐를 사용하여 간단하게 구현 가능.


- 작업의 수행 순서에 따라 대기 시간이 변할 수 있음

  - 프로세스의 실행 순서에 따라 평균 대기 시간의 차이가 크다.

  - 처리시간이 짧은 프로세스 먼저 처리 => waiting time 최소화

## References

[2021 / 고려대학교 컴퓨터학과 OSLab / 유혁 교수 / 운영체제 / CPU Scheduling](https://os.korea.ac.kr/wp-content/uploads/2021/04/2021-OS_07-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81.pdf)

[2016 / 부산가톨릭대학교 컴퓨터공학과 / 변상선 교수 / 운영체제 / 프로세스 스케줄링](http://vod3.kocw.net/KOCW/document/2016/cup/byunsangseon/8.pdf)

[2015-2 / 금오공과대학교 컴퓨터소프트웨어공학과 / 이해연 교수 / 컴퓨터 사이언스 / 운영체제](http://contents.kocw.or.kr/KOCW/document/2015/kumoh/leehaeyeon/07.pdf)

[2015-1 / 부산가톨릭대학교 소프트웨어학과 / 원성현 교수 / 운영체제 / 단일 프로세서 스케줄링](http://contents.kocw.net/KOCW/document/2015/cup/weonsunghyun/6.pdf)
