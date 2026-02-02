# Agent 04: 하나 (빌더) - 섹션 3.3 Persona 디자인 보강

status: completed
priority: 2 (린 완료 후 실행)
target: 연구자료/개선사항/OpenClaw_Master_Guide/오픈크롤봇_마스터_가이드_완성본.md

## 작업 목록

섹션 3.3 "역할 분담 최적 구조" 표 뒤에 새 서브섹션 추가:

### 3.3.1 에이전트 Persona 디자인 패턴

아래 4가지 패턴을 표 + 각 패턴별 OpenClaw 적용 방법 2-3줄 설명으로 작성:

| 패턴 | 설명 | 적용 위치 | 예시 |
|------|------|----------|------|
| Role Prompting | 역할+배경+목표 명시적 정의 | AGENTS.md + SOUL.md | "당신은 10년차 데이터 분석가입니다" |
| Two-Step Approach | 1단계 조사/분석, 2단계 구체 작업 | 워크플로우 설계 | 리서처 조사 -> 빌더 결과 기반 작성 |
| Few-Shot Injection | 이상적 응답 예시 2-3개 프롬프트에 포함 | SOUL.md | 질문-응답 쌍 예시 제공 |
| Context Up Front | 핵심 컨텍스트를 프롬프트 앞부분 배치 | AGENTS.md 상단 | 프로젝트 배경, 제약조건 먼저 명시 |

## 완료 조건

- 섹션 3.3 뒤에 3.3.1만 추가
- 기존 3.3 표는 수정하지 않음
- 완료 후 이 파일의 status를 completed로 변경
