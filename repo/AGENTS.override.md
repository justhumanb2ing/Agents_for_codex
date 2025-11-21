# AGENTS.md

## 개요
Next.js 16(App Router)·Supabase 중심의 모듈화, TDD, 유지보수 용이성.
목표: **명확성**, **확장성**, **신뢰성**.

## 핵심 원칙
- 낮은 결합도·높은 응집도.
- 데이터 로직과 UI 표현 분리.
- Server-first, 최소 JS 번들.
- 핵심 함수/서비스에 JSDoc 의무.
- 기능 구현/변경 시 Markdown 문서화.

## 폴더 구조
/app, /components, /components/ui, /services, /lib, /config, /tests, /types
각 폴더 역할을 README.md로 문서화하고 엔티티는 JSON Schema로 정리.

## 컨벤션
- TypeScript strict, any 금지.
- 파일명 kebab-case, 컴포넌트/페이지 PascalCase.
- Conventional Commits 규칙을 따른다.
- SSR 우선, React Query 등 클라이언트 상태관리 미사용.
- .env.example은 .env.local과 반드시 동기화되어야 한다.

## PR 가이드
제목: <type>: 요약
본문: 문제, 접근, 테스트, 위험, 롤백 계획.

## 안전
- 테스트는 네트워크 호출 금지(mock).
- 저장소 루트 밖 쓰기 금지.
- 파괴적 명령은 명시적으로 요청된 경우에만.
