---
layout: post
title: "Linux Utility"
date:   2022-07-07 19:41:09
author: dark 
---
Linux 사용 시, 유용한 툴 사용법 정리  

## Contents
> + Network
> + ...  

*last updated: 2022.07.07*

## Network
### tcpdump
tcpdump is a poweful command-line packet analyzer
+ https://www.tcpdump.org/  

#### Example
eth0 인터페이스의 Destination IP: 127.0.0.1, Port: 20000 으로 수신되는 UDP 패킷 캡쳐
```shell
sudo tcpdump -i eth0 udp port 20000 and dst 127.0.0.1
```  
lo(loopbak) 인터페이스를 포함한 모든 인터페이스의 Port: 11124 로 수신되는 TCP 패킷을 캡쳐해서 xxx.pcap 파일로 저장
```shell
sudo tcpdump -i any tcp port 11124 -w xxx.pcap
```

### nping
Nping is an open source tool for network packet generation, response analysis and response time measurement.  
+ https://nmap.org/nping/  

#### Example
Source IP: 127.0.0.1, Port: 20000으로 Destination IP: 185.199.108.153, Port: 65000으로 UDP 패킷 전송
```shell
sudo nping -S 127.0.0.1 -g 20000 --udp 185.199.108.153 -p 65000
```  

## Reference
> + ...
> + ...
