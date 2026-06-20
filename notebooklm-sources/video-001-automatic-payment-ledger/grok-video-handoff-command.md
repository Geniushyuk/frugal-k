# Grok 전달용 — 알뜰한 K씨 영상 제작 명령서

## 역할 변경
이미지 생성은 Grok이 아니라 GPT 웹에서 진행한다.
이미지는 Notelm에 저장/관리한 뒤, 최종 이미지 파일을 로컬 `frames/` 폴더에 내려받는다.
Grok은 이미지 생성이 아니라 36컷 이미지를 기반으로 영상 제작만 맡는다.

## 작업 위치
```bash
cd "/Users/happydonggle/Documents/알뜰한 K씨"
```

## 입력 이미지
```text
drafts-private/codex-image-pipeline-001/frames/frame-01.png
...
drafts-private/codex-image-pipeline-001/frames/frame-36.png
```

## 영상 제작 기준
1. 총 36컷이다.
2. 각 컷은 약 5초 영상으로 만든다.
3. 컷 순서는 `frame-01.png`부터 `frame-36.png`까지 유지한다.
4. 영상은 영화 콘티처럼 자연스럽게 이어진다.
5. K씨 캐릭터, 순백색 배경, 장부/계산기/구독 점검 분위기를 유지한다.
6. 실제 브랜드 로고, 카드사 로고, 앱 로고, 서비스 로고는 추가하지 않는다.
7. 이미지 안의 금액과 텍스트는 변경하지 않는다.
8. 과한 카메라 무빙보다 컷보드의 샷 사이즈와 연결 오브젝트를 살리는 움직임을 우선한다.
9. 한 컷 안에 여러 장면을 새로 분할하지 않는다.
10. 하단 자막 공간을 억지로 만들지 않는다.

## Grok에 전달할 기본 명령
```text
첨부한 36장 이미지를 순서대로 사용해서 알뜰한 K씨 영상 컷을 만들어줘.
각 이미지는 약 5초 길이의 키프레임이고, frame-01부터 frame-36까지 순서를 절대 바꾸지 마.
이미지의 순백색 배경, 손그림 질감, K씨 캐릭터, 장부/계산기/구독 점검 분위기를 유지해줘.
실제 브랜드 로고, 카드사 로고, 앱 로고, 서비스 로고를 새로 만들거나 추가하지 마.
금액과 기존 텍스트는 바꾸지 말고, 컷보드의 샷 사이즈와 다음 컷 연결 오브젝트가 자연스럽게 이어지게 움직여줘.
과한 효과보다 생활비 장부를 차분하게 뜯어보는 영화 콘티 느낌으로 만들어줘.
```

## 생성 전 확인
이미지 누락 확인:
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

## Codex/Hermes 역할
1. GPT 웹에서 만든 이미지를 Notelm에서 내려받아 `frames/`에 저장한다.
2. `check_frames.py`로 `36/36` 여부를 확인한다.
3. `review.html`에서 컷 연결, 캐릭터 일관성, 흰색 배경, 로고/숫자 오류를 검수한다.
4. 통과한 36컷만 Grok 영상 제작에 전달한다.
5. 튀는 컷이 있으면 GPT 웹에서 해당 CUT만 다시 생성한다.
