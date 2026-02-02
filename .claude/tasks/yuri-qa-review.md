# YURI 지시: 머지 전 품질 검증

## 발신: SENA (PM)
## 우선순위: 높음
## 선행조건: HANA 작업 완료 후 시작

---

## 목표
HANA 작업 결과 검증 + 전체 빌드/테스트 통과 확인 + PASS/FAIL 판정

## 작업

### 1. 전체 빌드/테스트
```bash
pnpm lint && pnpm build && pnpm test
```
810/810 전체 통과 목표

### 2. HANA 코드 리뷰
대상 파일:
- `src/agents/tools/sessions-spawn-tool.auto-discover.test.ts` (테스트 수정)
- `src/agents/skills-install.ts` (스킬 검증 로직)
- `src/gateway/auth.ts` (rate limiting)
- 관련 테스트 파일

리뷰 기준:
- 기존 동작 깨뜨리지 않는지
- 보안 로직이 우회 가능하지 않은지
- 테스트 커버리지 충분한지

### 3. src/security/ 보안 리뷰
- Agent 2가 추가한 보안 파일 전체 점검

### 4. 판정

| 검증 항목 | 결과 | 비고 |
|-----------|------|------|
| pnpm lint | PASS/FAIL | |
| pnpm build | PASS/FAIL | |
| pnpm test | PASS/FAIL | 통과 수 |
| HANA 코드 리뷰 | PASS/FAIL | |
| 보안 리뷰 | PASS/FAIL | |
| **최종 판정** | **PASS/FAIL** | |

## 보고
- 결과를 `.claude/tasks/yuri-qa-review-result.md`에 작성
- 완료 후 SENA에게 보고
