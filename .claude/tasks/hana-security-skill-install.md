# HANA 보안 지시서: 스킬 설치 검증 강화

## 목표
`src/agents/skills-install.ts`에 보안 검증 3가지를 추가합니다.

## 배경
MIRU 리서치 결과: 현재 스킬 설치에 URL/해시/크기 검증이 없음.
상세: `.claude/tasks/miru-skill-verification-research.md` 참조

## 구현 항목 (우선순위순)

### 1. SHA-256 체크섬 검증
- install spec에 `sha256` 필드 추가 (`src/agents/skills/types.ts`)
- 다운로드 후 해시 비교, 불일치 시 설치 중단 + 파일 삭제
- `sha256` 필드 없으면 경고 로그 출력 후 계속 (하위 호환성)

### 2. HTTPS 강제
- `skills-install.ts` download 로직에서 URL 스키마 검증
- `http://` URL은 거부 (에러 + 메시지)
- `file://` 로컬 경로는 허용

### 3. 다운로드 크기 제한
- 기본값: 50MB
- config로 조정 가능: `config.skills.maxDownloadSize`
- 스트리밍 다운로드 중 크기 초과 시 중단

## 참고 파일
| 파일 | 역할 |
|------|------|
| `src/agents/skills-install.ts:147-277` | 다운로드 설치 로직 |
| `src/agents/skills/types.ts` | 타입 정의 (sha256 필드 추가) |
| `src/plugins/install.ts` | 참고: plugin 검증 패턴 (롤백 등) |

## 테스트
- `src/agents/skills-install.test.ts`에 추가:
  - SHA-256 불일치 시 설치 실패
  - HTTP URL 거부
  - 크기 초과 시 중단

## 제약
- 기존 스킬 설치 하위 호환성 유지 (sha256 없는 스킬도 설치 가능)
- NPM 설치 로직은 이번 스코프 밖
