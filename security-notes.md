---
layout: page
title: "Security Notes"
permalink: /security-notes
---

# Security Notes

정보보안 실습 및 이론을 정리하는 페이지입니다.  
**네트워크 보안 / 웹 보안 / 포렌식**을 중심으로, 약술·서술형 대비용 표와 간단한 구조도를 함께 정리합니다.

---

## 1. 네트워크 보안 실습 정리

### 1-1. 네트워크 분석 도구별 정리

| 구분 | 도구 | 주요 용도 | 핵심 포인트 |
|------|------|-----------|-------------|
| 패킷 분석 | Wireshark | 패킷 캡처, 프로토콜 분석, 세션 재구성 | 특정 세션(TCP 스트림) 추출 → 평문 노출 여부, 이상 플래그 확인 |
| 침입 탐지 | Snort | 시그니처 기반 NIDS, 룰 기반 탐지 | 정상 트래픽 패턴 이해 후 룰 튜닝, 오탐/미탐 관리 |
| 포트 스캔 | nmap | 서비스/포트 열림 상태 진단 | 스캔 타입(TCP SYN, UDP 등)에 따른 탐지 가능성 차이 이해 |
| 로그 분석 | Linux syslog 등 | 시스템/서비스 로그 확인 | 시간 동기화, IP/계정/프로세스 흐름을 한 줄로 엮기 |

### 1-2. 간단 네트워크 구조도

```mermaid
flowchart LR
    Client[사용자 단말] --> FW[방화벽]
    FW --> IDS[IDS / NIDS]
    IDS --> Web[웹 서버]
    IDS --> Log[로그 서버 / SIEM]

    subgraph Monitoring
      IDS
      Log
    end
