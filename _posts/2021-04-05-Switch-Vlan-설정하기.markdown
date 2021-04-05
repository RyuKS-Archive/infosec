---
layout: post
title:  "Vlan 설정"
description: Switch Vlan 설정하기
date:   2021-04-05
categories: Switch Vlan
---

# Vlan 설정하기     

1. PC와 스위치가 연결된 포트 확인
> CLI에서 show ip interface brief로도 연결 포트 확인가능
2. CLI에서 enable - configure terminal 입력 후 설정모드로 전환
3. interface [range(이어진 여러포트 일괄 설정시 사용)] fastEthernet [포트 ex) 0/1, 0/1-2(range)]
4. switchport mode access - switchport access vlan [번호] 
> 번호에 해당하는 vlan이 없으면 자동으로 생성
    
    
    
# 스위치간 통신시 Vlan정보는 넘겨주기 위한 trunk 설정
    
1. 다른 스위치와 연결되어 있는 포트 확인
> CLI에서 show ip interface brief로도 연결 포트 확인가능
2. CLI에서 enable - configure terminal 입력 후 설정모드로 전환
3. interface fastEthernet [스위치간 연결 포트 ex) 0/1]
> 포트가 연속적일 경우 range 옵션 사용 가능
4. switchport mode trunk
    
    
    
# 스위치는 다르지만 같은 Vlan으로 설정이 된 PC들 간의 통신
    
1. 스위치에 연결된 PC1, 2, 3을 각각 Vlan 설정하기로 Vlan 10, 20, 30로 설정
2. 스위치간 포트 모드를 trunk로 하여 Vlan 정보를 넘겨 받을 수 있게 설정
3. 하나의 스위치가 모든 Vlan의 루트 브릿지가 되어서 부하가 걸리지 않도록 루트 브릿지 분배 설정
> 부하가 걸리지 않도록 루트 브릿지를 나누는 것을 "로드쉐어링"이라고 한다.
4. 각 스위치의 CLI에서 enable - show spanning-tree로 Vlan 루트 브릿지를 확인한다
5. 하나의 스위치가 모든 Vlan의 루트 브릿지가 되지 않도록 각 스위치의 BUID의 Priority 값을 0으로 설정한다
> 각 스위치 CLI - enable - configure terminal - spanning-tree vlan [번호] priority 0 
6. 같은 vlan 소속 PC간 통신이 가능한지 ping 테스트
    
    
    



