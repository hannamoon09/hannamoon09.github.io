---
title: Tools for Modern Cryptography
published: 2026-04-25
description: "I'm studying Cryptography"
image: ''
tags: [Study]
category: 'Crypto'
draft: false 
lang: 'ko'
---

## Organize notes

### About PyCryptodome
    - AES, DES, RSA와 같은 암호뿐만 아니라 소수 판별과 같은 기능을 가진 수학 함수들이 구현되어 있어 유용하데 사용됨

    -> 사용 시에는 용도에 따라 from Crypto.Ciper import AES, from Crypto.Util.number import *과 같이 불러오는 방법이 다름

### About SageMath
    - SageMath, 또는 Sage는 CAS(Computer algebra system)라고도 불리는 컴퓨터용 수학 소프트웨어 중 하나임

    -> Zmod와 GF, 행렬과 벡터 클래스, 행렬 관련 함수를 자주 사용됨

    -> Python에 설치된 패키지와 SageMath에 설치된 패키지는 개별적임(pip 패키지 설치를 개별적으로 해줘야함)

    -> Python에서 ^ 연산자는 xor을 의미하지만, SageMath 셸에서는 거듭제곱, 즉 **과 같은 기능을 가짐
        - XOR 연산은 ^^을 이용함

## 번외
    **tqdm은 아주 유용한 모듈**
    - 이유: 암호학을 포함한 해킹의 대부분의 분야는 가끔 많은 양의 연산이 필요함. 그래서 tqdm이 진행도 표시 및 예상 시간을 표시해줌