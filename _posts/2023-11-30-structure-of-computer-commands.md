---
layout: post
title: 컴퓨터 명령어의 구조
tags: [컴퓨터 구조, 컴퓨터 명령어의 구조]
categories: [컴퓨터 구조, 컴퓨터 명령어의 구조]
date: 2023-11-30 14:07 +0900
---

컴퓨터에 "5와 3을 더해라!"라는 명령하게 되면 컴퓨터는 "무엇을", "어떻게 수행하라"와 같이 구분을 지어야 할 것 같은데, 어떻게 구분을 짓는 걸까? 🧐

## 연산 코드와 피연산자

**연산 코드(opcode)와 피연산자(Operands)는 컴퓨터 프로그래밍에서 기계어 명령어의 기본 구성 요소**이다. <br>
이들은 함께 CPU가 수행해야 하는 작업과 데이터 또는 데이터의 위치를 ​​정의한다.

### 연산 코드 (Opcode)

- **정의**: opcode는 수행할 작업을 지정하는 기계어 명령어의 일부이다. 이는 본질적으로 **어떤 종류의 작업이 필요한지 CPU에 알려주는 명령이다**.
- **기능**: opcode는 더하기, 빼기, 데이터 이동, 비교, 분기 등과 같은 작업을 결정한다. 각 opcode는 고유하며 CPU 명령 세트에 정의된 특정 작업에 해당한다.
- **이진 표현**: **기계 코드에서 opcode는 이진수로 표시**된다. 예를 들어 가상의 CPU 아키텍처에서 이진 코드 '1100'은 '추가' 연산을 나타내고 '1101'은 '뺄셈'을 나타낼 수 있다.
- **다양성과 복잡성**: opcode의 수와 복잡성은 CPU 아키텍처에 따라 크게 다를 수 있으며, 일부는 매우 제한된 간단한 opcode 세트를 가지고 있지만, 최신 CPU와 같은 다른 것들은 다양하고 정교한 작업을 위한 방대하고 복잡한 opcode 배열을 가지고 있다.

### 피연산자 (Operands)

- **정의**: 피연산자는 **연산할 데이터 또는 이 데이터가 있는 위치를 지정**하는 기계어 명령의 일부다. 이들은 본질적으로 opcode에 의해 시작되는 작업의 주체이다.
- **피연산자** 유형: 피연산자에는 여러 유형이 있다.
  - **즉시 피연산자**: 명령어에 사용되는 직접적인 **숫자 값 또는 상수**값이다.
  - **레지스터 피연산자**: CPU에서 작고 빠른 저장 장치인 **CPU 레지스터에 대한 참조**이다.
  - **메모리 피연산자**: **메모리의 특정 위치를 참조**한다.

![opcode-operands](/assets/img/post/computer-architecture/opcode-operands.png){: width="700" height="200 }

> 연산 코드와 오퍼랜드가 0과 1로 이루어져 있지 않다!!? 🫢 <br>
> 연산 코드(opcode)와 **피연산자 테이블을 볼 때 일반적으로 원시 이진 형식(0과 1)으로 표시되지 않는다**. <br>
> 대신 다음과 같은 이유로 인해 일반적으로 사람이 더 읽기 쉬운 형식으로 표시된다. <br><br> **니모닉 표현**: 어셈블리 언어의 연산 코드와 피연산자는 종종 **니모닉(이진 시퀀스보다 이해하고 기억하기 쉽고 사람이 읽을 수 있는 단어 또는 약어)**으로 표현된다. 예를 들어 덧셈은 'ADD', 뺄셈은 'SUB', 이동은 'MOV' 등이다. <br> **기호 피연산자**: **피연산자는 이진수로 표시되기보다는 기호로 표시되는 경우가 많다**(레지스터의 경우 'R1', 'R2', 16진수 메모리 주소의 경우 '0x4F' 등). 이렇게 하면 코드를 더 이해하기 쉽고 작성 및 디버깅이 더 쉬워진다. <br><br> **연산 코드와 오퍼랜드 표는 사람이 읽기 쉽게 표현한 것이고, 컴퓨터 내부적으로는 0과 1로 매핑되어 사용된다.❗️**

### 주소 지정 방식

피연산자는 직접적인 숫자 값이나 상수 또는 데이터가 저장되는 메모리 주소일 수 있다고 했다. <br>
주소 지정 방법은 **프로세서가 명령어에 지정된 피연산자를 해석하는 방법을 결정**한다.

> 피연산자에 상숫값을 바로 넣으면 되지 다양한 주소 지정 방식을 사용하는 이유는 뭘까?

#### 주소 지정 방식을 사용하는 이유

- **공간 활용**: **상숫값(즉시 주소 지정)이 명령어에 직접 포함되므로 명령어가 길어지고 더 많은 메모리 공간을 사용**할 수 있다. 레지스터 또는 간접 주소 지정과 같은 주소 지정 방법을 사용하면 보다 컴팩트하고 메모리 효율적인 명령어를 사용할 수 있다.
- **코드 재사용성**: 주소 지정 방식을 통해 코드 재사용성과 모듈식 프로그래밍이 용이해진다.
- **유연성과 동적 계산**: 종종 프로그램이 처리해야 하는 데이터를 미리 알 수 없으며 프로그램이 실행됨에 따라 변경될 수 있다. **간접 또는 인덱스 주소 지정과 같은 주소 지정 방법을 사용하면 프로그램이 런타임에만 알려진 동적 데이터로 작업**할 수 있다.

> 주소 지정 방식을 사용하는 이유에 대해 알았으니 이제 종류에 대해 하나씩 살펴보자! 😉

#### 주소 지정 방식에 종류

아래말고도 몇 가지 주소 지정 방식이 더 있지만 아래 대표적인 4가지 방식에 관해서만 기술하였다.

- **Immediate Addressing**(즉시 주소 지정): 피연산자는 명령어 자체의 일부인 상숫값이다.
  - **장점**: **피연산자를 가져오는 데 추가 메모리 액세스가 필요하지 않으므로 속도가 빠르다**.
  - **단점**: 제한된 유연성으로 상숫값을 사용하는 작업에만 적합하다.
    ![immediate-addressing](/assets/img/post/computer-architecture/immediate-addressing.png){: width="400" height="200 }
- **Register Addressing**(레지스터 주소 지정): 피연산자는 CPU 내의 레지스터에 있다.
  - **장점**: 레지스터의 데이터에 액세스하는 것이 **일반적으로 메모리에 액세스하는 것보다 빠르다**.
  - **단점**: **레지스터 수가 제한되어 있어 복잡한 작업에 제약**이 될 수 있다.
    ![register-addressing](/assets/img/post/computer-architecture/register-addressing.png){: width="500" height="200 }
- **Direct Addressing**(직접 주소 지정): **메모리에 있는 데이터의 주소는 명령어의 일부로 제공**된다.
  - **장점**: 데이터의 정확한 메모리 주소가 알려져 있고 고정되어 있는 경우 유용하다.
  - **단점**: **메모리에 액세스해야 하므로 레지스터 주소 지정보다 느리다**.
    ![rdirect-addressing](/assets/img/post/computer-architecture/direct-addressing.png){: width="500" height="200 }
- **Indirect Addressing**(간접 주소 지정): 피연산자의 실제 주소가 저장되는 메모리 위치의 주소를 저장한다.
  - **장점**: 런타임 시 실제 메모리 주소가 변경될 수 있으므로 보다 동적인 데이터 처리가 가능하다.
  - **단점**: 데이터에 액세스하려면 두 번의 메모리 액세스가 필요하다. 하나는 실제 주소를 검색하고 다른 하나는 데이터에 액세스하기 위한 것이다. 이 추가 단계로 인해 프로그램 실행 속도가 느려질 수 있다.
    ![indirect-addressing](/assets/img/post/computer-architecture/indirect-addressing.png){: width="500" height="200 }