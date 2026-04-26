# 커밋 메시지 규칙

## 형식
`<type>(<scope>): <description>`

## type 매핑
- feat: 새 문제 풀이 추가
- refactor: 기존 풀이 로직 개선 또는 양식 변경
- docs: 복잡도, 태그, README 등 메타데이터/문서 작업
- fix: 풀이의 오답/버그 수정
- chore: 폴더 구조, .gitignore 등 잡일
- perf: 성능 개선이 명확한 풀이 변경
- style: 들여쓰기, 공백 등 (정답성 영향 없음)

## scope
- Level0, Level1, Level2 (메인)
- weekly, notes (서브)

## 예시
- feat(Level1): add solution for 12918 (#문자열)
- docs(Level0): add complexity analysis to 61 solutions
- refactor: restructure folder by category