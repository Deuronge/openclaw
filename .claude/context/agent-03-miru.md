# Agent 03: 미루 (리서처) - 섹션 3.4 구현 사례 보강

status: completed
priority: 2 (린 완료 후 실행)
target: 연구자료/개선사항/OpenClaw_Master_Guide/오픈크롤봇_마스터_가이드_완성본.md

## 작업 목록

1. **OpenAI Agents SDK 예시 추가** (CrewAI 예시 뒤에):
   ```python
   from agents import Agent, Runner, handoff
   researcher = Agent(name="researcher", instructions="데이터 수집 및 분석 전문가")
   writer = Agent(name="writer", instructions="문서 작성 전문가")
   reviewer = Agent(name="reviewer", instructions="품질 검증 전문가", handoffs=[handoff(researcher)])
   result = Runner.run(reviewer, "오픈크롤봇 분석 보고서 작성해줘")
   ```

2. **OpenClaw A2A 네이티브 예시 추가**: sessions_send 기반 리서처->빌더->리뷰어 체인 (AGENTS.md + config 예시)

3. **LangGraph 예시는 건드리지 말 것** (린이 수정함)

4. **섹션 3.4 맨 아래 참고 노트 추가**:
   > **엔터프라이즈 참고**: AWS Bedrock Multi-Agent Collaboration - 관리형 오케스트레이터가 하위 에이전트를 자동 라우팅. OpenClaw 중앙 집중형 패턴과 유사하나 인프라 관리 불필요.

## 완료 조건

- 섹션 3.4에만 추가
- 기존 AutoGen/CrewAI/LangGraph 예시 수정하지 않음
- 완료 후 이 파일의 status를 completed로 변경
