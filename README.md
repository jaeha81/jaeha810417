# JH Interior Web App

React + Vite + TypeScript 기반으로 GPT가 생성한 `HomeApp` 컴포넌트를 실행할 수 있는 프로젝트입니다.  
Tailwind CSS, shadcn/ui, lucide-react를 설치하고 OpenRouter · Google Apps Script 연동을 위해 환경 변수를 사용합니다.

## 기술 스택

- Vite + React 19 + TypeScript
- Tailwind CSS · tailwindcss-animate
- shadcn/ui 스타일 가이드 (New York) + 커스텀 UI 컴포넌트
- lucide-react, class-variance-authority, clsx, tailwind-merge
- OpenRouter API, Google Apps Script Webhook

## 설치 방법

```bash
# 의존성 설치
npm install

# 개발 서버
npm run dev

# 타입 검사 + 번들
npm run build

# ESLint
npm run lint
```

## 환경 변수

루트에 `.env` 파일을 생성하고 아래 값을 채워 주세요. (샘플이 이미 포함되어 있습니다.)

```dotenv
VITE_OPENROUTER_KEY=sk-or-여기에API키입력
VITE_SHEET_ENDPOINT=https://script.google.com/macros/s/ID/exec
```

- OpenRouter 키는 [OpenRouter](https://openrouter.ai/)에서 발급 받은 실제 키로 교체하세요.
- `VITE_SHEET_ENDPOINT`에는 Google Apps Script Web App의 `doGet/doPost` URL을 적어야 합니다.

## 주요 폴더 구조

```
src/
 ├─ App.tsx            # HomeApp 래퍼
 ├─ HomeApp.tsx        # GPT가 생성한 메인 컴포넌트
 ├─ components/ui      # shadcn/ui Button, Card, Input, Textarea
 ├─ lib/utils.ts       # tailwind-merge 기반 유틸
 └─ index.css          # Tailwind + CSS 변수
tailwind.config.ts     # content 경로 및 shadcn 테마
components.json        # shadcn/ui CLI 설정
```

## shadcn/ui 사용하기

필요한 추가 컴포넌트는 아래처럼 설치할 수 있습니다.

```bash
npx shadcn@latest add button card input textarea
```

이미 Button/Card/Input/Textarea는 프로젝트에 포함되어 있으므로 나머지 컴포넌트만 추가하면 됩니다.

## 배포 체크리스트

- `.env`에 실제 API 키/웹훅 URL이 있는지 확인하세요.
- `npm run build`로 프로덕션 번들이 정상 생성되는지 확인합니다.
- OpenRouter, Google Apps Script가 올바르게 응답하는지 E2E 테스트를 수행하세요.

필요에 따라 `HomeApp.tsx`의 프롬프트, UI 카피, 요청 필드 등을 자유롭게 수정해 사용할 수 있습니다.
