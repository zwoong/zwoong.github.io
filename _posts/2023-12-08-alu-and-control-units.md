---
layout: post
title: ALU와 제어장치
tags: [컴퓨터 구조, ALU와 제어장치]
categories: [컴퓨터 구조, ALU와 제어장치]
image:
  path: /assets/img/post/computer-architecture/alu.png
  alt: alu
date: 2023-12-08 12:45 +0900
---

CPU 내에는 **ALU(산술 논리 장치)와 제어 장치**라는 두 가지 중요한 구성 요소가 존재하는데, 이 둘을 지금부터 알아보자! 😉

## 산술 논리 장치

ALU는 산술 및 논리 연산을 수행하는 CPU의 중요 구성 요소이다.

### 산술 논리 장치(ALU) 구성 요소

- **Integer Operand** (정수 피연산자): ALU가 처리하는 데이터로서, 이들은 보통 CPU의 레지스터나 메모리에서 오며, ALU는 이러한 피연산자들에 대해 산술 연산(덧셈, 뺄셈, 곱셈, 나눗셈 등)이나 논리 연산(AND, OR, XOR, NOT 등)을 수행한다. 예를 들어, **두 정수의 덧셈 연산에서 이 두 정수는 피연산자**가 된다.
- **Opcode** (연산 코드): **어떤 종류의 연산을 수행할지를 지시하는 코드**로서, 이는 CPU의 제어 장치(Control Unit)에 의해 해석되며, ALU에 어떤 연산을 수행할지를 알려준다.
- **Status** (상태 플래그): **ALU의 연산 결과에 대한 추가 정보를 제공**한다.

### 주요 연산 코드 종류

- **ADD**: 값을 추가한다.
- **AND**: 비트 단위 AND 연산을 수행한다.
- **MOV**: 한 곳에서 다른 곳으로 데이터를 이동한다.
- **JMP**: 지정된 메모리 주소로 이동한다.
- **CMP**: 두 값을 비교하고 플래그를 설정한다.
- **SHL**: 비트를 왼쪽으로 이동한다.

### 주요 상태 플래그 종류

- **Zero Flag**: 연산 결과가 0인 경우에 설정된다.
- **Carry Flag**: 주로 덧셈이나 뺄셈 연산에서 사용되며, 이 플래그는 연산 중에 최상위 비트(가장 왼쪽 비트)에서 발생한 캐리(덧셈)나 보로우(뺄셈)를 나타낸다.
- **Overflow Flag**: 부호 있는 정수 연산에서 중요하며, 이 플래그는 연산 결과가 해당 데이터 타입으로 표현할 수 있는 범위를 벗어났을 때 설정된다.
- **Sign Flag**: 연산 결과의 부호를 나타내며, 대부분의 컴퓨터 시스템에서는 최상위 비트를 사용하여 정수의 부호를 나타낸다. (0은 양수, 1은 음수)

## 제어장치

제어장치는 **CPU 내의 다른 구성 요소 또는 장치의 작동을 관리하거나 지시**하는 장치이다.

### 제어장치의 기능

- **데이터 관리**: 메모리와 주변 장치 또는 장치 내 다양한 ​​구성 요소 간 데이터 전송과 같은 시스템 내 데이터 흐름을 관리한다.
- **명령 실행**: 프로그램 명령을 실행하고 이러한 명령의 순서와 작동을 제어한다.
- **자원 할당**: 메모리, 처리 능력, 주변 장치 액세스와 같은 시스템 리소스를 할당하여 효율적이고 공정한 자원할당을 해준다.
- **모니터링 및 대응**: 시스템 상태 및 환경 요인을 모니터링하여 변경, 오류 또는 사용자 입력에 응답할 수 있다.
- **커뮤니케이션 관리**: 네트워크를 통해 데이터 패킷을 처리하는 네트워크 컨트롤러와 같이 시스템의 여러 부분 간 또는 시스템 간 통신을 관리한다.