# 알뜰한 K씨

생활 절약 콘텐츠 브랜드용 정적 웹사이트 MVP입니다.

## 로컬 실행

```bash
python3 -m http.server 4190
```

확인 URL:

- `http://localhost:4190/index.html`
- `http://localhost:4190/guides/oracle-wireguard-vpn.html`

## 배포 설정

Cloudflare Pages 기준:

- Framework preset: `None`
- Build command: 비워둠
- Build output directory: `/`
- Root directory: `/`

## 현재 주의사항

첫 가이드의 Oracle Cloud Free Tier + WireGuard 구축은 아직 실제 검증 전 초안입니다. 공개 상태에서도 “검증 전” 문구를 유지해야 합니다.
