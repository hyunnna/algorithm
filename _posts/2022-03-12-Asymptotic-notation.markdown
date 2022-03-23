---
layout: post
read_time: true
show_date: true
title:	점근적 표기법 (Asymtotic natation)
date:   2022-03-12 10:12:32 -0600
description : 
# img: posts/202203/data.jpg
tags: [asymtitic natation, algorithm, time complexity]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading

# toc: yes # leave empty or erase for no TOC
---
<br />


# <span style="color: #87CEEB">점근적 표기법 (Asymtotic natation) </span>  


#### 알고리즘의 효율성에서 실제 소요시간을 따지는 것이 중요하다.  



#### 알고리즘의 실행 시간은 **입력값의 크기**에 따라 달라질 수 있는데 예를 들어 특정 회원을 찾을 때 옵션을 들어 찾는다면 더 빨리 찾을 수 있을 것이다. 이렇게 입력값의 크기에 대한 함수로 알고리즘의 실행 시간을 생각할 수 있습니다.

 ### <span style="color: #87CEEB">**실행시간의 성장률 ( rate of growth )** </span>  


#### : 프로그램을 쉽게 유지 할 수 있도록 불핋요한 부분을 버리고 가장 중요한 부분만 추려내서 함수를 간소화 할 필요성이 있다.  
다음은 입력값의 크기에 따라 알고리즘의 함수가 얼마나 커지는지에 대한 그래프이다.  

1. 입력값의 크기가 n 인 알고리즘이 6n<sup>2</sup> + 100n + 300이라는 명령을 받는다고 가정했을 때 n의 값이 어느정도 커지면 6n<sup>2</sup>은 100n + 300보다 커지는 것을 볼 수 있다.  



<center>
<img src = "https://cdn.kastatic.org/ka-perseus-images/0642ea78ce621e53dbe7f45881a97786c7262635.png"  width=60% height="100%">
</center>


<br />
     n<sup>2</sup>의 계수인 6과 100n + 300을 제외하면 이 알고리즘의 실행시간은 n<sup>2</sup>으로 커지는 것을 아래 그래프에서 확인할 수 있다. 
<br /> <br />

2. 아래 그래프는 n의 계수들을 바꾸어 나타낸 그래프이다.  


<center>
<img src = "https://cdn.kastatic.org/ka-perseus-images/d2d40c938c1bab9f413c83164fec8ae9945e402b.png"  width=60% height="100%">
</center>


#### 따라서 필수적인 부분을 집중하고 불필요한 상세들을 무시하여 알고리즘의 수행시간을 표기하는 방법을  <span style="color: F05650">점근적 표기법</span>  이라고 한다.
 <br />
 
 **점근 표기법**은 위 그래프와 같이 시간복잡도 또는 공간복잡도 함수의 증가 양상을 구분하기 위해 사용하는 표기법으로 아래 세가지로 구분할 수 있다.  
    1. **O(f(n))** : 상한, 아무리 느려봤자 f(n) 정도이다. f(n)보다 빠르거나 같다.  
    2. **Ω(f(n))** : 하한, 아무리 빨라봤자 f(n) 정도이다. f(n)보다 느리거나 같다.  
    3. **Θ(f(n))** : 차수, 상한과 하한을 함께 제시. 두 집합의 교집합  

그전에 함수의 차수는 낮을수록 빠르며 그래프 으로 그렸을때 아래에 있는 함수가 더 빠르다.  

<center>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FTRG1s%2FbtqRonduSko%2FsS5eg2XJbdakWRJfkKNHnK%2Fimg.png" width="40%" height="100%">  
</center>

<br />

ex) 위 그래프를 봤을 때 처음에는 g(n)의 그래프가 더 아래에 있지만 시간이 갈수록 f(n)의 그래프가 아래에 있기 때문에 cf(n)의 함수가 더 빠르다.
 <br />

### <span style="color: #87CEEB">**O(F(n)) : 점근적 상한 / asympotic upper bound** </span>  
 <br />

<center>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FddfADm%2FbtqRnOh6rs0%2FAqRfHQMUZYR2Q3E0plDJpk%2Fimg.png" width="40%" height="100%">

</center>

### **[O-표기법] ( = Big-O)**   
  
 그래프를 봤을 때 g(n) ∈ O(f(n))일 때, f(n)이 g(n)의 상한이 된다. 즉 g(n)이 f(n)보다 빠르거나 같다는 뜻이다.

### **O(x(n)) = {f(n) : 모든 n ≤ f(n)≤ cx(n)인 양의 상수 c and n<sub>0</sub>이 존재 한다}**  
<br />

<center>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLDNZ0%2FbtqRomyycgm%2F9rVJBikUjX5qYNimlI7ECK%2Fimg.png" width="40%" height="100%">
</center>

위 그림과 같이 O(n<sup>2</sup>)에 속하는 집합의 함수들  = g(n) 은 n<sup>2</sup>(=f(n))보다 빠르거나 같다.  
<br />

### <span style="color: #87CEEB">**Ω(f(n)) : 점근적 하한, asympotic lower bound** </span>  
 <br />

<center>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbeRXK6%2FbtqRt5h4NpQ%2FdbsRFw3gCpeKOqYByDc5oK%2Fimg.png" width="40%" height="100%">

</center>

그래프를 봤을 때 g(n)dl cf(n)보다 느리므로 g(n) ∈ Ω(f(n))일 때, f(n)이 g(n)의 하한이 된다. 즉, g(n)이 f(n)보다 느리거나 같다.    

### **f(n)에 대해 g(n) ≥ c x f(n)을  만족하는 음이아닌 정수 n과 상수 c가 존재한다.**   
<br />


### <span style="color: #87CEEB">**Θ(f(n)) : 차수, asympotic tight bound**</span>  
 <br />

<center>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F6CfXA%2FbtqRt4XLpKi%2Fym7SYC0xiaHKbERqOBRdXK%2Fimg.png" width="40%" height="100%">

</center>

Θ(n) = O(f(n)) ∩ Ω(f(n))일 때, Θ(n)은 가능한 모든 g(n)의 집합이다. g(n) ∈ Θ(f(n))일 때, "g(n)은 f(n)의 차수(order)"라고 한다. 그래프를 보면 g(n)이 cf(n)보다 느리고, df(n)보다 빠르다. 따라서 g(n) ∈ Θ(f(n))이다.  

### **주어진 복잡도함수 f(n)에 대해 c x f(n) ≤ g(n) ≤d x f(n)을 만족 만족하는 음이아닌 정수 n과 상수 c가 존재한다.**  

 <br />

 ### <span style="color: #99CCFF">**시간복잡도 함수**</span>  
 
<br />
 : 문제를 해결하는데 걸리는 시간과 입력의 함수 관계  

 * ### O(n)  
      빅오 표기법 : 계수와 낮은 차수의 항을 제외시키는 방법  

     ex) 크기 n 의 모든 입력에 대한 알고리즘에 필요한 시간이 최대 n<sup>6</sup> + n<sup>3</sup> + 4 
 의 식을 가진다면 이 알고리즘의 점근적 시간 복잡도 O(n) = 6 이라고 할 수 있다.  

<br />

 * ### T(n)  
      빅오 표기법과 반대로 크기 n의 모든 입력에 대해 걸리는 최대의 시간을 보여주는 시간 복잡도  
 
 <br />
 <br />

****

##### 출처 :  

##### https://ko.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/asymptotic-notation  
##### https://chayan-memorias.tistory.com/100  
##### https://nolzaheo.tistory.com/3
