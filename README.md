
# 🔒 Alsumddak

<2025 오픈소스 개발자대회 참가작 / 개인정보 보호 오픈소스 프로젝트>

<img width="1920" height="872" alt="image" src="https://github.com/user-attachments/assets/3201d7b5-88fc-4586-9ad9-a4bd4bc04cde" />


---

## 👋 Team Introduce

| 이름  | 역할 (팀장, 디자인, FE, BE, AI) | 트랙   | 학과           | 학번 |
| --- | ------------------------ | ---- | ------------ | -- |
| 유호준 | 팀장 / AI                  | 인공지능 | 컴퓨터공학과       | 23 |
| 이제혁 | AI                       | 인공지능 | 컴퓨터공학과       | 20 |
| 정해윤 | AI                       | 인공지능 | 산업시스템공학과     | 24 |
| 백승빈 | BE                       | 보안/웹 | 정보통신공학과      | 19 |
| 박혜린 | BE                       | 보안/웹 | 컴퓨터공학과       | 23 |
| 김수빈 | FE                       | 보안/웹 | 불교학부         | 21 |
| 예원  | Design                   | 보안/웹 | 미디어커뮤니케이션학전공 | 23 |

---

## 📖 About Alsumddak


**생성형 AI에 포함되는 민감정보를 자동 탐지·마스킹하는 오픈소스 솔루션**


<img width="1920" height="872" alt="image" src="https://github.com/user-attachments/assets/3201d7b5-88fc-4586-9ad9-a4bd4bc04cde" />

&nbsp;

최근 **생성형 AI의 활용이** 급격히 확산되면서, 사용자 입력(프롬프트)에 이름·계좌번호·연락처와 같은 민감정보가 그대로 외부로 유출될 위험이 커지고 있습니다. 이에 본 프로젝트는 이를 해결하기 위해 **정규표현식 + KoELECTRA NER 모델**을 활용하여 개인정보를 자동 탐지하고, 문맥을 보존한 채 안전하게 마스킹하는 기능을 제공합니다.

&nbsp;

---

## ✨ 주요 기능

1. 🔍 **지능형 개인정보 자동 탐지**

   * 단순히 정규표현식(regex)으로만 탐지하지 않고, **KoELECTRA 기반 NER 모델**을 함께 활용하여 다양한 개인정보(이름, 계좌번호, 연락처 등)를 정밀하게 식별합니다.
   * 특히 이 프로젝트는 **탐지 과정 자체에서도 개인정보가 외부로 유출되지 않도록 전처리 단계에서 AI를 활용**합니다. 즉, LLM에게 그대로 노출되기 전에 선제적으로 보호막을 형성하는 구조라 기존 보안 도구와 차별화됩니다.
   * 
<div align="center">
  <img src="https://github.com/user-attachments/assets/159b7086-37da-46e8-82d4-751ed3482b04" alt="탐지 예시 이미지" width="80%" />
</div>

2. 🛡️ **문맥 기반 마스킹 (Randomized Masking)**
   * 
   * 기존에 개인정보를 유사 맥락의 대체 값으로 변경하는 방식은 때때로 문맥상의 오류를 일으키는 문제가 있었습니다. 
   * 이러한 점을 개선하기 위해, 이제는 개인정보를 '항목명'으로 대체하여 문맥의 의미 손실을 최소화합니다.
   * 단순히 "***" 같은 기호로 가리거나 유사한 의미의 단어로 바꾸는 대신, 생성형 AI가 쉽게 이해할 수 있는 항목명으로 변경합니다.
      예: 국민은행 → [은행명] / 홍길동 → [이름]
   * 이러한 방식을 사용하면 AI 모델이 프롬프트를 처리할 때 내용의 흐름을 방해하지 않고도 개인정보를 안전하게 보호할 수 있습니다.
   * *\[Demo GIF 자리]*
     
<div align="center">
  <img src="https://github.com/user-attachments/assets/54d37d1e-d829-450e-a1df-00738bbcbbf2" alt="마스킹 예시 이미지" width="80%" />
</div>

3. 👆 **사용자 선택적 원문 확인 및 보호 강도 조절**

   * 마스킹된 항목을 **클릭하면 원문을 확인**할 수 있어, 사용자가 필요할 때만 실제 데이터를 열람할 수 있습니다.
   * 사용자는 **마스킹 강도를 직접 설정**할 수 있습니다.

     * 예: 모든 개인정보 마스킹 / 이름만 표시 / 계좌번호 일부만 마스킹 등
   * 이를 통해 **보안성과 편의성 사이의 균형**을 사용자가 직접 선택할 수 있습니다.
  

4. 🧩 **사용자 맞춤 템플릿 제공**

   * 자주 쓰이는 입력 형태(예: 이력서 첨삭, 메일 작성, 요약 요청 등)를 **템플릿으로 제공**하여 사용자가 안전하게 프롬프트를 작성할 수 있습니다.
   * 사용자는 목적에 맞는 템플릿을 선택하고, 개인정보 마스킹이 자동 적용된 프롬프트를 바로 활용할 수 있습니다.


https://github.com/user-attachments/assets/4a67faba-d1ad-4346-ab66-3cfa3aba74c1


5. 🌐 **크롬 확장 프로그램 지원**

   * 별도의 프로그램 설치 없이, **웹 브라우저 환경에서 곧바로 마스킹 기능을 적용**할 수 있습니다.
   * ChatGPT, Claude, Gemini 등 웹 기반 LLM 서비스에 바로 연결 가능하여 **실사용자 친화적인 접근성**을 보장합니다.
   * 또한 오픈소스 프로젝트로 확장성이 뛰어나, 누구나 기여하고 개선할 수 있는 구조입니다.

6. 🧠 **개인정보 없이도 사용 이력 저장 가능**

   * 프롬프트 저장 기능은 상태 관리 방식으로 구현되어, **개인 식별 정보 없이도** 사용 이력을 저장할 수 있습니다.
   * 이로 인해 서버에 별도 개인정보가 저장되지 않아 **유출 위험을 원천적으로 차단**할 수 있습니다.

---

## 🖥️ Architecture

<div align="center">
<img width="562" height="371" alt="image" src="https://github.com/user-attachments/assets/a933b745-ed30-4a6b-8df8-3cc7de972132" />
</div>

---

## ⚡ Skills

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square\&logo=python\&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square\&logo=pytorch\&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FCC624?style=flat-square\&logo=huggingface\&logoColor=black)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square\&logo=react\&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square\&logo=vite\&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square\&logo=node.js\&logoColor=white)
![Chrome](https://img.shields.io/badge/Chrome_Extension-4285F4?style=flat-square\&logo=googlechrome\&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square\&logo=docker\&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square\&logo=github\&logoColor=white)

---

## 🎯 Repository Guide

* **브랜치 전략**

  * `main` ← 배포용
  * `develop` ← 통합 개발
  * `ai` / `server` / `client` ← 기능별 브랜치

* **커밋 컨벤션 (Conventional Commits)**

  * `feat`: 새로운 기능 추가
  * `fix`: 버그 수정
  * `refactor`: 리팩토링
  * `docs`: 문서 작성
  * `chore`: 설정 / 기타 작업

* **PR 규칙**

  * 작업 단위별 PR → 최소 1명 리뷰 후 머지
  * 템플릿 기반 (PR 설명, 체크리스트, 관련 이슈 링크 포함 필수)

---

## 📌 License

MIT License


