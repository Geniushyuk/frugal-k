# NotebookLM Source — 알뜰한 K씨 영상 001

이 폴더는 NotebookLM에 GitHub 레포 소스로 연결하기 위한 영상 제작 참고 자료입니다.
중앙 지식 저장소가 아니라 `알뜰한 K씨` 영상 제작용 참고 저장소로만 사용합니다.

## NotebookLM 연결 대상

GitHub 레포:

```text
https://github.com/Geniushyuk/frugal-k
```

우선 참고 경로:

```text
notebooklm-sources/video-001-automatic-payment-ledger/
```

## 핵심 문서

- `hermes-image-handoff-command.md` — Hermes/GPT 이미지 제작 및 검수 기준
- `grok-all-image-prompts.md` — GPT 웹 이미지 생성용 36컷 전체 프롬프트
- `grok-video-handoff-command.md` — Grok 영상 제작 전달 명령서
- `cut-data.json` — 36컷 컷보드 데이터: 타임코드, 샷 사이즈, 카메라, 연결, 이미지/영상 프롬프트
- `video-001-elevenlabs-narration.txt` — ElevenLabs용 내레이션 대본

## 제작 기준

- 총 36컷
- 컷당 약 5초
- 전체 영상 약 3분
- 배경은 순백색 흰색
- 하단 자막 공간을 일부러 비우지 않음
- K씨 캐릭터 유지: 둥근 얼굴, 짧은 검은 머리, 검은 사각 안경, 하얀 셔츠, 초록/카키 가디건, 검은 바지
- 실제 브랜드 로고, 카드사 로고, 앱 로고, 서비스 로고 금지
- 영상 대본과 컷보드 일치
- 이미지 생성은 GPT 웹에서 진행
- 이미지는 NotebookLM이 아니라 별도 이미지 저장/관리 흐름에서 관리
- Grok은 검수 완료된 36컷 이미지를 바탕으로 영상 제작만 담당

## NotebookLM 사용 방식

1. NotebookLM에서 GitHub 소스로 `https://github.com/Geniushyuk/frugal-k`를 연결한다.
2. 이 폴더의 문서를 영상 001 참고 자료로 사용한다.
3. 질문은 컷보드, 내레이션, 이미지 프롬프트, Grok 영상화 기준 확인 용도로만 사용한다.
4. 브랜드 전체 지식 저장소나 영구 중앙 저장소로 취급하지 않는다.

## 빠른 질문 예시

- 영상 001의 36컷 흐름을 요약해줘.
- CUT 01~06의 이미지 생성 기준을 표로 정리해줘.
- Grok에 영상 제작을 맡길 때 지켜야 할 금지사항을 정리해줘.
- 내레이션과 컷보드가 어긋나는 부분이 있는지 확인해줘.
- 실제 로고가 들어가면 안 되는 컷을 모두 찾아줘.
