---
layout: post
read_time: true
show_date: true
title:	Greedy Algorithm
date:   2022-03-11 18:12:32 -0600
description : Greedy Algorithm 
tags: [algorithm]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading

# toc: yes # leave empty or erase for no TOC
---

# <span style="color:MediumSeaGreen">[Algorithm] **Greedy**  </span>  

<center>
<img src="https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/08/%E1%84%8B%E1%85%AD%E1%86%A8%E1%84%86%E1%85%A1%E1%86%BC%E1%84%8B%E1%85%B4-%E1%84%92%E1%85%A1%E1%86%BC%E1%84%8B%E1%85%A1%E1%84%85%E1%85%B5.jpeg?w=460&ssl=1" width="40%" height="100%">  
</center>

## **그리디 알고리즘**

 : <span style="color:MediumSeaGreen">**Greedy( 탐욕스러운 , 욕심많은)**  </span> 뜻 그대로 각 단계에서 현재 상태의 최적의 값 만을 선택하는 알고리즘  

순간마다 하는 선택은 그 상황에서는 최적일수는 있어도 상황들을 적합한 결과의 해답은 최적이 아닐수 있다.  

탐욕 알고리즘은 항상 최적의 결과를 도출하는 것은 아니지만, 어느정도 최적의 근사한 값을 빠르게 도출할 수 있는 장점이 있다.
<br />

### <span style="color:OliveDrab">**그리디 알고리즘 해결방법**  </span>
1. **선택절차(Selection Procedure)** : 현재 상태에서의 최적의 해답을 선택한다.  

2. **적절성 검사(Feasibility Check)**: 선택된 해가 문제의 조건을 만족하는지 검사한다.  
3. **해답 검사 (Solution Check)** : 원래의 문제가 해결되었는지 검사하고, 해결되지 않았다면 선택 절차로 돌아가서 과정을 반복한다.   
<br />

### <span style="color:OliveDrab">**그리디 알고리즘 적용 조건**  </span>
 1. **탐욕적 선택 속성(Greedy Choice Property)** : 앞의 선택이 이후의 선택에 영향을 주지 않는다.  

2. **최적 부분 구조(Optimal Substructure)**: 문제에 대한 최종 해결 방법은 부분 문제에 대한 최적 문제 해결 방법으로 구성 된다.  
<br />

**이러한 조건이 성립하지 않는 경우에는 탐욕알고리즘은 최적해를 구하지 못한다.** 

<br />

### <span style="color:OliveDrab">**그리디 알고리즘 예시**  </span>  

### 1.

<br />
<center>
<img src="https://thumb.ac-illust.com/t/fb/fb32ced92221e25df882b69ec7436710_t.jpeg" width="50%" height="30%">  
</center>
<br />

#### **거스름돈 계산하기**

`
 냐옹이 띠부띠부씰을 뽑기 위해 빵 자판기에서 빵을 사는 중이다! 빵을 네개 사서 총 5200원을 내야한다. 10000원을 냈을 때 거스름돈은 어떻게 거슬러 줘야할까? 거스름돈은 동전의 개수를 최소한으로 하여 거슬러줘야한다. 
` 
<br />
<br />

- **해결 과정 적용** 
1. **선택 절차**
    + 거스름돈의 동전 개수를 줄이기 위해 현재 가장 가치가 높은 동전을 우선 선택  
<br />
2. **적절성 검사**  
    + 1번 과정을 통해 선택된 동전들의 합이 거슬러 줄 금액을 초과하는지 검사
    + 초과하면 가장 마지막에 선택한 동전을 삭제하고 , 1번으로 돌아가 한 단계 작은 동전을 선택 
<br />
3. **해답검사**
    + 선택된 동전들의 합이 거슬러 줄 금액과 일치하는지 검사
    + 금액이 부족하면 1번 과정부터 다시 반복
    <br />
    <br />

- **해답**  
거스름돈은 10000 - 5200 = **4800**  

    (1) 먼저 가장 가치가 높은 금액인 1000원 짜리 4장  **(거스름돈 800원)**  
    (2) 5장을 줄 경우 거스름돈이 더 많으므로 삭제  
    (3) 다음 500원짜리 1개  **(거스름돈 300원)**  
    (4) 500원짜리 2개를 거슬러 줄 경우 거스름돈이 더 많으므로 삭제  
    (5) 다음 100원짜리 3개 **(거스름돈 0원)**  
    (6) 100원짜리 3개를 거슬러 줄경우 거스름돈이 더 많으므로 삭제  

    거스름돈 : **1000 * (4) + 500 * (1) + 100 * (3)**

```java

```










<br /><br />  
***

##### 출처 : https://hanamon.kr/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%ED%83%90%EC%9A%95%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-greedy-algorithm/


