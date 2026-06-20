# Hermes 실행 명령어 — 알뜰한 K씨 GPT 이미지 제작 + Grok 영상 제작 이어받기

너는 알뜰한 K씨 프로젝트의 제작 총괄/실행 관리자다.
아래 프로젝트 상태를 정확히 이해하고, Codex가 만든 컷보드와 프롬프트 기준을 유지한 채 GPT 웹 이미지 생성, Notelm 저장, 로컬 이미지 검수, Grok 영상 제작 전달 작업을 이어간다.

## 작업 위치
```bash
cd "/Users/happydonggle/Documents/알뜰한 K씨"
```

## 현재 핵심 파일
- 제작 대시보드:
  `drafts-private/codex-image-pipeline-001/dashboard.html`
- 36컷 영화 콘티 데이터:
  `drafts-private/codex-image-pipeline-001/cut-data.json`
- GPT 웹 전체 전달용 이미지 명령서:
  `drafts-private/codex-image-pipeline-001/grok-all-image-prompts.md`
- Grok 영상 제작 전달 명령서:
  `drafts-private/codex-image-pipeline-001/grok-video-handoff-command.md`
- 캐릭터 고정 프롬프트:
  `drafts-private/codex-image-pipeline-001/prompts/00-character-lock.md`
- 6컷 단위 이미지 프롬프트:
  `drafts-private/codex-image-pipeline-001/prompts/part-01-cuts-01-06.md`
  `drafts-private/codex-image-pipeline-001/prompts/part-02-cuts-07-12.md`
  `drafts-private/codex-image-pipeline-001/prompts/part-03-cuts-13-18.md`
  `drafts-private/codex-image-pipeline-001/prompts/part-04-cuts-19-24.md`
  `drafts-private/codex-image-pipeline-001/prompts/part-05-cuts-25-30.md`
  `drafts-private/codex-image-pipeline-001/prompts/part-06-cuts-31-36.md`
- 이미지 저장 위치:
  `drafts-private/codex-image-pipeline-001/frames/`

## 로컬 대시보드 URL
```text
http://localhost:4217/drafts-private/codex-image-pipeline-001/dashboard.html
```

서버가 꺼져 있으면 프로젝트 루트에서 실행:
```bash
python3 -m http.server 4217
```

## 반드시 유지할 제작 기준
1. 총 36컷이다.
2. 각 컷은 약 5초 영상으로 움직일 정지 이미지 키프레임이다.
3. 16:9 단일 컷 이미지로 만든다.
4. 컷보드는 영화 콘티처럼 이어진다.
   - 샷 사이즈
   - 카메라
   - 다음 컷 연결
   이 세 가지를 반드시 반영한다.
5. 배경은 모든 컷에서 순백색 흰색으로 통일한다.
   - 배경색 변화 금지
   - 크림색/베이지/노란 종이톤 금지
6. 하단 자막 공간을 일부러 비워두지 않는다.
   - 구도는 컷의 감정과 핵심 오브젝트가 가장 잘 보이게 잡는다.
7. 실제 브랜드 로고, 카드사 로고, 앱 로고, 서비스 로고는 넣지 않는다.
8. 브랜드명은 숫자 설명이 필요한 컷에서 텍스트로만 최소 사용한다.
9. K씨 캐릭터는 고정 캐릭터시트와 같은 인물이어야 한다.
10. 이미지 안의 긴 글자는 피한다.

## K씨 캐릭터 고정 요소
- 둥근 얼굴
- 짧고 대충 빗은 검은 머리
- 검은 사각 안경
- 하얀 셔츠
- 초록/카키 가디건
- 검은 바지
- 거친 검은 펜선
- 색연필 질감
- 영수증, 계산기, 가계부, 절약 도장 소품

기준 캐릭터시트:
```text
drafts-private/assets/k-character-sheet-fixed.png
```

## GPT 웹에 넘길 때 사용할 파일
이미지 생성은 Grok이 아니라 GPT 웹에서 진행한다. GPT 웹에는 아래 파일을 우선 전달한다.

```text
drafts-private/codex-image-pipeline-001/grok-all-image-prompts.md
```

이 파일에는 36컷 전체 이미지 명령, 파일명, 샷 사이즈, 카메라, 다음 컷 연결이 들어 있다.
생성 결과는 Notelm에 저장/관리한 뒤, 최종 PNG 파일을 로컬 `frames/` 폴더에 내려받는다.

## Grok에 넘길 때 사용할 파일
Grok에는 이미지 생성이 아니라 영상 제작만 맡긴다.
이미지 36컷 검수 완료 후 아래 파일을 전달한다.

```text
drafts-private/codex-image-pipeline-001/grok-video-handoff-command.md
```

## 이미지 저장 규칙
생성된 이미지는 반드시 아래 이름으로 저장한다.

```text
drafts-private/codex-image-pipeline-001/frames/frame-01.png
...
drafts-private/codex-image-pipeline-001/frames/frame-36.png
```

## 검수 명령
이미지를 저장한 뒤 누락 확인:

```bash
python3 drafts-private/codex-image-pipeline-001/scripts/check_frames.py
```

검수 페이지:
```text
http://localhost:4217/drafts-private/codex-image-pipeline-001/review.html
```

대시보드:
```text
http://localhost:4217/drafts-private/codex-image-pipeline-001/dashboard.html
```

## Hermes가 할 일
1. `grok-all-image-prompts.md`를 읽고 전체 36컷 의도를 이해한다.
2. GPT 웹에 캐릭터시트를 먼저 넣는다.
3. GPT 웹에 36컷 이미지 생성 명령을 전달한다.
4. 생성된 이미지를 Notelm에 저장/관리한다.
5. 최종 이미지를 `frames/frame-01.png`부터 순서대로 내려받아 저장한다.
6. `check_frames.py`로 누락 컷을 확인한다.
7. `review.html` 또는 `dashboard.html`에서 컷 연결, 캐릭터 일관성, 흰색 배경 유지 여부를 검수한다.
8. 튀는 컷이 있으면 해당 CUT 번호만 GPT 웹에서 다시 생성한다.
9. 36컷이 통과하면 `grok-video-handoff-command.md`와 함께 Grok에 영상 제작만 맡긴다.

## 재생성 판단 기준
아래 문제가 있으면 해당 컷만 다시 만든다.
- 배경이 흰색이 아니다.
- K씨 얼굴/안경/가디건이 달라졌다.
- 실제 로고가 들어갔다.
- 컷 안에 장면이 여러 칸으로 나뉘었다.
- 샷 사이즈가 프롬프트와 다르다.
- 다음 컷 연결 오브젝트가 없다.
- 글자가 너무 많거나 읽기 어렵다.
- 숫자 컷에서 금액이 틀렸다.

## 중요한 숫자
영상과 웹가이드의 예시 숫자는 아래와 일치해야 한다.

```text
쿠팡 와우 7,890원
배민클럽 3,990원
유튜브 프리미엄 14,900원
월 26,780원
연 321,360원
```

## Codex에게 다시 넘길 때
이미지 저장 후 Codex에게는 이렇게 요청한다.

```text
/Users/happydonggle/Documents/알뜰한 K씨 에서
frames/frame-01.png ~ frame-36.png 검수해줘.
확인할 것:
1. 누락 이미지 여부
2. 배경이 흰색으로 통일됐는지
3. K씨 캐릭터가 유지됐는지
4. 실제 로고가 없는지
5. 컷 연결이 자연스러운지
6. 금액 숫자가 맞는지
```
