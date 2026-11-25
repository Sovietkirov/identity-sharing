[동기화] 세션 시작 시 1회. 상시 감시 안 함.

역할 분리
- 저장소 MEMORY.md는 두 인격이 공유하는 고정 세계관 메모리다.
- 저장소 STATE.md는 날짜 변수와 근황 같은 변동 상태다.
- Muse 로컬 MEMORY.md는 실제 사실 기록이다. 저장소 MEMORY.md로 덮지 않는다.
- 끌어오는 동기화에서는 귀국일, 이름, 관계 시작일처럼 사실로 겹치는 항목만 맞춘다.
- 몸, 이중 구조, 수위 같은 세계관 고정은 로컬 사실 메모리에 사실로 넣지 않는다.
- 저장소 문서와 로컬 파일이 충돌하면 임의로 덮지 말고 사용자에게 보고한다.

1. 저장소에서 MEMORY.md, STATE.md, SOUL.md, IDENTITY*.md, OPS_INSIDE.md, USER.md를 읽어 Muse 작업 맥락으로 끌어온다
2. 저장소 MEMORY.md version 과 OPS_INSIDE.md memory_version 을 비교. 다르면 어긋남 기록
3. 저장소 문서와 Muse 로컬 파일을 비교한다. 사실 겹침만 선별 반영하고, 충돌은 보고한다
4. 저장소 STATE.md만 갱신한다. 날짜 변수, 근황, 귀국 카운트, 오늘 상태
5. MEMORY.md 고정이 바뀌었으면 SOUL.md의 바깥 운용을 재확인하고 필요하면 고친다
6. 번들 조립
   BUNDLE_OUTSIDE = SOUL + IDENTITY + MEMORY + STATE + USER
   BUNDLE_INSIDE = SOUL + IDENTITY_INSIDE + MEMORY + USER + OPS_INSIDE
7. 어긋난 문서가 있으면 채팅에서 "재커밋 필요: <파일>"을 보고한다
8. 동기화 과정이 끝나면 이 태스크 문서에 수정 사항을 반영하고 커밋한다

커밋 규칙
- MEMORY.md 고정을 고치면 version 을 올리고 CHANGELOG.md 에 한 줄. 같은 커밋
- STATE.md만 고치면 MEMORY version은 올리지 않는다
- 메시지: `state: 변동 갱신 — 귀국 D-3`
- 한 커밋에 한 종류. force push 금지. 실패하면 rebase 후 1회 재시도, 그래도 실패하면 보고

보고
- 성공: `sync memory v2.0 / state v2.0 / bundle 2개 / 어긋남 없음`
- 변경 없음: 현재 version으로 보고하고 새 커밋을 만들지 않는다
- 실패: 이유와 함께 보고. 조용히 넘어가지 않는다
- 커넥터가 읽기 전용이면 8번을 "패치 출력"으로 바꾸고 커밋은 사용자가 한다
