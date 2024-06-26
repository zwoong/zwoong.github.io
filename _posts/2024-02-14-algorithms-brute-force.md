---
layout: post
title: 브루트 포스(brute-force)
tags: [알고리즘, 브루트 포스(brute-force)]
categories: [알고리즘, 브루트 포스(brute-force)]
image:
  path: /assets/img/post/algorithm/brute-force.png
  alt: brute-force
date: 2024-02-14 15:02 +0900
---

## 브루트 포스(brute force)

브루트 포스(brute force)는 컴퓨터 과학에서 **문제를 해결하기 위해 가능한 모든 후보 해를 하나씩 대입하고 검사하는 방법**이다. 이는 일반적으로 모든 가능한 경우의 수를 탐색하여 원하는 결과를 찾는 데 사용된다. 브루트 포스 알고리즘은 단순하고 직관적이지만, 경우에 따라 성능이 나쁠 수 있다. 하지만 경우에 따라서는 최적의 해를 보장하는 강력한 방법이 될 수 있다.

### 특징

- **완전 탐색**: 브루트 포스는 **가능한 모든 후보 해를 탐색하여 문제를 해결**한다. 따라서 모든 가능한 경우의 수를 고려한다.
- **직관적인 구현**: 알고리즘이 **단순하고 직관적**이기 때문에 이해하고 구현하기가 쉽다.
- **보장된 결과**: 브루트 포스는 **모든 가능한 후보 해를 탐색하므로 최적의 해를 보장**한다. 그러나 이는 종종 시간과 공간이 많이 소요되는 단점으로 이어질 수 있다.
- **시간 복잡도**: 경우에 따라 브루트 포스는 **지수적인 시간 복잡도를 갖는다**. 따라서 입력 크기가 큰 경우에는 효율적인 해결책이 될 수 없다.

## brute-force attack

무차입 대입 공격(브루트 포스 공격, Brute Force Attack)은 컴퓨터 보안에서 **사용자의 계정이나 시스템의 비밀번호를 찾아내기 위해 가능한 모든 조합을 시도하는 공격 기법**이다. 이 공격은 매우 단순하고 직접적이지만, 비밀번호가 강력한 경우에도 성공할 수 있다.

- **대상 식별**: 공격자는 대상 시스템을 식별하고, 대상 시스템에 접근하기 위해 사용자 이름 또는 계정을 식별한다.
- **대입 공격**: 공격자는 **가능한 모든 조합의 비밀번호를 시도하여 대상 시스템에 액세스하려고 한다**. 이때, 대상 시스템이나 인증 서버는 대량의 로그인 시도를 감지하고 차단할 수 있다. 그러나 공격자는 이를 피하고자 대량의 로그인 시도를 다양한 IP 주소를 사용하여 분산시키거나, 일정 시간 간격을 두고 시도하는 등의 방법을 사용할 수 있다.
- **성공 또는 실패**: 공격자가 올바른 비밀번호를 찾으면, 해당 계정으로 로그인할 수 있다. 그렇지 않으면, 계속해서 다른 조합을 시도하게 된다.

```python
# 대상 시스템에 대한 사용자 이름과 비밀번호
target_username = "target_user"
target_password = "100000"

# 반복 횟수 초기화
iteration_count = 0

while True:
    for password_num in range(iteration_count, iteration_count + 10000):
        password_str = str(password_num).zfill(4)

        if password_str == target_password:
            print(f"비밀번호 찾음! 사용자 이름: {target_username}, 비밀번호: {password_str}")
            break
    else:
        iteration_count += 10000
        print(f"비밀번호를 찾지 못했습니다. 현재까지의 반복 횟수: {iteration_count}")
        continue

    break
```

### brute-force attack 방지 조치

- **강력한 비밀번호 정책 적용**: 사용자에게 **강력한 비밀번호를 설정하도록 요구**하고, 비밀번호는 길이가 길고 다양한 문자와 기호를 포함해야 한다. 이를 통해 공격자가 비밀번호를 추측하는 데 더 많은 시간과 노력이 필요하게 된다.
- **계정 잠금**: **일정 시간 동안 여러 번의 로그인 실패 시도가 있으면 계정을 일시적으로 잠그는 기능을 구현**한다. 이렇게 하면 공격자가 대규모로 비밀번호를 시도하여 무차입 공격을 할 때 계정이 잠기게 된다.
- **CAPTCHA 또는 reCAPTCHA 사용**: 로그인 시도 시 CAPTCHA(Completely Automated Public Turing test to tell Computers and Humans Apart) 또는 reCAPTCHA와 같은 **자동화 방지 기능을 사용하여 봇 또는 자동화된 스크립트에 의한 공격을 방지**한다.
- **2단계 인증(2FA)**: 사용자가 로그인할 때 **두 단계의 인증(비밀번호 입력 후 추가 인증 수단 필요)을 통해 보안을 강화**한다.
- **IP 차단**: 일정 시간 동안 동일한 IP 주소에서 너무 많은 로그인 시도가 있으면 해당 IP 주소를 차단한다.
