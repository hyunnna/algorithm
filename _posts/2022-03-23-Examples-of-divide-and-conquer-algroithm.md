---
layout: post
read_time: true
show_date: true
title:	Merge , Quick , Binary Sort
date:   2022-03-22 10:12:32 -0600
description : Examples of divide and conquer algroithm
# img: posts/202203/data.jpg
tags: [Divide and Conquer]
author: HyunHwa
github: hyunnna
mathjax: yes # leave empty or erase to prevent the mathjax javascript from loading
# toc: yes # leave empty or erase for no TOC
---

# <span style="color:PaleVioletRed">[분할 정복] **Merge/ Quick / Binary Sort**  </span>  
<br />

## <span style="color:PaleVioletRed">**합병정렬 ( Merge Sort )** </span> 
<br />
<center>
<img src = "https://gmlwjd9405.github.io/images/algorithm-merge-sort/merge-sort-concepts.png
"  width="80%" height="100%">
</center>  
<br />


 
* 입력이 2개의 부분문제로 분할되고, 부분문제의 크기가 1/2로 감소하는 **분할 정복 알고리즘 중 하나**이다.  
* **분할 정복 방법** : n 개의 숫자들을 n/2개씩 2개의 부분 문제로 분할하고, 각각의 부분문제를 재귀적으로 합병 정렬한 후, 2개의 정렬된 부분을 합병하여 정렬한다. 주로 순환호출을 이용함.  
+ 안정 정렬중 하나이고 분할되는 배열이 균등하다.
* **과정 설명**
    1. 리스트의 길이가 0또는 1이면 이미 정렬된 것으로 보고 그렇지 않은 경우에는 
    2. 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.
    3. 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
    4. 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다.

<br />

## <span style="color:PaleVioletRed">**LOGIC**  </span> 

```java
MergeSort(A,p,q)  
입력 : A[p] ~ A[q]
출력 : 정렬된  A[p] ~ A[q]

1 if (p < q ){ // 배열의 원소가 2개 이상일 경우
2    k = [(p+q)/2] // k = 반으로 나누기 위한 중간 원소의 인덱스
3    MergeSort(A,p,k) // 앞부분 재귀 호출
4    MergeSort(A,k+1,q) // 뒷부분 재귀 호출
5    A[p] ~ A[k]와 A[k+1] ~ A[q]를 합병한다
6 }
```

- Line 1에서는 정렬할 부분의 원소의 수가 2개 이상일 때에만 다음 단계가 수행 되도록 하고 만일 p=q (원소의 갯수가 1)이면 , 그 자체로 정렬된 것으로 line 2~5가 수행되지 않은채 이전 호출했던 것으로 리턴한다.  
- Line 2에서는 정렬할 부분의 원소들을 반으로 나누기 위해 k = [(p+q)/2]를 계산한다. 안, 원소의 수가 홀수인 경우, k는 소수점 이하를 버린 정수이다.  
- Line 3~4에서는 MergeSort(A,p,k)와 MergeSort(A,k+1,q)를 재귀 호출하여 각각 정렬한다.  
- Line 5에서는 line 3 \~ 4에서 각각 정렬된 부분을 합병한다. 합병 과정의 마지막에는 임시 배열에 있는 합병된 원소들을 배열 A로 복사한다. 즉, 임시 배열 B[p]\~B[q]로 복사한다.

<br /> 

## <span style="color:PaleVioletRed">**Merge Sort Code**  </span> 
<br />

|배열 A |8 |9|45|78|2|77|90|16|
|------|---|---|---|---|---|---|---|---|


|배열 B |12 |60|46|10|28|31|53|94|
|------|---|---|---|---|---|---|---|---|  

<br />

|배열 C |2|8|9|10|12|16|28|31|45|46|53|60|77|78|90|94|
|------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 

<br /> 아래 코드는 배열 A와 B가 합병되어 배열 C에 저장된 것을 보여준다.  


```java
public class Main {
    public static int[] src;
    public static int[] tmp;

    public static void main(String[] args){
        src = new int[8,9,45,78,2,77,90,16];
        printArray(src);
        mergeSort(0, scr.length-1);
        printArray(src);
    }
    public static void mergeSort(int start, int end){
        if (start < end ){
            // start :merge sort를 진행할 배열의 시작 인덱스
            //end: 마지막으로 포함될 배열의 인덱스 의미
            int mid = (start+end) /2; // 그림처럼 binary tree 형태로 쪼개기때문에 start 와 end의 중간지점 저장
            mergeSort(start, mid); // 첫분할은 시작점부터 중간점까지가 된다.
            mergeSort(mid+1 , emd); // 두번째 분할은 중간점 다음부터 끝점까지가 된다.

            int i = start; 
            int j = mid + 1; 
            int idx = i; // start는 항상 mid+1 보다 작기때문에 start 지점이 된다.

            while(i<=mid || j<=end) {
                if (j>end || (i<=mid && src[i]<src[j])){
                    tmp[idx++] = src[i++];
                }else {
                    tmp[idx++] = src[j++];
                }
            }
            for( int k = start; k<=end; k++){
                src[k] = tmp[k];
            }
        }
    }
    public static void printArray(int[] a){
        for(int x=0; x<a.length; x++)
            System.out.print(a[x]+" ");
        System.out.println();
    }
}

```

+ 또한 i가 mid 이하 이거나 j가 end 이하일때 동작해야 한다. 미만이 아닌 이유는 원소의 개수가 1개일때 까지 나누기 때문이다. 동시에 종료가 되지 않을 수도 있으니 조건은 &&가 아닌 || 이다.  
+ 첫번째 분할에서 원소를 가져오는 경우는 다음의 두가지와 같다.
    1. 두번째 분할의 원소를 이미 다 가져온 경우 (q>end) ---- <span style="color:lightskyblue">*j > end*  </span> 
    2. 첫번째 분할에서 가져오지 않은 원소가 있고, 첫번째 분할의 첫 원소 값이 두번째 분할의 첫 원소값보다 작은 경우 ---- <span style="color:lightskyblue">*i <= mid && src[i] * < src[j]**  </span>  
<br />
+ 두조건 중 하나 이상 만족하면 첫번째 분할에서 원소를 가져오므로 두 조건 사이에 or을 사용한다. 따라서 if문이 if (j>end || (i <=mid && src [i]<src [j] )) 이렇게 선언되었다.  
+ if 문에 결과에 따라 1번 분할의 첫번째 값이나, 2번 분할의 첫번째 값을 정렬된 값을 tmp ( 임시저장하는 배열 )에 저장해준다.  
이때 가져온 원소의 다음 인덱스를 다시 비교하기 위해 i++ 또는 j++를 조건에 맞게 해준다.(idx도 다음 최솟값을 찾아 저장해야하므로 당연히 ++ 해준다. )  
+ 1번 분할과 2번 분할의 모든 원소를 가져오면 start 부터 end 까지 정렬된 값을 다시 src 라는 원래 배열에 저장한다. 

<br />

## <span style="color:PaleVioletRed">**시간복잡도**  </span> 
### **:  O(n * log n)**  

* 자료의 크기를 완전히 분해하기 까지 **log n**개의 호출레벨이 생긴다. 자료의 갯수가 9개일경우 2<sup>3</sup> < 호출레벨 <= 2<sup>4</sup> 이 된다.  

* **n의 의미** : 병합 알고리즘은 각각의 나누어진 경우에서 각 원소들을 비교하여 새로운 버퍼에 하나씩 집어넣는다. 버퍼의 크기 만큼 비교가 일어나고 버퍼의 크기는 원래의 자료의 크기이므로 n번 이루어진다. 



***
 
## <span style="color:PaleVioletRed">**퀵정렬 ( Quick Sort )** </span>  
<br />

<center>
<img src = "https://blog.kakaocdn.net/dn/bb5JKi/btq5aAjJZnz/lkkjHB9nXbzXkFG0cDUEK0/img.gif
"  width="50%" height="100%">
</center>
<br />

+ 퀵 정렬은 분할 정복 알고리즘을 통해 데이터를 정렬하는 기법이다. 
+ **원소만의 비교만으로 정렬을 수행**하는 알고리즘이기 때문에 비교정렬의 한 종류이고 불안정 정렬에 속한다. 또한 위의 Merge Sort와 다르게 분할되는 배열이 불균등 하다.  
+  퀵 정렬은 데이터를 비교하면서 찾기 때문에 **비교정렬**이며 정렬의 대상이 되는 데이터 외에 추가적인 공간을 필요로 하지 않으므로 제자리정렬 (in-place-sort)이다.
+ 피벗을 기준으로 두개의 부분리스트를 만들때 서로 떨어진 원소끼리 교환이 일어나기 때문에 **불안정 정렬** 알고리즘이다.  


<br />

## <span style="color:PaleVioletRed">**LOGIC**  </span> 
1. 주어진 배열에서 임의의 한 원소를 고르고 이를 **피벗(Pivot)** 이라고 가정한다. 
2. 피벗을 기준으로 **피벗보다 값이 작은 원소들을 모은 배열 하나** 와 **피벗보다 값이 큰 원소들을 모은 배열 하나**로 배열을 둘로 나눈다. 피벗은 그자리에 고정
3. 분할된 두개이 배열에 대해 **위 1과 2 과정을 반복**하여 정렬한다.  
<br /> 

## <span style="color:PaleVioletRed">**Quick Sort Code**  </span> 

```java
array = [ 4 , 8, 7, 22, 6, 78, 1, 27, 15]
def  Quick_Sort(array):
    if len(array) <= 1:
        return array // 길이가 1까지 도달한 경우 그대로 리턴한다.

        pivot = array[0] // 첫번째 원소를 피벗으로 삼는다. 
        tail = array[1:] // 피벗제외 배열을 나눈다.

        left_side = [x for x in tail if x<=pivot] // 피벗보다 작거나 같은 원소만 모은 배열
        right_side = [x for x in tail if x > pivot] // 피벗보다 큰원소

        // 피벗의 자리는 고정되었으며 피벗 기준 왼쪽 배열과 오른쪽 배열에 대해 재귀를 수행한다.
        return Quick_Sort(left_side) + [pivot] + Quick_Sort(right_side)

    print(Quick_Sort(array))

```
## <span style="color:PaleVioletRed">**시간복잡도**  </span> 
+ ### **최선의 경우**  
    ###  : O(nlogn) 
    1. 비교 횟수 
    - 원소의 개수의 n이 2의 거듭제곱이라고 생각했을 때 n = 16 인경우 ( n = 2^4 )  
    - 2로 나누어서 분할되기 때문에 (16-8-4-2) 순으로 줄어들어 recursive 깊이가 3이다.  
    - n = 2 ^ k라고 가정했을때 **k = long<sub>2</sub>n** 이다.
    
    <br />

    2. 각 recursive 호출단계의 비교연산  
    ###  : O(n)  
    * 순환 호출 각각에서는 **피벗과 전체원소들 각각을 비교**해야 하기 때문에 평균적으로 n번 비교가 발생한다. 

<br />

+ ### **최악의 경우**  
    * 정렬하고자 하는 배열이 오름차순 , 내림차순을 정렬되어 있을때 시간복잡도가 **O(n^2)** 가 되고 불균형 분할에 의해 성능이 안좋아진다.


<br />
<br />

***  
###### 출처 : https://yunmap.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Java%EB%A1%9C-%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94-%EC%89%AC%EC%9A%B4-Merge-Sort-%EB%B3%91%ED%95%A9-%EC%A0%95%EB%A0%AC-%ED%95%A9%EB%B3%91-%EC%A0%95%EB%A0%AC  , https://velog.io/@haero_kim/%EC%A0%95%EB%A0%AC-%EC%84%B8%EA%B3%84%EA%B4%80-%EC%B5%9C%EA%B0%95%EC%9E%90-Quick-Sort , https://velog.io/@haero_kim/%EC%A0%95%EB%A0%AC-%EC%84%B8%EA%B3%84%EA%B4%80-%EC%B5%9C%EA%B0%95%EC%9E%90-Quick-Sort
