# HANA 보안 지시서: DNS Rebinding 방어

## 목표
Gateway의 DNS rebinding 취약점 2가지를 수정합니다.

## 배경
MIRU 리서치 결과: Origin 미검증 + 0.0.0.0 fallback으로 취약.
상세: `.claude/tasks/miru-dns-rebinding-research.md` 참조

## 구현 항목 (우선순위순)

### 1. Origin 헤더 검증 (WebSocket upgrade)
- 위치: `src/gateway/server-http.ts:310-314` (ws upgrade 핸들러)
- Origin이 allowedHosts에 포함되는지 검증
- allowedHosts 기본값: `["localhost", "127.0.0.1", "::1"]`
- 불일치 시 WebSocket 연결 거부 (HTTP 403)
- Origin 없는 요청 (비브라우저): 허용 (CLI, curl 등)

### 2. 0.0.0.0 fallback 제거
- 위치: `src/gateway/net.ts:101,108,112,117,121,126,129`
- loopback 바인드 실패 시: 에러 출력 + 종료 (0.0.0.0 fallback 금지)
- `--bind all` 명시적 플래그가 있을 때만 0.0.0.0 허용

## 참고 파일
| 파일 | 역할 |
|------|------|
| `src/gateway/auth.ts:87-104` | 기존 Host 검증 로직 |
| `src/gateway/server/ws-connection.ts:73` | Origin 읽기 (현재 미검증) |
| `src/gateway/server-http.ts:304-316` | WebSocket upgrade 핸들러 |
| `src/gateway/net.ts:80-130` | 바인드 모드 |

## 테스트
- `src/gateway/auth.test.ts`에 추가:
  - Origin mismatch 시 연결 거부
  - Origin 없는 요청 허용
  - 0.0.0.0 fallback 금지 확인

## 제약
- `*.ts.net` (Tailscale) 호스트는 계속 허용
- 기존 `--bind loopback` 동작은 변경 없음
- `--bind all` 플래그 추가 시 기존 사용자 호환성 고려
