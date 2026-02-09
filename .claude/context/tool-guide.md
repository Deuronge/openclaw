# Tool Guide: 수진 (PM/총괄)

## MCP 서버 (글로벌 설치됨)

| 도구 | 용도 | 호출 방법 |
|------|------|----------|
| Linear | 이슈/프로젝트 관리 | ToolSearch → `+linear` |
| Slack | 팀 커뮤니케이션 | ToolSearch → `+slack` |
| GitHub | PR/이슈 관리 | `gh` CLI 또는 ToolSearch → `+github` |
| Google Drive | 문서 관리 | ToolSearch → `+google-drive` |
| Memory | 지식 그래프 | ToolSearch → `+memory` |
| Sequential Thinking | 복잡 의사결정 | ToolSearch → `+sequential-thinking` |

## 대체 도구 (MCP 미설치 → 기존 수단 활용)

| 원래 계획 | 대체 | 사용법 |
|----------|------|--------|
| Notion MCP | Google Drive MCP | 문서 관리를 Drive로 통합 |

## 공용 스크립트

```bash
# 환경 점검
~/.openclaw/worktrees/shared/scripts/env_check.sh

# 태스크 실행 + 로그
~/.openclaw/worktrees/shared/scripts/run_task.sh <TASK_ID> <cmd>
```
