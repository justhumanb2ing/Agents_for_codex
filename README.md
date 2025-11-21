# Agents for Codex

Next.js 16(App Router)과 Supabase를 전제로, 도메인별 작업 지침을 폴더별 `AGENTS.override.md`에 모아둔 메모리 리포지토리다. AI 에이전트가 어느 영역을 다루든 일관된 원칙을 참조하고, 코드·문서 작업 흐름을 맞추는 것이 목적이다. 폴더와 파일의 역할은 아래와 같다.

## 폴더 구조 및 역할
- `global/`: 전 영역에 공통으로 적용되는 작업 합의 사항.
- `repo/`: 레포 전체의 아키텍처 원칙·컨벤션·PR 가이드.
- `frontend/`: App Router 기반의 서버 우선 렌더링, 캐시·무효화 정책, 상태 관리 기준.
- `component/`: UI 컴포넌트 스타일 가이드와 네이밍 규칙.
- `service/`: 서비스 계층 설계 원칙과 공통 품질 기준.
- `backend/`: Supabase 스키마 변경과 타입/프론트 반영까지 이어지는 자동화 흐름.
- `test/`: 테스트 범위, 네트워크 모킹, DX 원칙.

## 폴더별 `AGENTS.override.md` 역할
| 경로 | 실제 위치(1행 안내) | 역할 | 주요 초점 |
| --- | --- | --- | --- |
| `global/AGENTS.md` | `~/.codex/AGENTS.md` | 모든 작업자가 따라야 할 공통 원칙을 정의 | JS/TS 수정 후 테스트, bun 우선, 비파괴적 명령, 루트 밖 쓰기 금지, 테스트 네트워크 모킹 |
| `repo/AGENTS.override.md` | `AGENTS.md` | 레포 전반의 기본 철학과 컨벤션 제시 | Next.js+Supabase 지향, 느슨한 결합·높은 응집, JSDoc·Markdown 문서화, TypeScript strict, Conventional Commits |
| `frontend/AGENTS.override.md` | `app/AGENTS.md` | 앱 레이어 작업 가이드 | 서버 컴포넌트 중심 데이터 처리, 빈/에러/로딩 상태 명시, 캐시 태그 기반 재검증, 제한적인 상태 관리 |
| `component/AGENTS.override.md` | `components/AGENTS.md` | UI 컴포넌트 제작 규칙 | TailwindCSS 기반 빠른 스타일링, 주요 섹션 분리, shadcn/ui 우선, 파일·컴포넌트 네이밍 준수 |
| `service/AGENTS.override.md` | `services/AGENTS.md` | 서비스/도메인 로직 기준 | 기능 단위 구조화, 낮은 결합도·높은 응집도, 핵심 함수 JSDoc, 공통 로깅·에러 트래킹·관찰성 |
| `backend/AGENTS.override.md` | `config/supabase/AGENTS.override.md` | Supabase 스키마 변경 파이프라인 | 마이그레이션 작성, RLS 템플릿, `push.sh` 자동 관리, 타입 영향/프런트 영향/문서/필수 명령 출력 순서 |
| `test/AGENTS.override.md` | `tests/AGENTS.override.md` | 테스트 전략과 제한 규정 | 단위·통합 테스트 중심, 컴포넌트·서비스별 대응 테스트, 네트워크 호출 모킹, 명확하고 예측 가능한 테스트 지향 |

## 사용법
- 특정 영역을 작업하기 전에 해당 폴더의 `AGENTS.override.md`를 읽고 따라야 할 규칙을 확인한다.
- 공통 합의가 필요한 경우에는 `global/AGENTS.override.md`에 명시된 항목을 우선한다.
