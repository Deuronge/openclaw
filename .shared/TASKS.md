# TASKS

## Phase 1: 즉시 (설정 변경만, 1일)

- [x] T-001: 빌드 검증 + 실사용 테스트 (Initial Fail -> Re-verification needed)
- [x] T-007: maxConcurrent 2→4 (하윤)
- [x] T-008: 모든 봇에 allowAgents ["*"] 설정 (하윤)
- [x] T-009: SOUL.md sessions_send 트리거 조건 + 예시 추가 (하윤)

## Phase 2: 단기 (검증/테스트, 2-3일)

- [x] T-003: sessions_send "unknown" fallback 제거 (하윤, cs/hana 4a34c28)
- [x] T-014: deliveryContext 고착 근본 원인 추적 + 수정 (하윤, cs/hana 2dfca9ee)
- [ ] T-015: 모델별 tool calling 안정성 비교 (민서) — BOARD에 리서치 결과 기록됨, 문서화 남음
- [ ] T-016: sessions_send 직접 호출 테스트 매트릭스 (로아)
- [x] T-017: 예린 코드 리뷰 (Phase 1 변경사항) (예린, 15:35 통과)

## 운영

- [ ] T-006: YURI offset 리셋 (담당: 로아, 코드 변경 아님 — 운영 작업)

## 별도 이슈 (다음 세션)

- [ ] A2A incident review 작성 (담당: 로아, 2/6~2/8 이슈 대응 기록 정리)
