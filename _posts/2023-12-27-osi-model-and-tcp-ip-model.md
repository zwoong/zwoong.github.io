---
layout: post
title: OSI 모델, TCP/IP 모델
tags: [네트워크, OSI 모델, TCP/IP 모델]
categories: [네트워크, OSI 모델, TCP/IP 모델]
image:
  path: /assets/img/post/network/osi-and-tcp-ip.webp
  alt: osi-and-tcp
date: 2023-12-27 23:09 +0900
---

## OSI 모델, TCP/IP 모델

OSI(개방형 시스템 상호 연결) ​​모델과 TCP/IP(전송 제어 프로토콜/인터넷 프로토콜) 모델은 **네트워크와 해당 프로토콜을 이해하고 설계하는 데 사용되는 개념적 프레임워크**(여러 기능을 가진 클래스와 라이브러리가 '특정 결과물을 구현하고자' 합쳐진 형태)이다. 두 모델 모두 각기 다른 기능을 지닌 서로 다른 계층에 대해 알아보자. 😉

### OSI(Open Systems Interconnection) 모델

- **물리 계층**
  - **역할**: 네트워크 통신 매체를 통한 **데이터의 물리적 전송**을 제공한다.
  - **프로토콜**
    - **이더넷**: 근거리 통신망(LAN)에 사용되는 가장 일반적인 프로토콜이다.
    - **DSL(Digital Subscriber Line)**: 전화선을 통해 디지털 데이터를 전송하는 데 사용되는 기술이다.
- **데이터링크 계층**
  - **역할**: 직접 연결된 두 노드 사이의 링크인 **노드 간 데이터 전송을 제공**한다. 또한 **물리 계층의 오류 수정도 처리**한다.
  - **프로토콜**
    - **PPP(지점 간 프로토콜)**: 직렬 인터페이스를 통한 직접 연결에 사용되며 일반적으로 전화 접속 모뎀 또는 DSL을 통한 인터넷 액세스에 사용된다.
- **네트워크 계층**
  - **역할**: 장치 주소 지정을 관리하고, **데이터 전송을 위한 최상의 경로를 식별**하고, **데이터 패킷을 라우팅**한다.
  - **프로토콜**
    - **IP(인터넷 프로토콜)**: **IP 주소 지정, 라우팅, 패킷 조각화 및 재조립을 담당**한다.
    - **ICMP(인터넷 제어 메시지 프로토콜)**: ping 명령과 같은 진단 및 오류 보고에 사용된다.
- **전송 계층**
  - **역할**: 분할, 승인, 다중화를 포함하여 **애플리케이션에 대한 엔드투엔드 통신 서비스를 제공**한다.
  - **프로토콜**
    - **TCP(전송 제어 프로토콜)**: 승인 및 재전송을 사용하여 **데이터 패킷이 오류 없이 순서대로 도착하도록 보장하는 연결 지향 프로토콜**이다.
    - **UDP(사용자 데이터그램 프로토콜)**: TCP의 안정성이 필요하지 않은 애플리케이션을 위한 더 간단하고 비연결형 프로토콜이다.
- **세션 계층**
  - **역할**: **애플리케이션 간의 세션이나 연결을 관리**한다. 연결을 설정, 관리 및 종료한다.
  - **프로토콜**
    - **NetBIOS(네트워크 기본 입출력 시스템)**: 세션 계층과 관련된 서비스를 제공하여 서로 다른 컴퓨터의 응용 프로그램이 LAN을 통해 통신할 수 있도록 한다.
    - **PPTP(지점 간 터널링 프로토콜)**: VPN을 구현하고 네트워크 프로토콜 데이터를 캡슐화하는 데 사용된다.
- **프리젠테이션 계층**
  - **역할**: 데이터를 애플리케이션 계층이 수용할 수 있는 형태로 변환한다. 이 계층은 **네트워크를 통해 전송될 데이터의 형식을 지정하고 암호화**한다.
  - **프로토콜**
    - **SSL/TLS(Secure Sockets Layer/Transport Layer Security)**: 인터넷을 통해 전송되는 정보를 암호화하기 위한 프로토콜이다.
- **애플리케이션 계층**
  - **역할**: **최종 사용자에게 가장 가까운 이 계층은 소프트웨어 애플리케이션과 상호 작용**하여 통신 구성 요소를 구현한다.
  - **프로토콜**
    - **HTTP(Hypertext Transfer Protocol)**: 인터넷을 통해 웹페이지를 전송하는 데 사용된다.
    - **FTP(파일 전송 프로토콜)**: 컴퓨터 네트워크의 클라이언트와 서버 간에 파일을 전송하는 데 사용된다.
    - **SMTP(Simple Mail Transfer Protocol)**: 이메일 전송에 사용된다.

> 그렇다면 A라는 컴퓨터에서 B라는 컴퓨터에 데이터를 보낼 때 어떤 식으로 동작하는 것일까? 🧐

#### OSI 모델에 데이터 전송예시❗️

컴퓨터 A가 컴퓨터 B로 데이터를 보내면 데이터는 OSI 모델의 각 계층을 통과하여 응용 프로그램 계층에서 컴퓨터 A 측의 물리 계층으로 이동한 다음 컴퓨터 B 측의 계층 위로 이동한다.

![osi-example](/assets/img/post/network/osi-example.png){: width="800" }

- **컴퓨터 A(데이터 전송)**

  - **애플리케이션 계층**: **데이터 전송 프로세스는 웹 브라우저나 이메일 클라이언트와 같은 컴퓨터 A의 애플리케이션으로 시작**된다. 예를 들어 컴퓨터 A가 이메일을 보내는 경우 이메일 클라이언트는 SMTP(Simple Mail Transfer Protocol)를 사용하여 메시지 형식을 지정하고 보낸다.
  - **프레젠테이션 계층**: **네트워크가 이해할 수 있는 방식으로 데이터 형식을 지정**한다. 이메일과 같은 데이터를 암호화하거나 압축해야 하는 경우 여기에서 수행한다. SSL/TLS와 같은 프로토콜을 암호화에 사용할 수 있다.
  - **세션 계층**: **컴퓨터 B와의 연결을 설정, 관리 및 종료**한다. 예를 들어 VPN 연결을 위해 NetBIOS 또는 PPTP를 사용하여 세션을 설정한다.
  - **전송 계층**: **데이터를 더 작은 패킷으로 나눈다**. 여기서는 모든 패킷이 올바르게 전송되고 수신되게 하려고 TCP(전송 제어 프로토콜)가 일반적으로 사용된다. TCP는 각 패킷에 번호를 매기고 올바른 순서를 보장하며 오류를 확인한다.
  - **네트워크 계층**: 이 계층은 **컴퓨터 A에서 컴퓨터 B로 데이터가 이동하는 최상의 물리적 경로를 결정**한다. IP(인터넷 프로토콜)는 대상 주소를 찾고 네트워크를 통해 각 패킷을 라우팅하는 데 사용된다.
  - **데이터 링크 계층**: 여기서 패킷은 네트워크 세그먼트에 필요한 헤더와 트레일러로 구성된다. MAC(Media Access Control) 주소는 **패킷이 올바른 물리적 장치에 도달하는지 확인하는 데 사용**된다.
  - **물리적 계층**: **데이터는 최종적으로 전기 신호 또는 광 펄스로 변환**되어 이더넷 케이블이나 광섬유 케이블과 같은 **물리적 매체를 통해 컴퓨터 B에 도달**한다.

- **컴퓨터 B(데이터 수신)**
  - **물리적 계층**: 컴퓨터 B는 **물리적 네트워크 인터페이스를 통해 전기 신호 또는 광 펄스를 수신**한다.
  - **데이터 링크 계층**: **데이터 패킷의 물리적 전송 오류를 검사하고 시스템이 이해할 수 있는 형식으로 해석**한다.
  - **네트워크 계층**: **패킷이 올바른 대상에 도달했는지 확인**하기 위해 IP 헤더를 읽는다. 여러 개의 패킷이 있는 경우 이 계층은 이러한 패킷을 올바른 순서로 재조립하는 프로세스를 시작한다.
  - **전송 계층**: 컴퓨터 B의 TCP는 오류를 확인하고 필요한 경우 재전송을 요청한다.
  - **세션 계층**: 두 컴퓨터 간의 세션을 유지하여 데이터 전송 기간 동안 연결이 유지되도록 한다.
  - **프레젠테이션 계층**: 데이터가 암호화되거나 압축된 경우 이 계층은 **데이터를 원래 형식으로 해독하거나 압축을 푼다**.
  - **애플리케이션 계층**: 데이터를 수신하도록 의도된 애플리케이션(예: 이메일 클라이언트 또는 웹 브라우저)은 수신 **데이터를 가져와 사용하거나 표시하기 위해 처리**한다.

### TCP/IP(Transmission Control Protocol/Internet Protocol) 모델

- **네트워크 액세스 계층**
  - **기능**: 네트워크 하드웨어를 통한 **데이터의 물리적 전송을 담당**한다. 이는 OSI 모델의 물리적 및 데이터 링크 계층의 조합에 해당한다.
  - **데이터 전송에서의 역할**
    - 이더넷 케이블 및 네트워크 어댑터와 같은 데이터 전송의 물리적 및 하드웨어 측면을 처리한다.
    - 주소 지정(MAC 주소), 오류 감지 및 수정을 관리한다.
  - **주요 프로토콜**: 이더넷, PPP(지점 간 프로토콜), ARP(주소 확인 프로토콜)
- **인터넷 계층**
  - **기능**: 네트워크 경계를 넘어 **패킷을 라우팅하여 데이터가 소스에서 대상으로 전송되도록 하는 역할**을 한다.
  - **데이터 전송에서의 역할**
    - **IP 주소를 기반으로 데이터 패킷을 라우팅**한다.
  - **주요 프로토콜**: IP(인터넷 프로토콜), ICMP(인터넷 제어 메시지 프로토콜), IGMP(인터넷 그룹 관리 프로토콜)
- **전송 계층**
  - **기능**: 전송 계층은 **호스트 컴퓨터 간의 엔드투엔드 통신과 데이터 무결성을 담당**한다.
  - **데이터 전송에서의 역할**
    - 전송을 위해 데이터를 더 작은 패킷으로 분할하고 목적지에서 재조립하는 작업을 관리한다.
    - 오류 수정 및 흐름 제어 메커니즘을 통해 안정적인 데이터 전송을 보장한다.
  - **주요 프로토콜**: TCP(전송 제어 프로토콜), UDP(사용자 데이터그램 프로토콜)
- **애플리케이션 계층**
  - **기능**: 네트워크 통신을 위해 애플리케이션에서 사용하는 상위 수준 프로토콜을 포함한다.
  - **데이터 전송에서의 역할**
    - 애플리케이션이 네트워크를 통해 데이터를 교환하는 데 사용하는 프로토콜을 제공한다.
    - 데이터 인코딩, 암호화 및 세션을 관리한다.
    - **주요 프로토콜**: HTTP(Hypertext Transfer Protocol), FTP(파일 전송 프로토콜), SMTP(Simple Mail Transfer Protocol), DNS(Domain Name System)

### OSI, TCP/IP 차이점

- **레이어 수**
  -**OSI 모델**: 7개의 개별 계층(물리적, 데이터 링크, 네트워크, 전송, 세션, 프레젠테이션 및 애플리케이션)이 있다.
  - **TCP/IP 모델**: 4개 계층(네트워크 액세스, 인터넷, 전송 및 애플리케이션)으로 구성된다.
- **디자인 접근 방식**
  - **OSI 모델**: 국제 표준화 기구(ISO)에서 네트워크 프로토콜 설계를 위한 이론적이고 포괄적인 프레임워크로 개발되었다.
  - **TCP/IP 모델**: 인터넷에서 사용되는 프로토콜을 기반으로 개발되었다. 실제 네트워킹에 더욱 실용적인 모델이다.
- **표준화 및 실용화**
  - **OSI 모델**: 네트워크 아키텍처를 이해하는 데 널리 알려졌지만 실제 네트워킹 프로토콜의 기초로 사용되지는 않는다.
  - **TCP/IP 모델**: 인터넷 및 네트워킹 프로토콜의 기초를 형성하며 실제 구현에 널리 사용된다.
- **레이어 기능**
  - **OSI 모델**: 각 레이어마다 구체적이고 뚜렷한 기능이 있다. OSI의 세션 및 프리젠테이션 계층은 TCP/IP 모델에서 명시적으로 정의되지 않는다. 해당 기능은 일반적으로 TCP/IP 애플리케이션 계층의 일부로 간주한다.
  - **TCP/IP 모델**: 레이어 간 경계가 덜 견고하여 더욱 유연해졌다. OSI의 물리적 및 데이터 링크 계층을 링크 계층으로 결합하고, OSI의 애플리케이션, 프리젠테이션 및 세션 계층을 애플리케이션 계층으로 결합한다.

요약하면, **OSI 모델은 네트워크 계층을 이해하기 위한 보다 상세하고 구조화된 접근 방식을 제공**하지만, **TCP/IP 모델은 최신 네트워킹에서 사용되는 실제 프로토콜 및 방식과 더욱 밀접하게 일치**한다. 😉