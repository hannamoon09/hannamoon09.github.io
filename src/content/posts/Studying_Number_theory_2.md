---
title: Studying Number theory 2
published: 2026-04-26
description: "I'm studying Number theory"
image: ''
tags: [Crypto, Math]
category: 'Crypto'
draft: false 
lang: 'ko'
---

## Organize notes

### 정수론 2
- 설명: 페르마의 정리(Fermat's little theorem)와 오일러 정리(Euler's theorem)의 정수론과 암호악에 있어 빼놓을 수 없는 중요한 정리임
    - RSA 공개키 암호, DSA 전자 서명 등의 많은 정수론을 사용한 암호학적 시스템이 이 정리들에 기반함

    1. **페르마의 소정리**(Fermat's little theorem)
        - 위치(position): 소수(Prime number)가 가지는 여러 중요한 성질 중 하나에 관한 정리

        - 설명: 소수 p, 그리고 p와 서로소인 정수 a에 대하여 a<sup>p-1</sup> ≡ 1 (mod p)를 만족함
            - p가 소수이기 때문에 a가 p인 소로소인 조건은 a가 p의 배수가 아니기만 하면 됨. 달리말해, p를 modulus로 하였을 때, 0이 아닌 나머지 p - 1가지 의 모든 수 a에 대하여 a<sup>p-1</sup> ≡ 1 (mod p)가 성립함