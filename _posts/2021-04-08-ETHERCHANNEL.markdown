---
layout: post
title:  "Etherchannel 설정"
description: L3스위치 간 Etherchannel 설정
date:   2021-04-08
categories: telnet subnet
---
    
    
# Etherchannel 설정
+ 두 개의 케이블로 연결하여 속도와 안전성을 갖추는 방법
+ L3스위치 A와 L3스위치 B의 fastEthernet 0/23-24 크로스케이블 2개를 연결하는 것을 예시로 상정하여 설정 설명
    
### L3스위치 A    
1. configure terminal - interface range fastEthernet 0/23-24
2. no switchport - channel-group [채널이름] mode desirable (동기화 반드시 필요)
3. exit - interface port-channel [채널이름]
4. ip address [포트 ip지정] [서브넷] - no sh 

+ ip 라우팅 설정과 같은 의미라고 생각하면 됨 포트 2개를 하나의 채널 그룹으로 묶어 ip를 지정해 주는 작업

### L3스위치 B
1. A와 같은 방법으로 설정하고 채널이름을 같게 해줘야 함,  당연히 포트 ip는 다르게 설정
2. ping 테스트
