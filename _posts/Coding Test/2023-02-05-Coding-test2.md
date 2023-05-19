---
layout: single
title: "[Coding_test] 2022 KAKAO BLIND RECRUITMENT #2 k 진수에서 소수의 개수 구하기"
categories: Coding_test
tag: [C, Kakao, Coding_test]

toc: true
author_profile: false
sidebar:
    nav: "counts"
---


# 2022 KAKAO BLIND RECRUITMENT


## Team Coding Match

<div class="notice--success">
    <b>[ 잡담 ]</b>
    <br>
    이제 두번째 대결이당. 저번 1차시에선 내가 1등했다. ㄱㅇㄷ 
    이번에도 1등하겟단 마인드였지만 작성자는 독감으로 일주일 쓰러져잇고 
    내가 멀쩡해지니까 하은이가 죽을려고 한다.ㅜㅜ 하지만 우린 할수잇다!
    <br><br>
    <b>[ 팀 구성 ]</b>
    <u1>
        <li>민기, 하은</li>
        <li>승제, 지안</li>
        <li>새진, 민주</li>
    </u1>
    <br>    
    <b>[ 커리큘럼 ]</b>
    <u1><br>
        1_신고 결과 받기<br>
        <b>2_k 진수에서 소수의 개수 구하기</b><br>
        3_주차 요금 계산<br>
        4_양궁 대회<br>
        5_양과 늑대<br>
        6_파괴되지 않은 건물<br>
        7_사라지는 발판<br>
    </u1>
</div>

## 문제#2_k 진수에서 소수의 개수 구하기

### 문제 설명

양의 정수 **n**이 주어집니다. 이 숫자를 **k**진수로 바꿨을 때, 변환된 수 안에 아래 조건에 맞는 소수(Prime number)가 몇 개인지 알아보려 합니다.

* **0P0**처럼 소수 양쪽에 0이 있는 경우
* **P0**처럼 소수 오른쪽에만 0이 있고 왼쪽에는 아무것도 없는 경우
* **0P**처럼 소수 왼쪽에만 0이 있고 오른쪽에는 아무것도 없는 경우
* **P**처럼 소수 양쪽에 아무것도 없는 경우
* 단, **P**는 각 자릿수에 0을 포함하지 않는 소수입니다.
   * 예를 들어, 101은 **P**가 될 수 없다.
     
   

예를들어, 437674을 3진수로 바꾸면 **211**0**2**01010**11**입니다. 여기서 찾을 수 있는 조건에 맞는 소수는 왼쪽부터 순서대로 211, 2, 11이 있으며, 총 3개입니다.
(211, 2, 11을 **k**진법으로 보았을 때가 아닌, 10진법으로 보았을 때 소수여야 한다는 점에 주의합니다.)
211은 **P0** 형태에서 찾을 수 있으며, 2는 **0P0**에서, 11은 **0P**에서 찾을 수 있습니다.


정수 **n**과 **k**가 매개변수로 주어집니다. **n**을 **k**진수로 바꿧을 때, 변환된 수 안에서 찾을 수 있는 **위 조건에 맞는 소수**의 개수를 return 하도록 solution 함수를 완성해 주세요.


---



#### 제한사항
  * 1 <= **n** <= 1,000,000
  * 3 <= **k** <= 10

  

---


#### 입출력 예


|n|k|result|
|:-:|:-:|:----:|
|437674|3|3|
|110011|10|2|

 <br> 

---



#### 입출력 예 설명



**입출력 예 #1**


문제 예시와 같습니다.


**입출력 예 #2**


110011을 10진수로 바꾸면 110011입니다. 여기서 찾을 수 있는 조건에 맞는 소수는 11, 11 2개입니다. 이와 같이, 중복되는 소수를 발견하더라도 모두 따로 세어야 합니다.

 

---



#### solution.c


```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

int solution(int n,int k){
  int answer = -1;
  return answer;
}
```


### 문제 풀이

#### 아이디어_1
- 처음 이 문제에 대해서 생각했을 때 일반적인 int형 변수로 한다면 범위가 작아서 안될거라고 생각했다. 그래서 숫자를 입력받아 진수변환을 하면서 값들 하나하나를 배열에 넣었다.
    - n에서 k를 나눈 나머지를 a[]에 처음부터 넣고 n/=k를 통해 n값을 나눠준다. 이 과정을 반복해서 진수변환을 통해 a[]에 역순으로 숫자가 들어간다.
        - a[index++] = n % k;
        - n /= k;


<br>

- 반복문으로 a[]을 역순으로 읽으면서 a[i] != 0 이면 num 변수에 10을 곱하여 a[i]의 값을 더해준다. 
    - 0이 아닐 경우에는 하나씩 읽은 숫자가 1, 1, 2이고 다음의 숫자가 0이라고 가정한다면 211이라는 숫자를 만들어야하기 때문이다.
        - ```c
        if (a[i] != 0) {
                num *= 10;
                num += a[i];
        }
        ```

- 만약 0이라면 위에서 언급한 것처럼 숫자가 완성되었기 때문에 primeNum() 함수에 넣어 소수라면 answer++ 해준다.
    - ```c
    bool primeNum(int x) {
            printf("%d\n", x);
            if (x == 1) return false;
            for (int i = 2; i*i <= x; i++) {
                if (x % i == 0) return false;
            }
            return true;
    }
    ```


<br>

- 위의 과정들을 반복하고 for문을 탈출하였을 때 마지막 숫자는 0을 만나지 않기 때문에 if문을 이용하여 마지막 숫자를 따로 처리한다.
    - ```c 
        if (num != 0 && primeNum(num)) answer++; 
    ```

<br>

- 최종적으로 answer를 반환한다.

<br>

---




#### 아이디어_1 코드

```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

bool primeNum(int x) {
    printf("%d\n", x);
    if (x == 1) return false;
    for (int i = 2; i*i <= x; i++) {
        if (x % i == 0) return false;
    }
    return true;
}

int solution(int n, int k) {
    short int index = 0;
    int a[100] = { 0 };  
    int answer = 0;

    while (n > 0) {
        a[index++] = n % k;
        n /= k;
    }

    unsigned long long int num = 0;
    for (int i = index - 1; i >= 0; i--) {
        if (a[i] != 0) {
            num *= 10;
            num += a[i];
        }
        else {
            if (num == 0) continue;
            if (primeNum(num)) answer++;
            num = 0;
        }
    }

    if (num != 0 && primeNum(num)) answer++;
    return answer;
}

int main() {
    printf("%d", solution(797161, 3));
}
```



---

<br>

#### 아이디어_2

- 아이디어_1에서는 배열을 이용하여 풀었는데 정말 변수만을 사용하여 문제를 해결할 수 없을까 생각하다가 자료형의 범위에 대해서 새로 공부하게 되었다.
    - 그 결과 unsigned long long int 자료형을 사용하면 충분히 문제를 해결할 수 있음을 깨닫고 시도하였다.
        - 작동원리는 아이디어_1과 거의 동일하다.
            - 차이점은 배열에 저장하지 않고 변수에 일일히 저장하여 소수인지 판별하고 다시 초기화하여 다음 값을 넣는 방식을 사용하였다.


        - 최종적으로 answer를 반환한다.

<br>

---

#### 아이디어_2 코드

```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

bool primeNum(unsigned long long x) {
	if (x < 2) return false;
	for (unsigned long long i = 2; i * i <= x; i++) {
		if (x % i == 0) return false;
	}
	return true;
}

int solution(int n, int k) {
	unsigned long long num = 0;
	unsigned long long remain = 0;
	unsigned long long mul = 1;
	int answer = 0;


	while (n > 0 || num > 0) {
		remain = n % k;
		.printf("remain : %d\n", remain);
		if (remain == 0) {
			if (primeNum(num)) answer++;
			num = 0;
			mul = 1;
		}
		else {

			printf("num : %d\n", num);
			num += remain * mul;
			mul *= 10;

		}
		n /= k;
	}


	if (primeNum(num)) answer++;
	printf("\nanswer : %d", answer);
	return answer;
}

int main() {
	solution(437674, 3);
	// solution(110011, 10);
}
```



<br>

---
## 후기
<div class="notice--success">
최종적으로 나와 하은이 제출한 <b>아이디어_1 코드</b>는 3등을 하였다.ㅜㅜㅜ
실패 요인 중 하나는 반례가 존재한다는 것이었다. 프로그래머스에 테스트 케이스를 모두 돌렸을 때는 100프로 정답이였는데
알고보니 쓰레기값이 들어갔는데 운 좋게 통과한 것이었당..ㅜㅡ 좀더 자세히 알아보고 다양한 시도를 했으면 알아차렸을텐데 아쉬웠당.
하여튼 그 이유는 코드에서 num이라는 변수를 소수인지 판별하는데 <b>num변수를 short int 로 정의</b>했기 때문이다.
num변수의 범위를 넘어가는 수가 들어가되면 오류가 뜬다..ㅜㅜ
사실 하은이가 short 추가햇는데...ㅋㅋ 내가 알아차리지 못햇으니 내 죄인거같당..ㅜㅜ
이번 문제를 통해서 범위를 확인하고 반례가 없는지 꼼꼼히 살펴봐야겟다.. 내 돈..ㅜㅜ
다음엔 내가 1등할거다 ㄹㅇㅋㅋㅋㅋ
</div>