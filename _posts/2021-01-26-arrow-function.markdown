---
layout: post
title: "함수의 화살표 표기법"
date: "2021-01-23"
categories: Javascript
---

ES6 버전부터는 화살표 표기법을 사용해서 함수 선언을 좀 더 간편하게 사용할 수 있다.
주로 **이름 없는 함수(익명 함수)를 변수에 지정할 때** 많이 사용하며, function 예약어는 사용하지 않는다.

* 매개변수가 없거나 2개 이상일 경우, 괄호 표기
* 매개변수가 1개일 때는 괄호 생략
* return 생략

&nbsp;

## 매개변수가 없을 경우

```javascript
// 기존 함수 표기법
var hello = function() {
  return 'Hello, soyoung';
}
hello();

// 화살표 표기법 (ES6)
var hello = () => 'Hello, soyoung';

hello();
```

&nbsp;

## 매개변수가 1개일 경우

```javascript
// 기존 함수 표기법
var welcome = function(name) {
  return name + '님 환영합니다!'
}
welcome('소영');

// 화살표 표기법 (ES6)
var welcome = name => `${name}님 환영합니다!`;

welcome('소영');
```

&nbsp;

## 매개변수가 2개일 경우

```javascript
// 기존 함수 표기법
var add = function(a, b) {
  return a + b;
}
add(5, 10);

// 화살표 표기법 (ES6)
var add = (a, b) => a + b;

add(5, 10);
```
