---
layout: post
title:  "IP 라우팅 (Static)"
description: Static 방식의 IP 라우팅
date:   2021-04-06
categories: routing
---
    
    
# IP 라우팅 (Static)
    
1. L2스위치와 연결된 L3스위치2, 3 포트 설정
```
configure terminal - interface fastEthernet 0/21 (& 0/22)
no switchport - ip address 1.1.1.1 (& 2.2.2.1) 255.255.255.0 - no sh
```
2. L3스위치1 설정
```
configure terminal - interface [L3스위치 2, 3과 연결된 포트]
no switchport - ip address 1.1.1.2 (& 2.2.2.2) 255.255.255.0 -no sh
```
3. ping 1.1.1.1 (& 2.2.2.1) 테스트
4. L3스위치1 라우팅 테이블 설정 (최대 65503)
```
configure terminal - ip route 192.168.1.0 255.255.255.0 1.1.1.1
                     ip route 192.168.2.0 255.255.255.0 1.1.1.1
                     ip route 192.168.3.0 255.255.255.0 2.2.2.1
                     ip route 192.168.4.0 255.255.255.0 2.2.2.1
```
5. show ip route 확인
6. L3스위치2, 3 디폴트 경로 설정
```
configure terminal - ip route 0.0.0.0 0.0.0.0 1.1.1.2 (& 2.2.2.2) 
```
7. PC에서 ping 테스트
    
    
# 라우팅 테이블 서머리
    
+ PC ip 서브넷 마스크를 255.255.252.0으로 설정
> ex) L3스위치2에 연결된 pc는 192.168.0.0/22 
>     L3스위치3에 연결된 pc는 172.16.0.0/22

+ 위와 같이 네트워크를 구성했을시 IP 라우팅 (Static) 4번 설정을 아래와 같이 간략하게 할 수 있어 라우팅 부하를 덜어 줌
```
configure terminal - ip route 192.168.0.0 255.255.252.0 1.1.1.1
                     ip route 172.16.0.0 255.255.252.0 2.2.2.1
```
