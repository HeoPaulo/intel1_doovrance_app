# 두브란스 병원 안내 시스템

두산 로보틱스 부트캠프 — 간호사 보조 로봇 프로젝트의 병원 내 키오스크 & 직원 대시보드 웹 앱입니다.

## 화면 구성

| 페이지 | 경로 | 설명 |
|--------|------|------|
| 키오스크 | `kiosk.html` | 환자용 AI 챗봇 + 4개국어 지원 |
| 직원 대시보드 | `staff.html` | 호출 알림, 환자 채팅, 건의함 실시간 수신 |
| QR 약품 관리 | `index.html` | 약품 QR 등록 및 스캔 |

## 주요 기능

- **AI 안내 챗봇** — Ollama (gemma3:4b) 기반 병원 정보 Q&A
- **다국어 지원** — 🇰🇷 한국어 / 🇺🇸 English / 🇨🇳 中文 / 🇯🇵 日本語
- **음성 입력(STT)** — Web Speech API, 언어별 자동 전환
- **음성 출력(TTS)** — SpeechSynthesis, 언어별 음성 선택
- **실시간 통신** — BroadcastChannel (로봇 호출 / 간호사 호출 / 직원 채팅 / 건의함)
- **PWA** — 오프라인 캐시, 홈 화면 설치 지원

## 로컬 실행

```bash
# Ollama 실행 (AI 챗봇용)
ollama serve
ollama run gemma3:4b

# 웹 서버 실행
cd medqr
python3 -m http.server 3000

# 브라우저에서 열기
# http://localhost:3000/kiosk.html   ← 환자용 키오스크
# http://localhost:3000/staff.html   ← 직원 대시보드
```

## 기술 스택

- **Frontend** — Vanilla HTML/CSS/JS (프레임워크 없음)
- **AI** — Ollama API (`http://localhost:11434/api/chat`, model: `gemma3:4b`)
- **실시간** — BroadcastChannel API + localStorage storage event
- **음성** — Web Speech API (SpeechRecognition + SpeechSynthesis)
- **PWA** — Service Worker + Web App Manifest

## 프로젝트 구조

```
medqr/
├── kiosk.html          # 환자용 키오스크 (메인)
├── staff.html          # 직원 대시보드
├── index.html          # QR 약품 관리
├── sw.js               # Service Worker
├── manifest.json       # PWA 매니페스트
├── doovrance_logo.png  # 두브란스 로고
└── icons/              # PWA 아이콘
```

## 개발 팀

두산 로보틱스 부트캠프 — 간호사 보조 로봇 팀  
병원명: 두브란스 (Doovrance)
