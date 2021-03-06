---
title: "[알고리즘 학습] 02 - 버블 정렬(Bubble Sort)"
toc: false
tags: [알고리즘,알고리즘 학습,정렬,Sort,버블 정렬,Bubble Sort]
categories:
  - Algorithm
  - Study
date: 2020-07-27 04:00:00
thumbnail: /images/post_include/algorithm_study/poster.png
---
> 나동빈님의 [실전 알고리즘 강좌(Algorithm Programming Tutorial)](https://www.youtube.com/playlist?list=PLRx0vPvlEmdDHxCvAQS1_6XV4deOwfVrz)를 바탕으로 학습한 내용을 정리한 포스트입니다.  
> 실습 코드는 [WebKit's style guide](https://webkit.org/code-style-guidelines/)를 따라 C언어로 작성되었습니다.   
> 개인적으로 학습하며 작성한 포스트이기 때문에 <font color='red'>오류</font>가 있을 수 있습니다. 잘못된 내용이 있다면 댓글로 알려주세요.  

# 소스코드
```c
#include <stdio.h>

int main(void)
{
    int i, j, temp;
    int array[10] = { 1, 10, 5, 8, 7, 6, 4, 3, 2, 9 };
    for (i = 0; i < 10; ++i) {
        for (j = 0; j < 9 - i; ++j) {
            if (array[j] > array[j + 1]) {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }

    for (i = 0; i < 10; ++i) {
        printf("%d ", array[i]);
    }

    return 0;
}
```

# 개요
버를 정렬은 인접한 두 숫자를 서로 비교하여 두 숫자의 위치를 변경해나가는 방식의 정렬입니다.  
배열을 한바퀴 순환할 때 마다 가장 큰 수가 배열의 끝에 확정되게 됩니다.  

# 시간 복잡도
길이가 10인 배열을 정렬할 때 버블 정렬을 사용하는 경우 `10+9+8+...+1=55`번 배열에 접근합니다.
  
이러한 등차수열은 `N*(N+1)/2` 즉, `10*(10+1)/2`로 구하는 방법도 있는데, N이 매우 큰 숫자일 경우 +1과 /2는 의미가 큰 의미가 없기 때문에 일반적으로 `N*N`번 접근한다고 이야기합니다.

이를 Big-O 표기법으로 표기하면 O(N*N) => O(N<sup>2</sup>)이 됩니다.

하지만 수를 비교할 때 마다 Swap을 수행하기에 같은 O(N<sup>2</sup>) 정렬 알고리즘 중에서 가장 느리다고 볼 수 있습니다.

결론: 버블 정렬의 시간 복잡도는 <strong>O(N<sup>2</sup>)</strong>이다.