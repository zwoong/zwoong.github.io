---
layout: post
title: 병렬 처리 기법
tags: [컴퓨터 구조, 병렬 처리 기법]
categories: [컴퓨터 구조, 병렬 처리 기법]
date: 2023-12-12 00:22 +0900
---

## 병렬 처리

컴퓨팅에서 "병렬 처리"라는 용어는 큰 문제를 더 작은 하위 문제로 나누고 이러한 하위 문제를 **단일 컴퓨터 내의 여러 프로세서나 코어 또는 여러 컴퓨터에서 동시에 또는 병렬로 처리하는 기술**을 의미한다. 이 접근 방식은 컴퓨팅 작업 속도를 크게 높이고 대규모 계산 및 복잡한 데이터 처리 작업을 처리하는 데 특히 유용하다.

### 병렬 처리의 주요 개념

- **다중 프로세서/코어**: 병렬 처리에서는 **작업이 여러 처리 장치(CPU 또는 CPU 내의 코어)에 분산**된다. 각 프로세서는 문제의 해당 부분을 독립적으로 처리한다.
- **문제 분할**: 주요 작업은 더 작고 관리하기 쉬운 하위 작업으로 나뉜다. 이 구분은 작업의 성격과 병렬 처리 시스템의 아키텍처에 따라 달라진다.
- **동시 실행**: 이러한 하위 작업은 **서로 다른 프로세서 또는 코어에서 동시에 실행**된다. 목표는 모든 하위 작업을 순차적으로 실행하는 단일 프로세서보다 더 빠르게 전체 작업을 완료하는 것이다.

### 병렬 처리 기법

- **Data Parallelism(데이터 병렬 처리)**
  - 데이터 병렬 처리는 **서로 다른 분산 데이터에 대해 동일한 작업을 동시에 수행하는 것**을 의미한다.
    대규모 데이터 세트에 대해 동일한 작업을 반복적으로 실행해야 하는 경우 가장 효과적이다.
  - 일반적으로 하나의 명령어가 여러 데이터 포인트에서 동시에 실행되는 SIMD(Single Instruction, Multiple Data) 아키텍처를 사용하여 구현되며, 벡터 프로세서나 GPU가 있는 환경에서 자주 사용된다.
  - **예시**
    - **이미지 처리**: 이미지에 필터를 적용하면 각 픽셀 또는 픽셀 그룹에서 동일한 작업(예: 흐림 또는 가장자리 감지)이 동시에 수행된다. 이미지에 수백만 개의 픽셀이 있는 경우 데이터 병렬 처리를 사용하면 처리 시간을 크게 줄일 수 있다.
- **Task Parallelism(작업 병렬 처리)**
  - 작업 병렬 처리에는 **서로 다른 데이터에서 서로 다른 작업을 병렬로 실행하는 것**이다. 뚜렷하고 독립적인 작업으로 나눌 수 있는 복잡한 작업에 적합하다.
  - 프로그램을 여러 스레드 또는 프로세스로 나누어 구현하며, 각 스레드는 서로 다른 작업을 처리한다. 멀티 코어 또는 멀티 프로세서 시스템에서 일반적이다.
  - **예시**
    - **웹 서버 운영**: 동시에 여러 웹 요청을 처리하는 서버인 경우, 데이터 검색, 계산, 파일 업로드 등 각 요청은 별도의 스레드나 프로세스에 의해 처리되므로 여러 클라이언트 요청을 동시에 처리할 수 있다.

<!-- ![data-and-task-parallelism](/assets/img/post/computer-architecture/data-and-task-parallelism.jpeg){: width="600" height="200 }

- **Pipeline Parallelism(파이프라인 병렬 처리)**
  - 파이프라인 병렬 처리는 프로세스의 여러 단계가 병렬로 실행되는 조립 라인과 유사하다. 파이프라인의 각 단계는 **데이터의 다른 부분이나 다른 작업을 처리하고 해당 출력을 다음 단계의 입력으로 전달**한다.
  - [스트림](http://www.ktword.co.kr/test/view/view.php?m_temp1=1311) 처리 및 실시간 데이터 처리 시스템에서 사용한다.
  - **예시**
    - **비디오 스트리밍**: 비디오 스트리밍 애플리케이션에서는 디코딩, 필터링(예: 밝기 조정) 및 인코딩과 같은 다양한 단계를 파이프라인화할 수 있다. 한 프레임이 디코딩되는 동안 이전 프레임과 그 이전 프레임이 동시에 필터링될 수 있다.

![pipeline-parallelism](/assets/img/post/computer-architecture/pipeline-parallelism.png){: width="600" height="200 }

> 데이터 병렬 처리와 파이프라인 병렬 처리는 얼추 비슷한 것 같은데? 🧐

### 데이터 병렬 처리와 파이프라인 병렬 처리의 차이점 ❗️

- **데이터/작업의 흐름**: 파이프라인 병렬 처리는 단계를 통한 데이터의 순차적 흐름을 강조하는 반면, 작업 병렬 처리는 독립적인 작업의 동시 실행에 중점을 둔다.
- **종속성**: 파이프라인 병렬 처리의 단계는 일반적으로 순차적 방식으로 서로 종속되는 반면, 작업 병렬 처리의 작업은 일반적으로 독립적이다.
- **적합성**: 파이프라인 병렬 처리는 일련의 단계로 나눌 수 있는 작업에 더 적합하지만, 작업 병렬 처리는 관련되지 않은 여러 작업을 동시에 처리할 수 있는 시나리오에 더 적합하다. -->