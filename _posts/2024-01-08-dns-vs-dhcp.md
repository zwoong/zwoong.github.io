---
layout: post
title: DNS vs DHCP
tags: [네트워크, DNS vs DHCP]
categories: [네트워크, DNS vs DHCP]
image:
  path: /assets/img/post/network/dns-vs-dhcp.jpg
  alt: dns-vs-dhcp
date: 2024-01-08 23:11 +0900
---

## DNS

DNS는 본질적으로 인터넷의 전화번호부로서, **사람이 읽을 수 있는 도메인 이름(예: www.example.com)을 기계가 읽을 수 있는 IP 주소(예: 192.0.2.1)로 변환**하여 컴퓨터가 인터넷을 통해 서로 찾고 통신할 수 있도록 한다. 😉

### DNS 동작 방식 ❗️

1. **사용자가 도메인 이름을 입력한다.**
   - 웹 브라우저에 도메인 이름(예: www.example.com)을 입력하면 DNS 확인 프로세스가 시작되며, 이 프로세스는 **본질적으로 도메인 이름을 컴퓨터가 이해할 수 있는 IP 주소로 변환**하는 것이다.
2. **브라우저에서 캐시를 확인한다.**
   - 브라우저는 먼저 캐시를 확인하여 최근에 도메인 이름을 확인했는지 확인한다.
3. **DNS Resolver**
   - 도메인 이름이 캐시에 없으면 브라우저는 쿼리를 DNS 확인자로 보낸다. 이 확인자는 **일반적으로 인터넷 서비스 공급자(ISP)에서 제공**한다. 확인자의 역할은 도메인 이름과 연결된 IP 주소를 찾는 것이다.
4. **Root Name Server**
   - DNS 확인자에 캐시된 레코드가 없으면 루트 네임 서버에 쿼리한다(.com, .net, .org). 이러한 루트 네임 서버는 전 세계적으로 13개가 있으며 최상위 도메인(TLD)에 대한 정보를 보유한다.
5. **TLD Name Server**
   - 루트 네임 서버는 도메인에 대한 적절한 TLD 이름 서버(예: www.example.com에 대한 .com TLD 서버)에 대한 주소를 응답한다. 그런 다음 DNS 확인자는 TLD 서버에 쿼리한다.
6. **Domain's Authoritative Name Server**
   - TLD Server는 DNS 확인자를 도메인의 권한 있는 이름 서버를 가리킨다. 이러한 서버에는 **도메인 이름과 관련된 IP 주소를 포함하여 도메인에 대한 실제 정보가 있다**. 해당 도메인에 권한이 있는 서버는 www.example.com에 대한 IP 주소를 응답한다.
7. **사용자가 응답을 캐시 한다.**
   - DNS 확인자는 지정된 시간(TTL(Time-To-Live) 값으로 정의됨) 동안 캐시에 DNS 레코드를 저장한다. 이 캐싱은 DNS 서버의 로드를 줄이고 향후 같은 도메인에 대한 액세스 속도를 높이는 데 도움이 된다.
8. **브라우저로 IP 주소 전송**
   - DNS 확인자는 IP 주소를 사용자의 브라우저로 보낸다. 브라우저는 HTTP(또는 HTTPS) 프로토콜을 사용하여 www.example.com을 호스팅하는 웹 서버에 대한 연결을 시작한다.

![dns-workflow](/assets/img/post/network/dns-workflow.png){: width=＂700＂ }

### DHCP(Dynamic Host Configuration Protocol)

DHCP는 **IP(인터넷 프로토콜) 네트워크에서 사용되는 네트워크 관리 프로토콜**이다. 네트워크의 장치(클라이언트라고 함)에 대한 IP 주소, 서브넷 마스크, 게이트웨이 및 기타 IP 매개변수 할당을 자동화한다.

#### DHCP의 목적

- **자동 IP 주소 할당**
  - DHCP는 **IP 주소를 장치에 동적으로 할당**하므로 네트워크 관리자가 IP 주소를 수동으로 할당할 필요성이 없다.
- **네트워크 구성**
  - IP 주소 외에도 DHCP는 서브넷 마스크, 기본 게이트웨이, DNS 서버 주소와 같은 구성 정보를 클라이언트에 제공한다.

#### DHCP의 주요 구성 요소

- **DHCP 서버**
  - **IP 주소 풀과 구성 정보를 보유하는 서버**로서, 클라이언트의 요청에 응답하고 IP 주소 및 기타 네트워크 구성 매개변수를 할당한다.
- **DHCP 클라이언트**
  - DHCP 서버에 구성 정보를 요청하는 네트워크의 장치이다.
- **IP 주소 풀**
  - DHCP 서버가 관리하고 클라이언트에 할당하는 IP 주소 범위이다.

#### DHCP 작동 방식: 4단계 프로세스

- **DHCPDISCOVER**
  - 클라이언트 장치가 네트워크에 연결되면 DHCP 서버를 찾기 위해 DHCPDISCOVER 메시지를 브로드캐스트한다.
- **DHCPOFFER**
  - 네트워크의 DHCP 서버는 DHCPOFFER 메시지에 응답하여 IP 주소와 기타 구성 세부 정보를 클라이언트에 제공한다.
- **DHCPREQUEST**
  - 클라이언트는 제공된 매개변수를 수락했음을 나타내는 DHCPREQUEST 메지시에 응답한다.
- **DHCPACK**
  - DHCP 서버는 클라이언트에 DHCPACK(승인) 메시지를 보내 IP 주소 임대를 확인하고 네트워크 구성 정보를 제공한다.

![dhcp-workflow](/assets/img/post/network/dhcp-workflow.png){: width=＂700＂ }

### DNS와 DHCP 주요 차이점

- **범위**: DNS는 전역 수준에서 작동하여 인터넷의 도메인 이름을 IP 주소로 변환하는 반면 DHCP는 대부분 IP 주소 할당을 위한 로컬 네트워크 프로토콜이다.
- **기능**: DNS는 네트워크 통신을 위해 도메인을 IP 주소로 확인하는 반면, DHCP는 로컬 네트워크 내의 장치에 IP 주소와 네트워크 설정을 제공한다.
