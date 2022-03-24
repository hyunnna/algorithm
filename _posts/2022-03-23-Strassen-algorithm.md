---
layout: post
read_time: true
show_date: true
title:	Strassen algorithm
date:   2022-03-23 10:12:32 -0600
description : Examples of divide and conquer algroithm
# img: posts/202203/data.jpg
tags: [Divide and Conquer]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading
# toc: yes # leave empty or erase for no TOC
---


---
layout: post
read_time: true
show_date: true
title:	Strassen Algorithm
date:   2022-03-23 18:12:32 -0600
description : Examples of divide and conquer algroithm - There is not in the text book!
tags: [algorithm]
author: HyunHwa
github: hyunnna
---

# <span style="color:PaleVioletRed">**[분할정복] Strassen Algorithm**</span>  

### <span style="color:PaleVioletRed">**행렬곱 기본형태** </span> 

<br />

<center>

<img src = "https://wikimedia.org/api/rest_v1/media/math/render/svg/9196c0c24ad20c3b18582bc78785fa405d91c7c3
"  width="70%" height="100%">

</center>  

<br />

위와 같이 각 크기가 n인 정사각 행렬 A,B가 있다고 가정하고,

<br />

<center>

<img src = "https://wikimedia.org/api/rest_v1/media/math/render/svg/7d3ce5d06e84e1a8575ce6f1d47a90d006baf628
"  width="40%" height="70%">

</center>  
행렬 곱 C = AB는 아래와 같이 크기 n인 정사각 행렬로 정의된다.  

<br />

### <span style="color:PaleVioletRed">**시간복잡도** </span>

<center>

<img src = "https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgkdfr2qjsuqs.jpg%22&type=w2
"  width="30%" height="50%">

</center> 

<br />

위는 행렬의 곱셈을 표현한 식이다.  
 
행렬 C 하나의 원소를 구하는데 드는 시간은 곱셈 **n**번과 덧셈 **n-1**이다. 행렬 C전체를 구하는 경우 행렬 C의 크기가 **n x n** 이므로 곱셈 **n<sup>3</sup>** 번, 덧셈 **n<sup>2</sup>(n-1)** 번하게 된다.따라서 행렬을 구하는 시간복잡도는 **O(n<sup>3</sup>)** 이 된다.

<br />

## <span style="color:PaleVioletRed">**슈트라센 알고리즘 ( Strassen Algorithm )** </span>  

<br />

* 분할 정복 알고리즘 중에 하나인 스트라센 알고리즘은 **행렬 곱셈**을 효율적으로 곱할 수 있는 방법이다.  
* 행렬 곱셈의 시간복잡도를 줄이려는 시도는 계속 있었고, 실제 슈트라센이 1969년 슈트라센 알고리즘을 제안 한 뒤 시간 복잡도는 계속 줄어왔습니다.  
* **알고리즘을 구현할 때 행렬을 가로,세로 절반으로 나누기 때문에 행렬의 가로/세로 길이도 짝수여야 한다. 따라서 0을 적절히 padding하여 크기를 맞추어야 한다.**  

<br />

### <span style="color:PaleVioletRed">**LOGIC** </span>  

* 행렬들을 쪼개서 곱하고 더하는 과정을 재귀적으로 반복함  
* 행렬의 덧셈이 곱셈보다 더 빠른 점을 이용해 쪼갠 행렬들의 곱셈 횟수를 줄이고 덧셈 횟수를 늘린다. ( 곱셈은  **O(n<sup>3</sup>)** , 덧셈은 **O(n<sup>2</sup>)** 의 시간복잡도를 가진다. )  

<br />

### <span style="color:PaleVioletRed">**재귀적으로 행렬 계산하기** </span>  

행렬을 재귀적으로 쪼개는 작업이 n을 2로 계속 나누기 때문에 사전에 행렬들의 크기를 2의 거듭제곱으로 맞추어놓는다.  
아래 사진 처럼 행렬 C를 A , B 각각 4분할로 쪼갠다.  
쪼개진 행렬들로 그 다음 4개의 식들이 성립된다.

<center>

<img src = "https://blog.kakaocdn.net/dn/0kUGz/btqNqB7ArLe/wIy79mpUOcWDjIrgKXdGuK/img.png"  width="50%" height="50%">

</center>  


### <span style="color:PaleVioletRed">**슈트라센** </span>  
 
 <br />

<center>

<img src = "https://media.vlpt.us/images/riechu3228/post/56edad15-fab4-4e31-8d09-0ce3b7720929/image.png
"  width="80%" height="50%">

</center>


<center>

<img src = "https://media.vlpt.us/images/riechu3228/post/64305f90-bf03-4fbd-b0c6-22d7fc6a3e8f/image.png
"  width="80%" height="50%">

</center> 

전 행렬의 곱셈에서는 8번의 곱셈과 4번의 덧셈, 하지만 슈트라센 알고리즘을 사용하면 7번의 곱셈과 18번의 덧셈, 뺄셈이 필요하다. 덧셈이 곱셈보다 더 빠르므로 행렬의 크기가 커지면 슈트라센 알고리즘이 더 효율적이라고 말할 수 있다.

<br />
<br />

***

###### 출처 : http://www.secmem.org/blog/2021/03/20/strassen-algorithm/