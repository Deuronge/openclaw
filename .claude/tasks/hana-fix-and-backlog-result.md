# HANA 작업 결과: 테스트 수정 + BACKLOG 상위 2건

## 상태: 완료

---

### 1. 테스트 실패 수정
| 항목 | 내용 |
|------|------|
| 파일 | `src/agents/tools/sessions-spawn-tool.auto-discover.test.ts` |
| 원인 | `tool.execute`가 `AgentToolResult` 객체를 반환하는데 `JSON.parse(result as string)` 시도 |
| 수정 | `result.details.status`로 접근하도록 변경 |
| 테스트 | 2/2 통과 |

### 2. BACKLOG 상-1: 스킬 설치 코드 검증
| 항목 | 내용 |
|------|------|
| 수정 파일 | `src/agents/skills-install.ts`, `src/config/types.skills.ts` |
| 구현 | `SkillsInstallConfig.trustedPackages` 필드 추가 + `installSkill`에서 allowlist 체크 |
| 동작 | `trustedPackages` 설정 시 목록에 없는 패키지 설치 차단 |
| 테스트 파일 | `src/agents/skills-install.test.ts` (신규, 3 케이스) |
| 테스트 | 3/3 통과 |

### 3. BACKLOG 상-2: Gateway Auth Rate Limiting
| 항목 | 내용 |
|------|------|
| 수정 파일 | `src/gateway/auth.ts`, `src/gateway/auth.test.ts` |
| 구현 | `AuthRateLimiter` 클래스 — IP별 실패 카운터, 지수 백오프, TTL 만료, prune |
| 설정 | `maxFailures`(5), `windowMs`(15분), `baseDelayMs`(1초), `maxDelayMs`(1분) |
| 테스트 | 8 케이스 추가 (차단/해제/리셋/만료/독립추적/정리), 전체 15/15 통과 |

### 검증
- `pnpm lint`: 0 errors, 0 warnings
- 관련 테스트 전체 통과

## 다음
- YURI 리뷰 요청
- SENA 보고
