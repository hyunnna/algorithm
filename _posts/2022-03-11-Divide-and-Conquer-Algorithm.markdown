---
layout: post
read_time: true
show_date: true
title:	Divide and conquer
date:   2022-03-11 18:12:32 -0600
description : Divide and conquer Algorithm 
tags: [algorithm]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading

# toc: yes # leave empty or erase for no TOC
---
# <span style="color:PaleVioletRed">[Algorithm] **Divide and conquer**  </span>  

### 분할정복 알고리즘

 :  여러 알고리즘의 기본이 되는 해결 방법으로 방대한 문제를 조금씩 나눠가면서 나눌수 없을 때까지 나누어서 각각 풀고, 다시 합병하여 문제의 답을 얻는 알고리즘  

 <br />


### **알고리즘 설계하기**
<br />

  1. **Divide** : 문제가 분할이 가능한 경우, 2개 이상의 문제로 나눈다.  
  2. **Conquer** : 나누어진 문제가 여전히 분할이 가능하면, 또 다시 Divide를 수행한다.
  3. **Combine** : Conquer한 문제들을 통합하여 문제의 답을 얻는다.  
<br />

  + 장점 : 문제를 나눔으로써 어려운 문제 해결 가능  

+ 단점 : 함수를 재귀적으로 호출하여 오버헤드가 발생할 수 있으며  
스텍에 다양한 데이터를 보관하고 있어야 하므로 스택 오버플로우가 발생하거나 과도한 메모리를 사용한다는 단점이 있다.  
또한 'F(x)가 간단하다'라는 것을 정의하기가 어려울 수 있다. 
<br />
<br />

### **적용방식**  

재귀적으로 자신을 호출하면서 그 연산의 단위를 조금씩 줄여가는 방식이다.  
<br />
```java
function F(x) :

    if F(x)가 간단 then:
    return F(x)를 게산 한 값

    else:
    x를 x1, x2로 분할
    F(x1), F(x2) 호출  
    return F(x1), F(x2)로 F(x)를 구한 값

```  
<br />

### **분할정복의 응용**  

1. 병합정렬 (Merge Sort)  

     시간복잡도 :  *`O(nlog n) `*  
     공간복잡도 : *`O(n)`*  

* 알고리즘  
  (1) 정렬할 데이터 집합의 크기가 0 또는 1이면 이미 정렬된 상태로 본다.  
  (2) 그렇지 않으면 데이터 집합을 반으로 나눈다.  
  (3) 원래 같은 집합에서 나눠져 나온 데이터 집합 둘을 병합하여 하나의 데이터 집합으로 만든다.  
  병합할 때 데이터 집합의 원소는 순서에 맞춰 정렬한다.  
  (4) 데이터 집합이 다시 하나가 될때 까지 (3)의 과정을 반복한다. 



    




<br /><br />
***
##### 출처 : https://namu.wiki/w/%EB%B6%84%ED%95%A0%20%EC%A0%95%EB%B3%B5%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98?from=%EB%B6%84%ED%95%A0%20%EC%A0%95%EB%B3%B5
