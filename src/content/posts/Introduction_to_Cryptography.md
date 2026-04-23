---
title: Introduction to CryptoGraphy
published: 2026-04-22
description: "I'm studying Cryptography"
image: ''
tags: [Crypto]
category: 'Study'
draft: false 
lang: 'ko'
---

## Crypto Studying
```markdown
**Date**: 2026-4-21 ~ Current
**Reffer**: Dreamhack
```

## Organize notes
```markdown
## About pwntools
1. 연결을 맺는 함수
    - 통신을 위해선 연결을 맺어야함. 다음 설명하는 함수들이 성공적으로 실행되면 *pwnlib.tubes*클래스를 반환함
    - **pwnlib.tubes**: 데이터를 주고받을 수 있는 다양한 함수들이 구현되어 있어 이후 편리하게 데이터를 송수신할 수 있음

    1. process()
        - 역할: 로컬에 위치한 프로그램을 실행하여 통신할 때 사용하는 함수 -> 인자를 전달하거나 환경 변수를 설정하여 통신할 수 있음
    2. remote()
        - 역할: 호스트의 도메인 혹은 IP 주소와 포트 번호를 인자로 받아 원격 서버에 통신할 때 사용되는 함수 -> 기본적으로 TCP로 연결함(typ인자로 UDP 전달 가능)
    3. ssh()
        - 역할: SSH 서버에 접속하여 통신하기 위해 사용함 -> ssh("사용자 이름", "호스트", port=포트, password=패스워드)

2. 데이터 송수신 함수
    1. recv() 예시
        1. p.recv(n) -> p가 출력하는 데이터를 최대 n 바이트까지 받음 # 여기서 p는 process를 의미
        2. p.recvline() -> p가 출력하는 데이터를 개행문자를 만날 때까지 받음
        3. p.recvn(n) -> p가 출력하는 데이터를 n 바이트만 받음
        4. p.recvuntil(b'hello') -> p가 b'hello'를 출력할 때까지 데이터를 수신하여 data에 저장
        5. p.recvall() -> p가 출력하는 데이터를 프로세스가 종료될 때까지 받음
    - recv()와 recvn()의 차이점: recv(n)은 *최대 n 바이트를 받는 함수*로 그만큼의 데이터를 받지 못해도 당장 받을 수 있는 만큼 수신한 뒤 종료하는 반면, recvn(n)의 경우 *정확히 n 바이트를 받는 함수*로 그만큼의 데이터를 받지 못하면 계속 기다림

    2. send() 예시
        1. p.send(b'A') -> p에 b'A'를 입력 # 여기서 p는 process를 의미
        2. p.sendline(b'A') -> p에 b'A' + b'\n'을 입력
        3. p.sendafter(b'hello', b'A') -> p가 b'hello'를 출력하면, b'A'를 입력
        4. p.sendlineafter(b'hello', b'A') -> p가 b'hello'를 출력하면, b'A' + b'\n'을 입력
    - sendafter()와 sendlineafter()를 실행한 뒤에 데이터 수신 함수들로 데이터를 수신할 경우 sendafter()와 sendlineafter()에서 *수신한 데이터 이후의 데이터부터 수신*하게 됨

    3. interactive() 예시
        1. p.interactive() -> 실시간으로 데이터를 송수신할 수 있음
    - send(), recv() 관련 함수들처럼 pwnlib.tubes 클래스에 구현된 함수임 -> 연결 함수가 필요함(process(), remote())

3. 연결을 종료하는 함수
    - 데이터 송신 및 수신을 완료했다면 연결을 종료해야함. 연결된 두 프로세스 중 어느 한 프로세스가 연결을 종료한다면 해당 연결은 종료 됨
    - 프로세스와 통신할 때 내가 연결을 종료할 수 있지만, 통신하고 있는 상대 프로세스가 연결을 종류할 수 있음

    1. close() 예제
        1. p.close() -> 실행되는 순간에 연결이 유지되고 있는 상태여야 함
        - p.close()가 실행되면 pwnlib.tubes 클래스인 p 객체 내부의 자원이 정리되어 이후 send()나 recv() 등을 호출하면 에러 발생
        - interactive()를 호출한 경우 함수가 종료될 때 연결이 같이 종료되기에 close() 함수를 추가로 사용할 필요 없음
    - send(), recv() 그리고 interactive()와 동일하게 pwnlib.tubes에 클래스에 구현된 함수임(내가 연결을 종료하고 싶을 때 사용)

4. 로그 출력
    - context.log_level을 이용해 로그 출력의 상세도를 설정할 수 있음
    
    1. context.log_level 종류
        1. critical -> 치명적인 오류 외에 출력하지 않음
        2. error -> 에러 메시지만 출력
        3. warning/warn -> 경고 메시지 출력
        4. info -> 일반적인 상태 메시지 출력
        5. debug -> 송수신 데이터, 내부 변수 등 상세히 출력
    - context.log_level을 따로 설정 안하면 info로 설정됨

5. Packing & Unpacking
    - 프로그래밍에서 패킹(Packing)과 언패킹(Unpacking)은 데이터를 하나의 형태로 모아 포장하거나, 다시 분해하는 것을 의미함
    - pwntools의 기능에서 정수 값을 bytes 클래스로 변환하거나 그 반대의 행위를 하는 기능이 함수로 구현되어 있고, 이를 패킹과 언패킹이라고 표현함

    1. 패킹 함수
        - p8(), p16(), p32(), p64() -> 함수명 뒤에 붙은 숫자는 패킹을 수행할 때 bytes 클래스의 비트 수를 의미함
    2. 언패킹 함수
        - u8(), u16(), u32(), u64() -> 함수명 뒤에 붙은 숫자는 패킹을 수행할 때 bytes 클래스의 비트 수를 의미함
    - 패킹 및 언패킹 함수는 기본적으로 리틀 엔디안으로 동작함(endian='big'으로 빅 엔디안 사용 가능)
```