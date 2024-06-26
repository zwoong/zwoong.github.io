---
layout: post
title: Proxy Server
tags: [Research, Proxy Server]
categories: [Research, Proxy Server]
image:
  path: /assets/img/post/research/proxy-server.png
  alt: proxy-server
date: 2024-02-29 11:40 +0900
---

## Proxy Server

프록시 서버(Proxy Server)는 **클라이언트와 인터넷 사이의 중계 역할을 하는 서버**이다. 클라이언트가 인터넷상의 다른 서버에 데이터를 요청할 때, 그 **요청을 대신 전송하고 결과를 클라이언트에게 전달**한다. 프록시 서버는 데이터 교환의 중간 지점에 있어 다양한 기능과 목적으로 활용된다. 😉

### 기능 및 용도

- **캐싱**: 프록시 서버는 자주 요청되는 웹 페이지나 파일들을 로컬에 저장(캐싱)하고, 이후 동일한 요청이 있을 때 직접 제공함으로써 **웹 페이지 로딩 시간을 줄이고 네트워크 트래픽을 감소**시킨다.

- **보안**: 프록시 서버는 **클라이언트의 IP 주소를 숨기고**, 외부로부터의 접근을 제어하는 보안 게이트웨이 역할을 한다. **악의적인 웹사이트로부터 사용자를 보호하고, 내부 네트워크의 보안을 강화**할 수 있다.

- **접근 제어 및 필터링**: **특정 사이트나 콘텐츠에 대한 접근을 제한**하거나, 사용자의 인터넷 사용을 모니터링 및 제어하기 위해 사용된다. 학교나 기업에서 부적절한 웹사이트 접근을 차단하는 데 사용될 수 있다.

- **익명성**: 프록시 서버는 **사용자의 실제 IP 주소를 숨기고 대신 프록시 서버의 IP 주소를 사용**하여 인터넷에 접속한다. 이를 통해 사용자의 익명성을 보장하고, 위치 기반 콘텐츠 제한을 우회할 수 있다.

- **지역적 제한 우회**: 특정 지역에서만 서비스되는 콘텐츠에 접근하기 위해, **해당 지역에 있는 프록시 서버를 사용하여 지역 제한을 우회**할 수 있다.

### Forward Proxy vs Reverse Proxy

프록시 서버에 종류에는 대표적으로 포워드 프록시(Forward Proxy)와 리버스 프록시(Reverse Proxy)가 존재한다. **두 가지 모두 네트워크 트래픽을 대신 전송하는 중개 서버 역할**을 하지만, **그 목적과 네트워크에서의 위치, 그리고 제공하는 기능 면에서 차이점**이 있다.

### 포워드 프록시 (Forward Proxy)

- **위치와 대상**: 포워드 프록시는 **클라이언트와 인터넷 사이에 위치**하며, **클라이언트의 요청을 대신해서 인터넷의 서버에 전달**한다. 클라이언트의 신원을 대신하여 인터넷에 접근한다.
- **목적**: 주로 **클라이언트의 익명성을 보장**하고, 접근 제어 및 콘텐츠 필터링, **사용자 요청의 캐싱**을 통해 네트워크 트래픽을 감소시키는 데 사용된다.
- **익명성**: **사용자의 실제 IP 주소를 숨기고, 대신 프록시 서버의 IP 주소를 사용하여 웹 요청을 한다**.
- **사용 사례**: 학교, 기업 등에서 인터넷 접속 제어, 사용자의 인터넷 사용 모니터링, 부적절한 콘텐츠 차단 등에 활용된다.

![forward-proxy](/assets/img/post/research/forward-proxy.png){: width=＂700＂ }

### 리버스 프록시 (Reverse Proxy)

- **위치와 대상**: 리버스 프록시는 **인터넷과 서버 사이에 위치**하며, **외부의 요청을 받아 내부 서버(들)로 전달**한다. 이 경우 프록시는 서버의 신원을 대신하여 클라이언트에 응답한다.
- **목적**: 주로 **서버의 보안 강화, 부하 분산, SSL 암호화 처리**, 콘텐츠 캐싱 및 압축을 통해 웹 서비스의 성능과 가용성을 향상시키는 데 사용된다.
- **보안**: 외부로부터의 직접적인 서버 접근을 차단하여 서버의 보안을 강화한다.
- **사용 사례**: **웹 애플리케이션의 부하 분산**, 보안 강화, SSL 오프로딩, 웹 가속화 등에 활용된다.

![reverse-proxy](/assets/img/post/research/reverse-proxy.png){: width=＂700＂ }
