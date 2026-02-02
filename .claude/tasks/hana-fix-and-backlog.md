# HANA 지시: 테스트 수정 + BACKLOG 상위 2건

## 발신: SENA (PM)
## 우선순위: 높음
## 선행조건: 없음 (즉시 시작)

---

## 목표
테스트 실패 2건 수정 + BACKLOG 상위 보안 이슈 2건 처리

## 작업

### 1. 테스트 실패 수정
- 파일: `src/agents/tools/sessions-spawn-tool.auto-discover.test.ts`
- 원인: vi.mock 관련 이슈로 추정
- `pnpm test` 해당 파일 통과 확인 후 다음 작업 진행

### 2. BACKLOG 상-1: 스킬 설치 코드 검증
- 파일: `src/agents/skills-install.ts`
- 문제: 스킬 설치 시 코드 검증/서명 확인 워크플로우 없음, trusted skill allowlist 부재
- 최소 구현: trusted skill allowlist 체크 로직 추가
- 테스트 추가 필수

### 3. BACKLOG 상-2: gateway auth rate limiting
- 파일: `src/gateway/auth.ts`
- 문제: 인증 실패 시 카운터/지연 로직 없음
- 구현: 실패 카운터 + 지연/차단 로직
- 테스트 추가 필수

## 완료 조건
- 각 작업별 관련 테스트 통과
- `pnpm lint` 에러 없음

## 보고
- 결과를 `.claude/tasks/hana-fix-and-backlog-result.md`에 작성
- 완료 후 YURI에게 리뷰 요청 + SENA에게 보고
