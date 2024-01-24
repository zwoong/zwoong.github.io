---
layout: post
title: 입출력 시스템
tags: [운영체제, 입출력 시스템]
categories: [운영체제, 입출력 시스템]
image:
  path: /assets/img/post/operating-system/io-systems.jpg
  alt: io-systems
date: 2023-12-20 11:56 +0900
---

## 입출력 시스템

입출력(I/O) 관리는 컴퓨터의 **내부 시스템과 외부 장치 간의 데이터 전송을 처리하고 조정**하는 운영 체제(OS)의 기본 기능이다. I/O 관리에 몇 가지 주요 구성 요소에 대해 알아보자. 😉

### I/O 관리의 주요 구성 요소

- **장치 드라이버**
  - **설명**: 장치 드라이버는 **운영 체제와 하드웨어 장치 간의 중개자 역할**을 하는 특수 소프트웨어 구성 요소이다. 각 드라이버는 특정 장치에 맞게 조정되어 **OS가 해당 장치와 올바르게 통신하고 제어**할 수 있도록 보장한다.
  - **예시**: 프린터 드라이버는 운영 체제에서 사용할 수 있는 형식의 데이터를 프린터가 이해하고 처리할 수 있는 형식으로 변환한다.
- **I/O 스케줄링**
  - **설명**: I/O 스케줄링은 운영 체제가 **여러 I/O 요청을 관리하고 우선순위를 지정하는 방법**이다. 대기 시간 단축, 처리량 최대화 등 목표에 따라 다양한 스케줄링 알고리즘을 사용할 수 있다.
  - **예시**: 하드 디스크에서 'Shortest Seek Time First' 알고리즘은 디스크의 읽기-쓰기 헤드의 움직임을 최소화하는 방식으로 데이터 요청을 정렬한다.
- **버퍼링**
  - **설명**: 버퍼링은 데이터가 **두 엔터티 간에 전송되는 동안 데이터가 버퍼 또는 메모리 영역에 일시적으로 보관**되는 프로세스이다. 이는 데이터 생산자와 소비자 간의 속도 불일치를 처리하는 데 도움이 된다.
  - **예시**: 동영상 스트리밍 시 네트워크 속도가 일시적으로 떨어지더라도 원활한 재생을 위해 데이터를 미리 버퍼링한다.

![buffering](/assets/img/post/operating-system/buffering.png){: width="600" }

- **캐싱**
  - **설명**: 캐싱에는 **자주 액세스하는 데이터의 복사본을 빠른 저장 매체에 저장**하는 작업이 포함된다. 이는 액세스 시간을 크게 줄이고 전반적인 시스템 효율성을 향상시킨다.
  - **예시**: 웹 브라우저 캐시는 최근 방문한 웹 페이지의 복사본을 저장하여 다음 방문 시 더 빠르게 로드할 수 있도록 한다.

![cache](/assets/img/post/operating-system/cache.webp){: width="600" }

- **스풀링(spooling)**
  - **설명**: 스풀링은 프린터와 같은 느린 장치에 대해 **데이터를 대기열에 넣어 I/O 작업이 완료될 때까지 기다리지 않고 I/O 작업을 요청한 프로그램이 계속 실행**될 수 있도록 하는 프로세스이다.
  - **예시**: 인쇄 스풀링을 사용하면 사용자가 다른 작업을 계속하는 동안 인쇄를 위해 여러 문서를 정렬할 수 있다.

![spooling](/assets/img/post/operating-system/spooling.png){: width="600" }

- **인터럽트(interrupt)**
  - **설명**: 인터럽트는 일반적으로 **I/O와 관련된 긴급 작업을 해결하기 위해 현재 작업을 일시적으로 중단**하는 CPU로 전송되는 신호이다. 이를 통해 CPU는 중요한 작업을 적시에 처리할 수 있다.
  - **예시**: 키보드 인터럽트는 키를 누를 때 CPU에 신호를 보내 키 입력이 즉시 처리되도록 한다.
- **직접 메모리 액세스(DMA)**
  - **설명**: DMA는 하드웨어 장치가 **CPU를 우회하여 메인 시스템 메모리에 직접 액세스**할 수 있도록 하는 기능이다. 이렇게 하면 CPU 로드가 줄어들고 메모리 작업 속도가 빨라진다.
  - **예시**: 사운드 카드에서 DMA는 CPU 개입 없이 오디오 데이터를 메모리에서 직접 저장하고 받을 수 있으므로 보다 원활한 재생 및 녹음이 가능하다.

> 버퍼링과 스풀링 언뜻 보기에는 둘 다 비슷해 보이는 데 무슨 차이점이 있을까? 🧐

### 버퍼링과 스풀링 차이점

- **목적**
  - **버퍼링**: 생산자와 소비자 사이의 속도 차이를 실시간으로 균형을 맞춘다.
  - **스풀링**: 종종 일괄 처리를 위해 여러 작업을 대기열에 추가하고 관리한다.
- **데이터 처리**
  - **버퍼링**: 연속적인 FIFO(First In First Out) 데이터 흐름을 가진다.
  - **스풀링**: 장치나 프로세스가 데이터를 처리할 준비가 될 때까지 데이터를 저장한다.
- **저장 위치**
  - **버퍼링**: 일반적으로 시스템 메모리의 일부를 사용한다.
  - **스풀링**: 디스크 저장소를 사용하는 경우가 많다.
- **실시간 처리와 일괄 처리 비교**
  - **버퍼링**: 실시간 데이터 처리에 더욱 적합하다.
  - **스풀링**: 일괄 처리 및 작업 예약에 적합하다.

요약하면, **버퍼링은 속도 불일치를 처리할 때 실시간 데이터 흐름을 관리**하지만, **스풀링은 주로 일괄 처리 모드에서 나중에 처리하기 위해 작업을 대기열에 넣고 관리**하는 것이다.❗️