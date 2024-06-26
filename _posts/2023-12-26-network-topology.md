---
layout: post
title: 네트워크 토폴리지
tags: [네트워크, 네트워크 토폴리지]
categories: [네트워크, 네트워크 토폴리지]
image:
  path: /assets/img/post/network/network.png
  alt: network
date: 2023-12-26 23:11 +0900
---

## 네트워크 토폴로지

네트워크 토폴로지는 **컴퓨터 네트워크의 다양한 요소(노드, 링크 등)의 배열 또는 레이아웃**을 나타낸다. 이는 네트워크 설계의 중요한 측면이며 성능, 안정성 및 확장성에 영향을 미칠 수 있다. 네트워크 토폴로지에는 여러 가지 유형이 있으며 각각 고유한 특성에 대해 알아보자. 😉

- **노드**: 네트워크에서 노드는 일반적으로 **통신 채널을 통해 정보를 전송, 수신 또는 전달할 수 있는 모든 장치를 의미**한다.
  - **컴퓨터**: 데스크탑, 노트북, 서버
  - **네트워크 장치**: 라우터, 스위치
  - **무선 장치**: 스마트폰, 태블릿 및 기타 모바일 장치
- **링크**: **노드를 서로 묶어 통신을 가능하게 하는 물리적 또는 논리적 연결을 의미**한다.
  - **유선 연결**: 이더넷 케이블
  - **무선 연결**: Wi-Fi 또는 Bluetooth

### 네트워크 토폴리지 유형

- **Ring Topology**
  - **설명**: 각 노드는 2개의 다른 노드에만 연결되어 각 노드를 통과하는 신호에 대한 **단일 연속 경로(링)를 형성**한다.
  - **장점**: 각 장치가 두 개의 인접 장치에만 연결되므로 **설치 및 재구성이 쉽다**.
  - **단점**: 케이블이나 장치에 **장애가 발생하면 루프가 끊어지고 전체 네트워크가 중단될 수 있다**.

![ring-topology](/assets/img/post/network/ring-topology.jpg){: width="600" }

- **Mesh Topology**
  - **설명**: **각 노드는 다른 모든 노드에 직접 연결**된다.
  - **장점**: 높은 신뢰성과 중복성을 제공하며, **한 링크가 비활성화되면 데이터는 다른 링크를 통해 전송될 수 있다**. 신뢰성이 중요한 네트워크에 이상적이다.
  - **단점**: **케이블 비용과 연결 복잡성이 매우 높다**. 복잡성과 비용 때문에 대규모 네트워크에서는 확장성이 떨어진다.

![mesh-topology](/assets/img/post/network/mesh-topology.png){: width="600" }

- **Star Topology**
  - **설명**: **모든 노드는 중앙 허브에 연결**된다. 허브는 데이터 흐름의 중계기 역할을 한다.
  - **장점**: 설치 및 배선이 쉬우며, 장치를 연결하거나 제거할 때 네트워크가 중단되지 않는다.
  - **단점**: **중앙 허브에 장애가 발생하면 전체 네트워크가 작동하지 않는다**.

![star-topology](/assets/img/post/network/star-topology.png){: width="600" }

- **Bus Topology**
  - **설명**: 모든 노드는 **단일 케이블(버스)에 연결**된다. 신호는 모든 노드에 브로드캐스트(네트워크 전체를 대상으로 패킷을 전송)되고 각 노드는 의도된 신호를 읽는다.
  - **장점**: 구현 및 확장이 쉽다. **소규모 네트워크에 적합**하다.
  - **단점**: 버스의 결함이나 파손 때문에 전체 네트워크가 중단될 수 있다.

![bus-topology](/assets/img/post/network/bus-topology.jpg){: width="600" }
