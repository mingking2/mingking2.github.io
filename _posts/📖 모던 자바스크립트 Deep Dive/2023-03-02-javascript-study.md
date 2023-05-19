---
layout: single
title: "[JS] javaScript Study"
categories: javaScript
tag: [JS, HTML, CSS, WEB]

toc: true
author_profile: false
sidebar:
    nav: "counts"
---

# 📖 모던 자바스크립트 Deep Dive

![**모던 자바스크립트 Deep Dive (이웅모 저)**](/images/2023-03-02-javascript-study/Untitled.png)

**모던 자바스크립트 Deep Dive (이웅모 저)**

---

## **스터디 진행 방식**

- 자바스크립트 책으로 격주간 공부할 범위를 스터디원들과 함께 결정
- 격주에 한 번 공부한 내용을 바탕으로, 회고록 발표 및 팀원 중 한명이 이론을 구현한 코드 리뷰 + (지난 발표때 팀원이 구현한 코드를 자신이 구현해와서 코드 리뷰)
- 자신이 구현한 코드는 나머지 팀원들이 다음 발표 전까지 똑같이 구현 해와야 함 (**컨닝 X**).

<aside>
⭐ **필수

1.** 회고록의 경우 2개 이상의 주제를 가지고 발표
2. 팀원이 구현한 코드를 자신의 방식으로 코드를 구현
2-1. 이론을 구현한 코드의 경우 할 수 있다면 어렵게 해도 상관없음

</aside>

---

## 기타

- 가끔 나도 회고록 발표함. 그리고 내가 문제 낼 수도 있음.
    
    문제 예시) [💻 비동기 요청 처리](https://www.notion.so/f666652a1a6646ecbbd61875866ab7ee)  
    
- 정원 - 최대 3명

---

## 회고록 및 코드 구현 예시

[회고록 예시.hwp](%F0%9F%93%96%20%E1%84%86%E1%85%A9%E1%84%83%E1%85%A5%E1%86%AB%20%E1%84%8C%E1%85%A1%E1%84%87%E1%85%A1%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B8%E1%84%90%E1%85%B3%20Deep%20Dive%202817ff98978a42ecb503935d5a944375/%25ED%259A%258C%25EA%25B3%25A0%25EB%25A1%259D_%25EC%2598%2588%25EC%258B%259C.hwp)

```jsx
// 정규표현식을 이용한 아이디, 비밀번호 유효성 검사

const id = document.querySelector("#id");
const password = document.querySelector("#password");
const toggle = document.querySelector("#toggle");
const submit = document.querySelector("#submit");
const paragraph = document.querySelector("p");

let onToggle = true;

toggle.onclick = () => {
  if (onToggle) {
    toggle.textContent = "invisible";
    password.type = "text";
  } else {
    toggle.textContent = "visible";
    password.type = "password";
  }

  onToggle = !onToggle;
};

submit.onclick = () => {
  try {
    const { statusID, statusPWD } = checkReg(id.value, password.value);

    if (statusID && statusPWD) {
      paragraph.textContent = "Success!";
    } else {
      paragraph.textContent = `ID: ${statusID}, PW: ${statusPWD}`;
    }
  } catch (e) {
    console.log(`Error: ${e}`);
  }
};

function checkReg(id, password) {
  /**
   * ^: ~로 시작
   * (?:) 비포괄적 괄호, 기억하지 않기때문에, 실패시 바로 탈락
   * (?=.*[A-Za-z]) 임의의 문자가 0개이상 반복되고, 문자가 최소 하나 포함되어 있는지 확인
   * (?=.*\d) 임의의 문자가 0개이상 반복되고, 숫자가 최소 하나 포함되어 있는지 확인
   * [A-Za-z\d].{n,} 대괄호 내부의 문자와 숫자가 n번 이상 반복되었는지 확인
   */
  const regExpID = /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d].{3,}$/;
  const regExpPW =
    /^(?=.*[A-Z])(?=.*[a-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]*$/;
  const status = { statusID: checkID(), statusPWD: checkPWD() };

  return status;

  function checkID() {
    if (id.length >= 4 && regExpID.test(id)) {
      return true;
    }
    return false;
  }

  function checkPWD() {
    if (password.length >= 8 && regExpPW.test(password)) {
      return true;
    }
    return false;
  }
}

```

---

[01장 프로그래밍](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-03-09-javascript01.md)

[02장 자바스크립트란?](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-03-16-javascript02.md)

[03장 자바스크립트 개발 환경과 실행 방법](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-03-23-javascript03.md)

[04장 변수](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-03-24-javascript04.md)

[05장 표현식과 문](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-03-30-javascript05.md)

[06장 데이터 타입](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-04-03-javascript06.md)

[07장 연산자](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-04-10-javascript07.md)

[08장 제어문](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-04-13-javascript08.md)

[09장 타입 변환과 단축 평가](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-04-18-javascript09.md)

[10장 객체 리터럴](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-04-27-javascript10.md)

[11장 원시 값과 객체의 비교](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-01-javascript11.md)

[12장 함수](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-02-javascript12.md)

[13장 스코프](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-03-javascript13.md)

[14장 전역 변수의 문제점](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-04-javascript14.md)

[15장 let, const 키워드와 블록 레벨 스코프](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-04-javascript14.md)

[16장 프로퍼티 어트리뷰트](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-06-javascript16.md)

[17장 생성자 함수에 의한 객체 생성](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-07-javascript17.md)

[18장 함수와 일급 객체](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-10-javascript18.md)

[19장 프로토타입](/_posts/%F0%9F%93%96%20%EB%AA%A8%EB%8D%98%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20Deep%20Dive/2023-05-12-javascript19.md)