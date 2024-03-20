---
title:  "[JS] 회전하는 사각형"
date:   2024-03-20 21:44:00 +0900
categories: JS
---

## 🎠 프로젝트 소개

- x, y, z축으로 회전하는 3D 큐브(사각형)
- 자바스크립트와 HTML(캔버스) 사용


## ⚽ 프로젝트 계기

- 유튜브에서 [도넛을 회전시키는 영상](https://www.youtube.com/watch?v=rj7DOPPTkQA&ab_channel=ServetGulnaroglu)을 보고 비슷한 프로그램을 만들고 싶어서 시작함.


## 📡 실행 주소

[https://wkd3ogks.github.io/Spinning-Cube/](https://wkd3ogks.github.io/Spinning-Cube/)

## 🔑 핵심 개념

> 3D 좌표를 2D로 변환하는 공식(d는 화면의 좌표, z는 사물의 좌표)

- 원점(기준)은 **사람의 눈**이다.
  
![image](https://github.com/wkd3ogks/wkd3ogks.github.io/assets/91067033/f0fcb311-3a45-4b46-a08c-a40aab4a716a)

> 축을 기준으로 회전하는 공식

![image](https://github.com/wkd3ogks/wkd3ogks.github.io/assets/91067033/5e6215b6-b8f6-491f-a363-68c16afbb372)

- 회전 방향은 단위원을 기준으로 값의 변화를 관찰하면 알 수 있었다.
- 아래 사진은 해당 프로그램에서 사용된 축 방향 및 회전 방향이다.
  
![image](https://github.com/wkd3ogks/wkd3ogks.github.io/assets/91067033/69082fa5-7f22-49a1-972e-f7e2f149adae)

**회전을 할 때에는 사각형의 중심을 원점으로 보고 2D로 변환할 때는 사람의 시점을 원점으로 둔다**

- 축의 방향은 그대로 두기에 눈을 기준으로한 화면의 좌표와 사각형 중심(원점)의 좌표는 음수로 나타난다.


## 실행 화면
![image](https://github.com/wkd3ogks/wkd3ogks.github.io/assets/91067033/96d6e6db-c406-4ba4-83f0-75f4b6aacb02)

