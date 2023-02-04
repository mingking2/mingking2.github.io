---
layout: single
title: "[Coding_test] 2022 KAKAO BLIND RECRUITMENT #1 신고 결과 받기"
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
    코딩테스트 문제를 풀어보고 싶었당. 근데 아직 컴퓨터공학 전공 2학년까지밖에 안해성
    혼자 하기에는 조금 무섭공 뭔가 열정이 안 생길거 같았다.
    그래서 같이 스터디원들과 2 vs 2 vs 2 로 팀을 구성하여 같은 문제 풀어서 
    가장 코드를 잘 짠(알고리즘이나 뭐 시간복잡도?) 팀 순으로 순위를 매긴다.
    3등이 1등팀에게 커피를 사주는 내기를 하였다.
    사람이 상품이 걸리면 욕심이 생긴다고 1등은 내꺼다. ㅎㅎ
    <br>
    일단 <b>카카오 2022 코테 문제</b>로 대결하기로 했다!!
    <br><br>
    <b>[ 팀 구성 ]</b>
    <u1>
        <li>민기, 승제</li>
        <li>하은, 새진</li>
        <li>지안, 민주</li>
    </u1>
    <br>    
    <b>[ 커리큘럼 ]</b>
    <u1><br>
        <b>1_신고 결과 받기</b><br>
        2_k 진수에서 소수의 개수 구하기<br>
        3_주차 요금 계산<br>
        4_양궁 대회<br>
        5_양과 늑대<br>
        6_파괴되지 않은 건물<br>
        7_사라지는 발판<br>
    </u1>
</div>

## 문제#1_신고 결과 받기

### 문제 설명

신입사원 무지는 게시판 불량 이용자를 신고하고 처리 결과를 메일로 발송하는 시스템을 개발하려 합니다. 무지가 개발하려는 시스템은 다음과 같습니다.

* 각 유저는 한 번에 한 명의 유저를 신고할 수 있습니다.
   * 신고 횟수에 제한은 없습니다. 서로 다른 유저를 계속해서 신고할 수 있습니다.
   * 한 유저를 여러 번 신고할 수도 있지만, 동일한 유저에 대한 신고 횟수는 1회로 처리됩니다.

* k번 이상 신고된 유저는 즉시 게시판 이용이 정지되며, 해당 유저를 신고한 모든 유저에게 정지 사실을 메일로 발송합니다.
   * 유저가 신고한 모든 내용을 취합하여 마지막에 한꺼번에 게시판 이용 정지를 시키면서 정지 메일을 발송합니다.   
     
   

다음은 전체 유저 목록이 [“muzi”, “frodo”, “apeach”, “neo”]이고, k = 2(즉, 2번 이상 신고 당하면 이용 정지)인 경우의 예시입니다.   

|유저 ID|유저가 신고한 ID|설명|
|-------|-----------------|----|
|"muzi"|"frodo"|"muzi"가 "frodo"를 신고했습니다.|
|"apeach"|"frodo"|"apeach"가 "frodo"를 신고했습니다.|
|"frodo"|"neo"|"frodo"가 "neo"를 신고했습니다.|
|"muzi"|"neo"|"muzi"가 "neo"를 신고했습니다.|
|"apeach"|"muzi"|"apeach"가 "muzi"를 신고했습니다.|


각 유저별로 신고당한 횟수는 다음과 같습니다.



|유저 ID|신고당한 횟수|
|-------|-----------------|
|"muzi"|1|
|"frodo"|2|
|"apeach"|0|
|"neo"|2|



위 예시에서는 2번 이상 신고당한 "frodo"와 "neo"의 게시판 이용이 정지됩니다. 이때, 각 유저별로 신고한 아이디와정지된 아이디를 정리하면 다음과 같습니다.



|유저 ID|유저가 신고한 ID|정지된 ID|
|-------|-----------------|----|
|"muzi"|["frodo", "neo"]|["frodo", "neo"]|
|"frodo"|["neo"]|["neo"]|
|"apeach"|["muzi", "frodo"]|["frodo"]|
|"neo"|없음|없음|


따라서 "muzi"는 처리 결과 메일을 2회, "frodo"와 "apeach"는 각각 처리 결과 메일을 1회 받게 됩니다.



이용자의 ID가 담긴 문자열 배열 **id_list**, 각 이용자가 신고한 이용자의 ID 정보가 담긴 문자열 배열 **report**, 정지 기준이 되는 신고 횟수 **k**가 매개변수로 주어질 때, 각 유저별로 처리 결과 메일을 받은 횟수를 배열에 담아 return 하도록 solution 함수를 완성해주세요.

.
#### 제한사항
* 2 ≤ id_list의 길이 ≤ 1,000
  * 1 ≤ id_list의 원소 길이 ≤ 10
  * id_list의 원소는 이용자의 id를 나타내는 문자열이며 알파벳 소문자로만 이루어져 있습니다.
  * id_list에는 같은 아이디가 중복해서 들어있지 않습니다.
  
* 1 ≤ report의 길이 ≤ 200,000
  * 3 ≤ report의 원소 길이 ≤ 21
  * report의 원소는 "이용자id 신고한id"형태의 문자열입니다.
  * 예를 들어 "muzi frodo"의 경우 "muzi"가 "frodo"를 신고했다는 의미입니다.
  * id는 알파벳 소문자로만 이루어져 있습니다.
  * 이용자id와 신고한id는 공백(스페이스)하나로 구분되어 있습니다.
  * 자기 자신을 신고하는 경우는 없습니다.
  
* 1 ≤ k ≤ 200, k는 자연수입니다.
* return 하는 배열은 id_list에 담긴 id 순서대로 각 유저가 받은 결과 메일 수를 담으면 됩니다.




#### 입출력 예
|id_list|report|k|result|
|-------|-----------------|----|----|
|["muzi", "frodo", "apeach", "neo"]|["muzi frodo","apeach frodo","frodo neo","muzi neo","apeach muzi"]|2|[2,1,1,0]|
|["con", "ryan"]|["ryan con", "ryan con", "ryan con", "ryan con"]|3|[0,0]|


#### 입출력 예 설명



**입출력 예 #1**


문제의 예시와 같습니다.


**입출력 예 #2**


"ryan"이 "con"을 4번 신고했으나, 주어진 조건에 따라 한 유저가 같은 유저를 여러 번 신고한 경우는 신고 횟수 1회로 처리합니다. 따라서 "con"은 1회 신고당했습니다. 3번 이상 신고당한 이용자는 없으며, "con"과 "ryan"은 결과 메일을 받지 않습니다. 따라서 [0, 0]을 return 합니다.



#### 제한시간 안내
  * 정확성 테스트 : 10초

 

---

<br>
### 문제 풀이

#### 아이디어_1
- 해당 유저가 신고받은 횟수를 저장하는 number_k[]을 선언하였다. 
- report[]에서 신고자와 신고대상을 나누는 작업이 필요하다.
  - strcpy 함수를 이용하여 기존 report[]의 값을 복사한 후 strtok 함수를 통해 신고자와 신고대상의 데이터를 나누어 tmp_s[]에 저장했다.
    - 위의 과정을 코드의 편의를 위해서 str_token이라는 함수로 만듬
- tmp_s[1]에 저장된 데이터가 id_list[]에 있는지 확인해야하고 있다면 해당 index 를 알아야한다.
  - strtmp 함수를 이용하여 for 문을 돌며 id_list[]에 존재한다면 몇번째 index인지 확인하고 전역변수 ch_k에 index값을 넣어준다.
    - 위의 과정을 str_compare라는 함수로 만들어 true or false로 반환한다.
- 위에서 구한 값들을 이용하여 해당하는 신고대상의 횟수를 증가시켜준다.
  - number_k[ch_k]++ 을 통해 해당하는 인덱스가 가리키는 값에 더해준다.

<br>

- 다시 한번 반복문을 새로 돌면서 report[]에 동일한 신고자가 동일한 신고대상을 신고했다면 number_k[]에서 해당하는 index가 가리키는 값을 감소시켜준다.
  - number_k[ch_k]--

<br>

- number_k[]의 값들이 모두 채워졌다면 이제 신고기준인 k 번이상 신고 당했는가를 확인하고 맞다면 신고대상을 신고한 신고자에게 메일을 발송해야한다.
  - char mail[]을 선언하고 위에서 사용했던 str_token 함수를 이용하여 신고자와 신고대상을 구분한다.
  - 만약 신고대상이 str_compare 함수를 통해 존재하고 number_k[]에서 k번이상 신고당했다면 신고자를 str_compare 함수에 넣어 신고자의 index를 알아낸 후 answer[신고자의 index]에 증가시켜준다.
    - if (str_compare(tmp[1]) && number_k[ch_k] >= k) {
      		str_compare(tmp[0]);
        		answer[ch_k]++;
      }

<br>

- 최종적으로 answer를 반환한다.

<br>

---




#### 아이디어_1 코드

```c
#define _CRT_SECURE_NO_WARNINGS
#define BUFFER_SIZE 20

#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>


const char* id_list[] = { "muzi","frodo","apeach","neo" };
const char* report[] = { "muzi frodo","apeach frodo","frodo neo","muzi neo","apeach muzi" };
int k = 0;

size_t id_list_len = sizeof(id_list) / sizeof(id_list[0]);
size_t report_len = sizeof(report) / sizeof(report[0]);

int* number_k = (int*)malloc(id_list_len, sizeof(int));	// 제출할때는 solution에 넣으슈
int ch_k = 0;




bool str_compare(char a[]) {
	for (int i = 0; i < id_list_len; i++) {
		if (strcmp(id_list[i], a) == 0) {
			ch_k = i;
			return 1;
		}
	}
	return 0;
}

void str_token(int p,const char* report[], char a[], char* tmp[]) {
	strcpy(a, report[p]);
	char* ptr = strtok(a, " ");
	tmp[0] = ptr;
	ptr = strtok(NULL, " ");
	tmp[1] = ptr;

}

// id_list_len은 배열 id_list의 길이입니다.
// report_len은 배열 report의 길이입니다.
// 파라미터로 주어지는 문자열은 const로 주어집니다. 변경하려면 문자열을 복사해서 사용하세요.
int* solution(const char* id_list[], size_t id_list_len,const char* report[], size_t report_len, int k) {

	int* answer = (int*)malloc(id_list_len, sizeof(int));

	for (int p = 0; p < report_len; p++) {
		char same_t[30];
		char* tmp_s[2] = { NULL, };
		str_token(p, report, same_t, tmp_s);
		str_compare(tmp_s[1]);
		number_k[ch_k]++;

		for (int q = p + 1; q < report_len; q++) {
			if (strcmp(report[q], report[p]) == 0) {
				number_k[ch_k]--;
			}
		}
	
	}


	for (int i = 0; i <= id_list_len; i++) {
		char mail[30];
		char* tmp[2] = { NULL, };
		str_token(i, report, mail, tmp);
	
		if (answer != NULL) {
			if (str_compare(tmp[1]) && number_k[ch_k] >= k) {
				str_compare(tmp[0]);
				answer[ch_k]++;
			}
		}	
	}

	return answer;
}




int main() {
	int* get_mail = solution(id_list, id_list_len, report, report_len, 2);

	printf("\n*   id_list[]   *\n");
	printf(" [");
	for (int i = 0; i < id_list_len; i++) {
		printf(" %s ", id_list[i]);
	}
	printf("]");
	printf("\n");


	
	printf("\n*   report[]   *\n");
	printf(" [");
	for (int j = 0; j < report_len; j++) {
		printf(" %s, ", report[j]);
	}
	printf("]");
	printf("\n");


	printf("\n*   number_k[]   *\n");
	printf(" [");
	for (int i = 0; i < id_list_len; i++) {
		printf(" %d ", number_k[i]);
	}
	printf("]");
	printf("\n");


	printf("\n*   answer[]   *\n");
	printf(" [");
	for (int j = 0; j < id_list_len; j++) {
		printf(" %d ", get_mail[j]);
	}
	printf("]");

}
```



---

<br>

#### 아이디어_2

- 기존의 방식은 number_k[]를 이용하여 신고받은횟수를 따로 count하고 다시 report를 읽어서 신고자와 신고대상을 분리하여 해당 신고대상이 k번 이상 신고 당했는지 확인하는 구조였다.
  - 이 과정이 비효율적이여서 새로운 방법을 찾다가 이차원 배열을 써보기로 하였다.
  - id_list[]의 index 크기만큼 이차원배열을 할당하여 신고자를 행, 신고대상을 열에 두어 한 눈에 신고자와 신고대상을 구분할 수 있게 하였고 신고횟수 또한 보기 쉽게  하였다.
    - 저번처럼 strtok 함수를 여러번 사용하여 report[]를 이용하는 것이 아니라 한 번 사용으로 신고자와 신고대상을 구분하고 곧바로 비교하여 해당하는 행과 열의 index를 구하고 행과 열의 index 값이 가리키는 이차원배열의 값에 1을 넣었다.
      - strtok 함수를 통해 신고자와 신고대상을 분리하여 index1, index2 값으로 받는다.
        - if (strcmp(id_list[j], report_strtok) == 0) {
          		index1 = j;
            		break;
          }
        - if (strcmp(id_list[j], report_strtok) == 0) {
          		index2 = j;
            		break;
          }
      - 행과 열의 index 값이 가리키는 이차원 배열의 값에 1을 넣었다.
        - ch [index1] [index2] = 1;
    - 신고횟수 k 번 이상인지 판단하기 위한 result[]을 동적할당한다.
      - 이차원 배열의 값이 1이라면 해당하는 열의 index값을 result[]의 index로 하여 1 더해준다.
        - if (ch[i] [j] == 1) result[j] += 1;
      - 그 후 result[]의 값이 신고 횟수 k 번 이상이고 해당하는 행,열이 가리키는 이차원 배열의 값이 1일 때 anwer[]에 행의 값을 index으로 주어 1 더해준다.
        - if (result[j] >= k) {
          		for (i = 0; i < id_list_len; i++) {
            			if (ch[i] [j] == 1) answer[i] += 1;
            		}
          }
    - 최종적으로 answer[]를 반환한다.

<br>

---

#### 아이디어_2 코드

```c
#define _CRT_SECURE_NO_WARNINGS
#define BUFFER_SIZE 20

#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

const char* id_list[] = { "muzi", "frodo", "apeach", "neo" };
const char* report[] = { "muzi frodo","apeach frodo","frodo neo","muzi neo","apeach muzi" };

size_t id_list_len = sizeof(id_list) / sizeof(id_list[0]);
size_t report_len = sizeof(report) / sizeof(report[0]);


int* solution(const char* id_list[], size_t id_list_len, const char* report[], size_t report_len, int k) {

	int** ch;
	int i, j;
	ch = (int**)malloc(sizeof(int*) * id_list_len);
	for (int i = 0; i < id_list_len; i++) {
		if (ch != NULL) {
			ch[i] = (int*)malloc(sizeof(int) * id_list_len);
		}
	}

	for (i = 0; i < report_len; i++) {
		char* report_strtok;
		char report_copy[20];
		strcpy(report_copy, report[i]);

		report_strtok = strtok(report_copy, " ");
		int index1 = 0;
		for (j = 0; j < id_list_len; j++) {
			if (strcmp(id_list[j], report_strtok) == 0) {
				index1 = j;
				break;
			}
		}

		report_strtok = strtok(NULL, " ");
		int index2 = 0;
		for (j = 0; j < id_list_len; j++) {
			if (strcmp(id_list[j], report_strtok) == 0) {
				index2 = j;
				break;
			}
		}

		ch[index1][index2] = 1;
	}

	int* result = (int*)calloc(id_list_len, sizeof(int));
	int* answer = (int*)calloc(id_list_len, sizeof(int));
	for (j = 0; j < id_list_len; j++) {
		for (i = 0; i < id_list_len; i++) {
			if (ch[i][j] == 1) result[j] += 1;
		}
		if (result[j] >= k) {
			for (i = 0; i < id_list_len; i++) {
				if (ch[i][j] == 1) answer[i] += 1;
			}
		}
	}

	for (i = 0; i < id_list_len; i++) {
		free(ch[i]);
	}
	free(ch);
	free(result);
	return answer;
}

int main() {
	int* get_mail = solution(id_list, id_list_len, report, report_len, 2);

	printf("\n*   id_list[]   *\n");
	printf(" [");
	for (int i = 0; i < id_list_len; i++) {
		printf(" %s ", id_list[i]);
	}
	printf("]");
	printf("\n");



	printf("\n*   report[]   *\n");
	printf(" [");
	for (int j = 0; j < report_len; j++) {
		printf(" %s, ", report[j]);
	}
	printf("]");
	printf("\n");

	printf("\n*   answer[]   *\n");
	printf(" [");
	for (int j = 0; j < id_list_len; j++) {
		printf(" %d ", get_mail[j]);
	}
	printf("]");

}
```



<br>

---
## 후기
<div class="notice--success">
최종적으로 나와 승제의 <b>아이디어_2 코드</b>가 1등을 하였다.!!!
처음 코딩테스트 문제를 풀다보니 막막하기도 했고 프로그래머스에서 테스트를 돌렸을 때 4.2프로의 정확률을 보고 많이 좌절하였다.
포기하지 않고 다양한 방법으로 접근하면서 시도해본 결과 시간은 오래 걸렸지만 결국은 해낼 수 있었다.
또한 코드 완성 후에 팀끼리 피드백하는 시간에 승제가 시간복잡도를 고려하여 피드백을 주었을 때 미쳐 내가 생각하지 못한 부분이 많았었다.
승제의 피드백으로 코드를 보완하여 시간복잡도를 줄일 수 있었다. 단순히 break하나와 for문을 합치는 과정만으로도 큰 도움이 되었다.
혼자서 문제를 고민하고 할 때 보다 같이 코드를 보며 분석하니 조금더 보완해나갈 부분이 많은 것을 느낄 수있었당
하여튼 완벽한 팀워크를 통해 우리는 1등했당.
공짜 커피 마실 생각에 벌써 설렌다. ㅎㅎ
</div>
