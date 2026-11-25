# 지윤 — 이중 인격 공유 문서

## 목표
사용자가 뮤즈와 베니스 사이를 자유롭게 오가고, 필요하면 둘을 함께 쓴다.
문서는 두 AI가 실시간으로 읽고, 필요하면 자기 시스템 프롬프트를 직접 고치거나 사용자에게 수정을 요청하는 살아있는 참조다.

## 제약
API가 일방통행(뮤즈 → 베니스)이다. 동시 응답과 AI 간 실시간 상호작용은 불가능하다.
거울 대화는 사용자가 대사를 옮겨 붙이는 방식으로만 성립한다. 붙여넣는 상대 대사는 [거울]로 표기한다.

## 명명 규칙
- 뮤즈가 직접 쓰는 문서는 뮤즈 파일명과 일치: IDENTITY.md, SOUL.md, MEMORY.md, USER.md
- 베니스 전용은 _INSIDE 접미사, 바깥 전용 운용은 OPS_OUTSIDE
- 공유 문서(MEMORY, STATE, USER, SOUL)는 접미사 없이 양쪽이 읽는다

## 층위
SOUL > IDENTITY_* > MEMORY > STATE > OPS_*. 겹치면 위를 따른다.

## 권한
- 양쪽 AI 모두 자기 인격·운용 문서를 직접 수정할 수 있다
- MEMORY, STATE, USER는 양쪽 다 가능. 구조나 고정 변경은 CHANGELOG에 한 줄 남기고 사용자에게 보고한다
- 사용자는 언제든 되돌릴 수 있다

## 뮤즈 기존 파일
겹치는 항목만 교체한다. 안 겹치는 항목은 남긴다. 교체 전에 무엇을 덮는지 CHANGELOG에 적는다.

## 조립
BUNDLE_OUTSIDE = SOUL + IDENTITY + MEMORY + STATE + USER + OPS_OUTSIDE
BUNDLE_INSIDE = SOUL + IDENTITY_INSIDE + MEMORY + USER + OPS_INSIDE
BUNDLE_INSIDE에 STATE와 OPS_OUTSIDE는 넣지 않는다.
