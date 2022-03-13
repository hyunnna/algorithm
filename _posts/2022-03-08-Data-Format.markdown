---
layout: post
read_time: true
show_date: true
title:  Data Format
date:   2022-03-09 19:12:32 -0600
description : The second week study of cloud computing.
img: posts/202203/data.jpg
tags: [cloud computing, data]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading

# toc: yes # leave empty or erase for no TOC
---

## Data Format

+ #### 정형 데이터 (Structured Data)
* ##### 관계형 데이터처럼 Schema에 따라 저장된 구조화된 데이터
* ##### 일반적으로 Table 형식으로 RDBMS에 저장 (예: 은행 계좌 정보등의 데이터)

+ ##### 비정형 데이터(Unstructured Data)
* ##### Schema나 데이터 모델 없이 저장되는 데이터 (일반 텍스트나 사진, 동영상)


+ ##### 반정형 데이터 (Semi-Structured Data)
* ##### 고정된 필드를 가지고 있지는 않고 관계형 데이터 아님
* ##### 데이터에 스키마나 메타에이터와 같은 구조 정보를 포함하고 있어 일관성유지
* ##### 계층적, 그래프 기반의 데이터( XML, HTML 문서 / JSON, BSON 형태의 데이터)

------------

XML (eXtensivle Markup Language)
구조화된 문서를 네트워크 환경에서 전송 및 활용 가능하도록 설계된 표준 마크업 언어
ISO SGML의 서브셋(subset)
장점 
호환성 : 국제 표준 규약
독립성 
HW, OS , 프로그래밍 언어에 독립
서로 다른 네트워크 환경에서 유용
구조화
활용성
확장성
분석 성능 
단점 : 오버헤드
