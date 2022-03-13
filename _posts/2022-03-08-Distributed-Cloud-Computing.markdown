---
layout: post
read_time: true
show_date: true
title:  Distributed Cloud Computing
date:   2022-03-09 19:12:32 -0600
description : Distributed Cloud Computing Class
img: posts/202203/data.jpg
tags: [Distributed Cloud Computing , Senior]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading

# toc: yes # leave empty or erase for no TOC
---
# <span style="color:Khaki"> **1. Data Format**  </span>  

 ### **정형 데이터 (Structured Data)**
* #### 관계형 데이터처럼 Schema에 따라 저장된 구조화된 데이터
* #### 일반적으로 Table 형식으로 RDBMS에 저장 (예: 은행 계좌 정보등의 데이터)

 ### **비정형 데이터(Unstructured Data)**
* #### Schema나 데이터 모델 없이 저장되는 데이터 (일반 텍스트나 사진, 동영상)


 ### **반정형 데이터 (Semi-Structured Data)**
* #### 고정된 필드를 가지고 있지는 않고 관계형 데이터 아님
* #### 데이터에 스키마나 메타에이터와 같은 구조 정보를 포함하고 있어 일관성유지
* #### 계층적, 그래프 기반의 데이터( XML, HTML 문서 / JSON, BSON 형태의 데이터)  
<br />

### **XML (eXtensivle Markup Language)**  

* 구조화된 문서를 네트워크 환경에서 전송 및 활용 가능하도록 설계된 표준 마크업 언어
* ISO SGML의 서브셋(subset)  

    +  장점   
        * 호환성 : 국제 표준 규약  
        * 독립성   
        + HW, OS , 프로그래밍 언어에 독립  
        + 서로 다른 네트워크 환경에서 유용  
        + 구조화  
        + 활용성
        + 확장성  
        + 분석 성능

    <br /> 

    + 단점   
     오버헤드 (large size)  
<br /> 

### **JSON (JavaScript Object Notation)** 

+ JavaScript 언어의 객체 사용방식
+ 데이터 교환을 위한 표현 방식  
    + XML 대비 경량 (small size) : 저장 및 전송 고속화
    + 개방형 표준 포맷  
        - AJAX에 활용  
+ 장점  
    + 사람, 기계 모두 읽고 쓰기 용이  
    + 프로그래밍 언어나 플랫폼에 독립적  
    + Javascript 문법 채용
        + eval() 함수로 처리 가능
        + 대부분의 웹브라우저가 JASON parser 내장  
    + 형식  
        + object - {"key2" : value, "key 2" : value}
        + value : 기본 자료형 (number, string, true , false, null) 및 array, object가능  
        + array - [a, b, c]  
 
### **BSON (Binary javaScript Object Notation)**  
<br />

+ Binary JSON  
    + 이진형식의 JOSN(text -> binary)
    + 데이터 교환을 위한 표현방식  
    + MongoDM 의 primary data format (데이터 저장 및 네트워크 전송용)  
    + 특징   
        + Lightweight : minimum overheads (small size)  
        + Traversal : designed to be traversed easily (vital property : MongoDB)  
        + Efficient : 대부분 프로그램 언어의 data type으로 빠르게 변환 가능  
        <br />

***
<br />

# <span style="color:Khaki"> **2. SOAP**  </span> 

* **개요**   
분산 환경에서 애플리케이션 간의 정보를 교환하기 위한 XML 기반의 메시지 프로토콜  

* **목적**  
    * 상호 운영성 Interoperability)  
    * 서로 다른 플랫폼에서 구현된 컴포넌트를 통합 할 수 있는 표준 프로토콜  

* **특징** 
    * XML 기반으로 구현 언어 및 플랫폼에 독립적  
     * 필요에 따른 확장 가능 구조  
    * HTTP 프로토콜을 이용하므로 방화벽에 차단되지 않음  
<br />

* ## **SOAP 메시징 구조**  

   ![구조](https://t1.daumcdn.net/cfile/tistory/1311C6184C8DD6BA5E)  

    ### **<span style="color: #000; background-color: LemonChiffon">SOAP의 루트 엘리먼트 <env:Envelope> </span>**  

    - SOAP 메시지의 최상위 엘리먼트 , <env:Header>, <env:Body> 엘리먼트를 포함  
    <br />
    ### **<span style="color: #000; background-color: LemonChiffon">SOAP Header </span>** 
    - <env:Envelope> 의 하위 엘리먼트  
    - 선택적으로 사용될 수 있ek.
    - SOAP 메시지를 처리하는데 필요한 추가 정보를 기술 (인증 정보, 세션, 트랜젝션)  
    - SOAP Header에 사용되는 두가지 attribute  
        + mustUnderstand attribute
        + actor attribute  
    ```java
    <env: Envelope xmlns:env="http://schemas.xmlsoap.org/soap/envelope/">  
        <env:Header>  
            * <t:Transaction xmlns:t="http://example.org/2022/03/tx"> 5 </t:Transaction>
        <env:Header> *
        ...SOAP Body...  
    </env:Envelope>  

   ```

    ### **<span style="color: #000; background-color: LemonChiffon">SOAP Attribute </span>**  

    + **용도**  
        해당 Header 블록을 누가 처리해야 하는지를 지정하는 attribute  

    + 처리   
        + **actor attribute가 지정된 경우**  
            : actor attribute에 지정된 노드가 SOAP Header 블록을 처리  
        + **actor attribute가 지정 되지 않았을 경우**  
            : SOAP 메시지의 최종 수신자가 처리  
    <br />

    ### **<span style="color: #000; background-color: LemonChiffon">mustUnderstand Attribute </span>**  

    + **용도**  
        Header에 포함된 내용이 반드시 처리되어야 하는지 지정하기 위한 attribute  

    + **attribute 값**
        + **값이 1일 경우**  
            : 반드시 처리 해야한다.
        + **값이 0일 경우**  
            : Header 정보를 처리하지 않아도 무방하다.  
<br />

    #### **<span style="color: #000; background-color: LemonChiffon">SOAP Body </span>**  

    + **<env:Body> element**  
        웹 서비스를 이용하기 위한 실제 메시지를 기술
    + **내용**   
        + 서비스 호출과 응답에 관련된 내용을 기술 
        + 웹 서비스가 수행된 후 에러가 있을 때 SOAP Fault를 기술  
    <br />

    #### **<span style="color: #000; background-color: LemonChiffon">SOAP Error Message </span>**  

    + **<env:Fault> element**  
        SOAP 문서의 처리시 에러가 발생할 경우 에러의 내용을 기술하기 위한 element

<br />

* ## **SOAP Encoding**  
    : 자바에서 사용되는 데이터 타입과 SOAP 메시지에 사용되는 데이터 타입 간의 변환 과정  
<br />

* ## **SOAP Binding**  
    + SOAP 메시지를 어떤 프로토콜을 사용해서 전송할 것인지 지정하는 것  
    + SOAP 메시지는 HTTP,FTP,SMTP 등 여러가지 프로토콜 이용가능 (기본적으로 HTTP 바인딩 이용)  
    <br />
    ### **SOAP 메시지 바인딩 - HTTP 바인딩의 SOAPAction**    
    : HTTP 헤더 안에 존재하는 SOAP 메시지의 부가정보 기술  
    
    #### **용도**  
    * SOAP 메시지의 확인  
    * 정확한 수신자 지정
    * 보안상의 목적 
    <br /><br />
    ***
