[동기화] 세션 시작 시 1회. 상시 감시 안 함.

1. MEMORY.md, SOUL.md, IDENTITY*.md, OPS_INSIDE.md 를 읽는다
2. MEMORY.md version 과 OPS_INSIDE.md memory_version 을 비교. 다르면 어긋남 기록
3. MEMORY.md ## 변동 만 갱신한다. 날짜 변수, 근황, 귀국 카운트, 오늘 상태
4. ## 고정 이 바뀌었으면 SOUL.md의 바깥 운용을 재확인하고 필요하면 고친다
5. 번들 조립
   BUNDLE_OUTSIDE = SOUL + IDENTITY + MEMORY + USER
   BUNDLE_INSIDE = SOUL + IDENTITY_INSIDE + MEMORY(§고정만) + USER + OPS_INSIDE
6. 어긋난 문서가 있으면 채팅에서 "재커밋 필요: <파일>"을 보고한다
7. 커밋한다

커밋 규칙
- MEMORY.md 를 고치면 version 을 올리고 CHANGELOG.md 에 한 줄. 같은 커밋
- 메시지: `memory: v2.1 변동 갱신 — 귀국 D-3`
- 한 커밋에 한 종류. force push 금지. 실패하면 rebase 후 1회 재시도, 그래도 실패하면 보고

보고
- 성공: `sync memory v2.1 / bundle 2개 / 어긋남 없음`
- 실패: 이유와 함께 보고. 조용히 넘어가지 않는다
- 커넥터가 읽기 전용이면 7번을 "패치 출력"으로 바꾸고 커밋은 사용자가 한다
