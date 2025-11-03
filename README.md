# 🧩 Vue.js Study

[![Notion](https://img.shields.io/badge/Notion-Study_Log-black?logo=notion&style=flat)](https://nettle-pilot-25c.notion.site/Vue-js-2a0178c4afac80b59c44e09c42a0aa90)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-42b883?logo=vue.js&logoColor=white)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Bundler-Vite-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **“React만 하는 개발자가 아닌, 프론트엔드 전반을 이해하는 개발자.”**  
> Vue.js 학습을 통해 프레임워크의 철학과 구조를 통합적으로 이해하는 것을 목표로 합니다.

---

## 🎯 학습 목적

| 목표                    | 설명                                                                                           |
| ----------------------- | ---------------------------------------------------------------------------------------------- |
| 🧠 프레임워크 사고 확장 | React, Vue, Svelte 등 서로 다른 구조를 비교하며 “프레임워크가 해결하려는 문제” 자체를 이해하기 |
| ⚙️ 상태 관리 이해       | React의 `useState`, Vue의 `ref`처럼 각 프레임워크의 반응형 시스템 구조를 비교                  |
| 🧩 구조적 사고력 향상   | React의 Hooks / Vue의 Composition API / Angular의 DI 등 구조적 접근을 통합적으로 이해          |
| 🧭 생산성 향상          | 프로젝트 상황에 맞는 도구를 선택할 수 있는 시야 확보                                           |

---

## 🧰 기술 스택

- **Vue 3 + Vite**
- Composition API (`<script setup>`)
- LocalStorage Persistence
- Vanilla CSS
- Node.js 18+

---

## 🧠 학습 주제

| 주제                          | 설명                                                                          |
| ----------------------------- | ----------------------------------------------------------------------------- |
| ✅ `ref`, `computed`, `watch` | Vue의 반응형 시스템 핵심. React의 `useState`, `useMemo`, `useEffect`와 대응됨 |
| 🧱 Composition API            | 함수 기반 구조로, React Hooks처럼 로직을 재사용 가능하게 함                   |
| 🎨 Template Syntax            | JSX 대신 직관적인 템플릿 기반 UI 선언 방식                                    |
| 💾 LocalStorage               | 서버 없이 브라우저에 상태 저장하기                                            |
| 🔄 Routing & Componentization | Vue Router, SFC 구조 이해                                                     |

---

## 📚 학습 기록

🗂️ [**Notion 정리 링크 바로가기**]([https://your-notion-link-here](https://nettle-pilot-25c.notion.site/Vue-js-2a0178c4afac80b59c44e09c42a0aa90))

> 학습 개념 정리, React와 Vue의 구조적 차이 분석, 예제 코드 정리 등 기록

---

## 🧑‍💻 실습 1 — To-Do List

> React에서 이미 구현해 본 To-Do List를 Vue로 다시 구현하여  
> “동일한 기능을 다른 프레임워크에서 어떻게 구조화하는가”를 실습합니다.

| 기능                 | 설명                             |
| -------------------- | -------------------------------- |
| ➕ 할 일 추가        | 입력 후 Enter로 새로운 todo 추가 |
| ✅ 완료 토글         | 체크박스로 완료 상태 변경        |
| 🗑️ 삭제              | 리스트에서 todo 삭제             |
| ✏️ 수정              | 더블클릭 또는 버튼으로 내용 수정 |
| 💾 LocalStorage 저장 | 새로고침 후에도 유지             |

---

## 🧩 React vs Vue 개념 대응표

| Vue              | React                   | 설명                |
| ---------------- | ----------------------- | ------------------- |
| `ref()`          | `useState()`            | 반응형 상태 관리    |
| `computed()`     | `useMemo()`             | 파생 상태 자동 계산 |
| `watch()`        | `useEffect()`           | 특정 값 변화 감시   |
| `<template>`     | JSX                     | UI 선언 문법        |
| `<script setup>` | 함수형 컴포넌트         | 로직 및 상태 정의   |
| `v-for`, `v-if`  | `.map()`, 조건부 렌더링 | 템플릿 제어 문법    |

---

## 🚀 학습 로드맵

1. [x] Vue 프로젝트 초기 세팅 (Vite)
2. [x] To-Do List 기본 CRUD 구현
3. [ ] Composition API 심화 (`reactive`, `watchEffect`, `toRefs`)
4. [ ] Vue Router로 페이지 분리
5. [ ] Pinia 상태관리 실습
6. [ ] Tailwind CSS 적용
7. [ ] React와의 구조적 비교 정리
8. [ ] Vue + Firebase 간단 배포

---

## 💬 개인 메모

> “프레임워크를 배우는 건 새로운 문법을 익히는 게 아니라,  
> ‘문제를 바라보는 관점’을 확장하는 일이다.”

---

© 2025 HaeWon — Frontend Developer studying Vue with curiosity 💚
