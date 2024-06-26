---
layout: post
title: 컴퓨터가 문자를 이해하는 방법
tags: [컴퓨터 구조, 컴퓨터가 문자를 이해하는 방법]
categories: [컴퓨터 구조, 컴퓨터가 문자를 이해하는 방법]
image:
  path: /assets/img/post/computer-architecture/number-word.jpg
  alt: number-word
date: 2023-11-28 22:44 +0900
---

컴퓨터는 0과 1로만 모든 정보를 표현하고, 이해할 수 있다고 하는데, 문자는 어떻게 이해하는 걸까? <br>
오늘은 컴퓨터가 문자를 이해하는 방법에 대해 알아보자. 😉

## 문자 집합

컴퓨터에서의 문자 집합(character set)은 **컴퓨터가 텍스트 데이터를 표현하고 조작하는 데 사용하는 문자의 집합**을 말한다. <br>
문자 집합은 **컴퓨터가 문자를 숫자(컴퓨터는 0과 1로 표현되는 데이터인 이진 데이터를 이해하고 처리하도록 설계되었기 때문에)로 매핑(mapping)하여 저장하고 처리**할 수 있도록 한다.

## 문자 집합의 종류

### ASCII (American Standard Code for Information Interchange)

- ASCII는 **가장 기본적인 문자 집합으로, 영문 알파벳, 숫자, 특수 문자 등 128개의 문자를 포함**한다.
- 각 문자는 7비트로 표현되며, 0에서 127까지의 코드 값을 가진다.
- ASCII는 초기 컴퓨터 시스템과 인터넷에서 널리 사용되었다.

### ISO 8859

- ISO 8859는 **ASCII를 확장하여 다양한 언어를 지원**한다. 이 집합은 여러 부분으로 나뉘며, 각각 다른 언어 그룹을 지원한다. (예: ISO 8859-1은 서유럽 언어를 지원)
- ISO 8859는 각 문자를 8비트(1바이트)로 표현한다.

### Unicode❗️

- Unicode는 **전 세계의 모든 문자를 포함하는 광범위한 문자 집합**이다.
- Unicode는 다양한 언어와 기호, 이모티콘 등을 포함하여 10만 개 이상의 문자를 지원한다.
- Unicode는 UTF-8, UTF-16, UTF-32 등 다양한 인코딩 방식으로 구현된다.

> ASCII는 미국 즉, 영어만을 고려한 문자 집합이며, ISO 8859는 그런 ASCII를 확장해서 서유럽 언어까지 지원하는 언어이다. <br>
> 여기서 제일 중요한 것은 **전 세계의 거의 모든 문자를 지원하는 Unicode**이다. <br>
> 현대의 컴퓨터 시스템, 소프트웨어, 인터넷 기술에서는 대부분 Unicode를 기본 문자 집합으로 채택하고 있다.

#### UTF-8 (8-bit Unicode Transformation Format)

- **가변 길이**: UTF-8은 가변 길이 문자 인코딩이다. 문자를 표시하기 위해 1~4바이트를 사용할 수 있으며, 사용되는 바이트 수는 인코딩되는 문자에 따라 다르다.
- **ASCII 호환성**: UTF-8은 ASCII 문자를 1바이트로 인코딩하며, ASCII 코드와 완전히 호환된다. 이는 영문 텍스트에 대해 매우 효율적이다.
- **국제적 사용에 적합**: 다양한 언어와 특수 문자를 효율적으로 인코딩할 수 있으며, 웹과 이메일을 비롯한 많은 인터넷 기술에서 널리 사용된다.
- **저장 공간 효율성**: **영문자는 1바이트, 유럽 및 중동 언어는 대부분 2바이트, 아시아 언어는 주로 3바이트를 사용**한다. 🫢

#### UTF-16 (16-bit Unicode Transformation Format)

- **가변 길이**: UTF-16도 가변 길이 인코딩이지만 가장 일반적인 문자에 2바이트를 사용하고 추가 문자(BMP 내에서 표현되지 않는 문자)에 4바이트를 사용한다.
- **ASCII의 경우 효율성이 낮음**: 주로 ASCII로 작성된 텍스트의 경우 **UTF-16은 문자당 최소 2바이트를 사용하므로 UTF-8보다 효율성이 떨어진다**.

#### UTF-32

- **고정 길이**: UTF-32는 모든 문자에 4바이트를 사용하는 **고정 길이 인코딩**이다. 모든 문자의 길이가 동일하므로 인덱싱 및 문자 처리 측면에서 더 간단해진다.
- **메모리 사용량**: **UTF-32는 모든 문자에 4바이트를 사용하기 때문에 이 세 가지 중에서 메모리 효율성이 가장 낮다**. 특히 대부분의 문자가 더 적은 바이트로 표시될 수 있는 영어와 같은 언어의 텍스트에서는 더욱 그렇다.
- **단순성**: **UTF-32의 주요 장점은 단순성**이다. 각 유니코드 문자는 단일 32비트 코드 단위에 해당하며, 가변 길이 문자를 처리할 필요가 없으므로 특정 텍스트 처리 작업이 단순화될 수 있다.
- **용도**: UTF-32는 **공간 요구 사항이 높기 때문에 실제 응용 프로그램에서는 일반적으로 덜 사용된다**. 특정 텍스트 처리 알고리즘이나 개별 문자에 대한 빠른 액세스가 필요한 메모리 내 데이터 구조와 같이 고정 길이 문자의 단순성이 메모리 비효율성보다 중요한 상황에서 더 자주 발견된다.

> 이제 우리는 기본적인 문자 집합에 대해 알게 되었다! 😉 <br>
> 위에서 **인코딩**이라는 문자가 반복적으로 등장하고 있는데, 사실 **문자 집합만 가지고는 컴퓨터가 문자를 이해할 수 없다**. 문자를 결국 0과 1로 변환해야 컴퓨터가 이해할 수 있는데, 이 변환 과정을 **문자 인코딩**(character encoding)이라고 하며, 반대로 사람이 이해할 수 있는 문자로 변환하는 과정을 **문자 디코딩**(character decoding)이라고 한다.

### 문자 인코딩(character encoding)

문자 인코딩은 **효율적인 저장 및 전송을 위해 문자 세트(예: 문자, 숫자, 기호)를 특정 형식으로 변환하는 프로세스**다. 이 프로세스에는 **각 문자에 고유 번호(코드 포인트)를 할당**한 다음 이러한 숫자를 컴퓨터가 저장하고 조작할 수 있는 이진 형식으로 나타내는 작업이 포함된다.

- **이진 형식**: 0과 1로 표시되는 두 가지 상태만을 사용하여 데이터를 표현하는 방법을 의미하며, 컴퓨팅에서 이 이진 형식은 컴퓨터가 정보를 저장하고 처리하는 기본 언어이다.
- **코드 포인트**: 인코딩 체계에서 각 문자는 코드 포인트에 매핑된다. 예를 들어, ASCII(American Standard Code for Information Interchange)에서 문자 'A'는 코드 포인트 65에 매핑된다.

### 문자 디코딩(character decoding)

문자 디코딩은 인코딩의 역과정으로서, 사용된 문자 인코딩 규칙에 따라 이진 데이터를 다시 문자로 변환하는 작업이 포함된다.

- **올바른 인코딩의 중요성**: 정확한 디코딩을 위해 시스템은 어떤 인코딩이 사용되었는지 알아야 한다. 인코딩을 알 수 없거나 잘못 가정한 경우 디코딩된 텍스트가 왜곡되어 읽을 수 없게 될 수 있다.

> 마지막으로 ASCII 문자 집합을 이용해 `hello`라는 문자를 인코딩하는 과정을 확인해 보자!

![ascii-character-set](/assets/img/post/computer-architecture/ascii-character-set.png){: width="600" }

1. **문자 매핑**: "hello"라는 단어의 각 문자는 해당 ASCII 값에 매핑된다. ASCII는 각 문자에 고유한 번호를 할당한다. <br>
   예를 들어 'h'는 104, 'e'는 101, 'l'은 108, 'o'는 111이다.
2. **이진 변환**: 이 숫자는 이진수로 변환된다. <br>
   'h' (10진수 104) -> 2진수 0110 1000 <br>
   'e' (10진수 101) -> 2진수 0110 0101 <br>
   'l' (10진수 108) -> 2진수 0110 1100 <br>
   'l' (10진수 108) -> 2진수 0110 1100 <br>
   'o' (10진수 111) -> 2진수 0110 1111
3. **연결**: 그런 다음 이 이진 시퀀스를 연결하여 "hello"의 이진 표현을 형성한다. <br>
   `0110 1000` `0110 0101` `0110 1100` `0110 1100` `0110 1111`
