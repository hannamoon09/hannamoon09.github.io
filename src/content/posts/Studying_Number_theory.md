---
title: Studying Number theory
published: 2026-04-26
description: "I'm studying Number theory"
image: ''
tags: [Crypto, Math]
category: 'Crypto'
draft: false 
lang: 'ko'
---

## Organize notes

### 정수론
- 설명: 수학의 한 분야로, 정수와 관련된 다양한 성질을 다루는 학문
    - 암호학에서 사용되는 정수론에서는 모든 자연수나 정수 범위보다도, 특정 값으로 나누는 나머지 연산이 높은 비중을 차지함

    1. **유클리드 알고리즘**(Euclidean algorithm) 혹은 유클리드 호제법
        - 소인수분해 과정 없이도 두 수의 최대공약수(Greatest Common Divisor, GCD)를 구할 수 있음

        - 다음과 같은 사실을 기반으로 함
            1. a > b인 양의 정수 a, b에 대하여 a를 b로 나눈 나머지를 r로 정의하면, a, b의 최대공약수와 b, r의 최대공약수는 동일하다.
            2. a > 0일때, a, 0의 최대공약수는 a로 정의된다.

    2. **확장 유클리드 알고리즘**(Extended Euclidean algorithm)
        - 