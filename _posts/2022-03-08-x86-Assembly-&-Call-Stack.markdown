---
layout: post
read_time: true
show_date: true
title:  x86 Assembly & Call Stack
date:   2022-03-09 22:32:20 -0600
description: The first weeek study avout security system.
img: posts/202203/assembly.jpg
tags: [security]
author: hyunnna
github:  hyunnna
mathjax: yes
---

### x86 Assembly

##### [ 어셈블리어 언어 ]

###### : 기계어와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급언어 , 컴퓨터 구조에 따라 사용하는 기계어가 달라지게 된다. 어셈블러는 니모니 기효 (사람이 보기 쉽게 만든 언어)를 opcode(기계어의 일부, 수행할 명령어를 나타내는 부호) 로 변환하고 메모리 위히와 기타 존재물에 따라 식별자를 다시 준석함으로써, 목적 코드(실행될 수 있는 기계어 코드)를 만들어 낸다.

##### [ Why x86? ]
###### 사용자에게 가장 일반적으로 사용되는 명령어 집합 아키텍쳐이다.
 
### 래지스터
###### : x86 기반 CPU는 8개의 범용 래지스터를 가지고 있으며 각각 4바이트(32bits)의 크기 저장 가능.


### Call Stack
###### : 콜 스택은 프로그램이 함수 호출을 추적할 때 사용하는 것. 각 function call 당 하나씩의 스택들로 이루어져 있다. 

```java
def plus_function():
  sum = 0
  return sum+1
  
def calculate():
  total =0
  total += plus_funtion()
  print(total)

```

###### 먼저 plus_function을 호출하고 콜스택 위에 쌓이게 된다. 

> ###### plus_function()
> > ######  calculate()
> > > ###### print()

##### 이 순서대로 쌓이게 된다.

### Stack
##### * 스택에 저장되는 내용
+ ###### 지역변수
+ ###### 함수로 들어온 인수
+ ###### 호출한 함수의 스택에 대한 정보
+ ###### 반환값주소 







###### 출처 : https://live2skull.tistory.com/15
