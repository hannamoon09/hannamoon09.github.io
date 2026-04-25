---
title: Studying Classical cipher
published: 2026-04-24
description: "I'm studying Crytography"
image: ''
tags: [Crypto]
category: 'Crypto'
draft: false 
lang: 'ko'
---

## Organize notes

### 고전 암호
    - 설명: 고성능 연산 장치가 발명되기 전에, 비교적 간단한 기계와 손 등으로 암복호화를 수행하던 암호 -> 현대에서는 쉽게 복호화되기 때문에 사용하지 않음

    1. 치환(Substitution) 암호
        - 설명: 평문의 문자를 다른 문자로 바꾸는 것

        1. 단일 문자 치환 암호(Monoalphabetic substitution cipher)
            - 설명: 평문의 각 문자를 약속된 다른 문자로 치환하는 암호
            -> 복호화를 위해 치환의 대응 관계는 일대일 대응

            대표적인 예시: 기원전 44년 줄리어스 카이사르가 사용한 카이사르 암호(Caesar cipher)
            -> 송신자와 수신자가 몇 회만큼 다음 순서의 알파벳으로 치환할지를 사전에 합의해야 통신이 가능함

        2. 다중 문자 치환 암호(Polyalphabetic substitution cipher)
            - 설명: 평문의 한 문자가 암호문에서 여러 종류의 문자로 치환될 수 있음

            대표적인 예시: 비제네르 암호(Vigenere cipher)
                - 각 행에서 평문의 문자에 대응되는 문자로 평문을 치환
![Vigenere](/src/content/posts/Crypto/Vigenere.png)

    2. 전치(Transposition) 암호
        - 설명: 평문 문자들의 위치를 바꾸는 것

        대표적인 예시: 기원전 450년에 고대 그리스인들이 발견한 스키테일 암호(Scytale cipher)
        - 설명: 나무봉(Scytale)을 이용한 암호로, 송신자가 종이 테이프를 나무봉에 감아서 테이프 위에 메세지를 기입하여 암호문을 만들고 수신자는 그 테이프를 받고 동일한 지름의 나무봉에 감아서 이를 해석함

    3. 고전 암호 공격

        1. 전수 키 탐색 공격(Exhaustive key search attack)
            - 설명: 평문과 암호문을 알 때, 키 공간을 전부 탐색하며 주어진 암호문과 같은 암호문을 생성하는 키를 찾는 방법

            -> 굉장히 단순하지만 키 공간의 크기가 작다면 빠른 시간 안에 키를 찾고, 암호를 해독할 수 있음

            -> 단일 치환 암호인 카이사르 암호는 키 공간이 26으로 매우 작기 때문에 전수 키 탐색 공격에 취약

        2. 빈도수 분석(Frequency analysis)
            - 설명: 암호문 내 문자나 문자열의 출현 빈도를 통계적으로 계산해 평문을 유추하는 방법

            -> 암호문이 어떤 언어로 구성되어 있어도 대상 언어의 특성을 안다면 시도해볼 수 있음