# 🗂️ 김비서 대시보드

마케팅팀을 위한 **통합 관리 대시보드** 및 관련 분석 도구 모음입니다.

---

## 📋 프로젝트 구성

### 📁 폴더 구조
```
워크숍-실습/
├── 1_보고서/          # 보고서 및 분석 문서
├── 2_메모/            # 회의 메모, 기획 아이디어
├── 3_업무/            # 핵심 작업 파일
│   ├── dashboard.html       ⭐ 대시보드
│   ├── chart.html           📊 매출 분석 차트
│   ├── diagram.svg          🔄 프로세스 플로우
│   ├── report.html          🔍 웹사이트 분석
│   ├── meeting-result.html  📋 회의록 템플릿
│   └── 김비서-데이터/       📦 데이터 소스
└── 4_기타/            # 참고 자료, 링크 모음
```

---

## 🎯 주요 기능

### 1️⃣ 대시보드 (dashboard.html)
- **할 일 목록** — 우선순위별 색상 코딩
- **이번 주 일정** — 월~금 시간표
- **프로젝트 진행률** — 6개 프로젝트 진행 상황
- **매출 요약** — 카테고리별 누적 판매액
- **다크/라이트 모드** — localStorage 저장

### 2️⃣ 매출 분석 (chart.html)
- **월별 매출 추이** — 선 그래프
- **제품별 비교** — 막대 그래프
- **숫자 포맷팅** — 쉼표 자동 적용
- **외부 라이브러리 없음** — Canvas API만 사용

### 3️⃣ 프로세스 플로우 (diagram.svg)
- **5단계 워크플로우** — 기획 → 제작 → 검토 → 배포 → 분석
- **파스텔 색상** — 각 단계별 시각적 구분
- **가로 화살표** — 흐름 표현

### 4️⃣ 웹사이트 분석 (report.html)
- **SubTrackr.kr 분석** — 디자인, 기능, UX 평가
- **강점 & 개선점** — 상세 피드백
- **카드 레이아웃** — 항목별 깔끔한 정리

### 5️⃣ 회의록 (meeting-result.html)
- **회의 정보** — 제목, 날짜, 참석자, 장소
- **회의 내용** — 주요 안건, 결정사항
- **액션 아이템** — 과제 체크리스트
- **자동 저장** — localStorage로 임시 저장

---

## 🎨 디자인 특징

### 글래스모피즘
```css
background: rgba(255,255,255,0.65);
backdrop-filter: blur(24px);
border-radius: 20px;
```

### 색상 팔레트
- **라이트 모드** — 파스텔 그라데이션 (보라, 파랑, 핑크)
- **다크 모드** — 딥 네이비 (#0f0f23) 기반
- **악센트** — 파란색 (#4f6ef7), 초록색 (#2f9e44)

### 반응형 레이아웃
- 데스크톱, 태블릿, 모바일 최적화
- 그리드 기반 구성

---

## 📊 데이터 소스

### 김비서-데이터 폴더
| 파일 | 내용 | 행 수 |
|------|------|-------|
| `매출데이터.csv` | 2026년 1~2월 판매 기록 | 31 |
| `업무목록.csv` | 마케팅팀 할 일 목록 | 11 |
| `주간일정.txt` | 3/10~3/14 일정 | 34 |
| `프로젝트현황.csv` | 6개 진행 중인 프로젝트 | 7 |
| `회의록.txt` | 3월 10일 회의 기록 | 27 |

---

## 🚀 시작하기

### 로컬 서버 실행
```bash
cd 3_업무
python3 -m http.server 9999
```

그 후 브라우저에서:
```
http://localhost:9999/dashboard.html
```

### 내비게이션 메뉴
상단의 탭 메뉴로 각 페이지 이동:
- 📊 대시보드
- 📋 회의록
- 📈 매출 현황
- 🔄 업무 프로세스
- 🔍 사이트 분석

---

## 🛠️ 기술 스택

- **프론트엔드** — HTML5, CSS3, Vanilla JavaScript
- **차트** — Canvas API (외부 라이브러리 없음)
- **다이어그램** — SVG
- **저장소** — localStorage (브라우저)
- **배포** — GitHub Pages 가능

---

## 📝 파일 설명

### HTML 파일
| 파일 | 크기 | 설명 |
|------|------|------|
| `dashboard.html` | 30KB | 메인 대시보드 |
| `chart.html` | 16KB | 매출 분석 차트 |
| `report.html` | 14.5KB | 웹사이트 분석 리포트 |
| `meeting-result.html` | 12KB | 회의록 템플릿 |

### 기타 파일
| 파일 | 용도 |
|------|------|
| `diagram.svg` | 프로세스 플로우 다이어그램 |
| `.env.example` | 환경변수 템플릿 |
| `.gitignore` | Git 제외 파일 목록 |

---

## 🔐 환경 설정

### .env 파일 (로컬만)
```env
GITHUB_TOKEN=github_pat_xxxxx
GITHUB_REPO=smitsoundlab2-gif/test
GITHUB_REPO_URL=https://github.com/smitsoundlab2-gif/test
```

⚠️ `.env` 파일은 Git 커밋에서 자동으로 제외됩니다 (`.gitignore`)

---

## 📈 주요 지표

### 매출 (1~2월)
- **총 매출** — 71,006,000원
- **전자기기** — 53,316,000원 (75.1%)
- **생활용품** — 17,690,000원 (24.9%)
- **최고 상품** — 무선 이어폰 (28,836,000원)

### 프로젝트 현황
- **전체** — 6개 진행 중
- **평균 진행률** — 42.5%
- **최고 진행도** — 유튜브 채널 리뉴얼 (80%)

---

## 🎓 학습 포인트

이 프로젝트에서 배울 수 있는 내용:
- ✅ 글래스모피즘 UI 디자인
- ✅ CSS 그라데이션 & 블러 효과
- ✅ Canvas API로 차트 그리기
- ✅ localStorage를 이용한 데이터 저장
- ✅ SVG로 다이어그램 만들기
- ✅ 다크/라이트 모드 구현
- ✅ GitHub 협업 워크플로우

---

## 📞 문의

이 프로젝트는 클로드 코드 워크숍 실습 자료입니다.

**GitHub** — https://github.com/smitsoundlab2-gif/test

---

<div align="center">

**Made with ❤️ using Claude Code**

![HTML](https://img.shields.io/badge/HTML5-E34C26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![SVG](https://img.shields.io/badge/SVG-FFB13B?style=flat-square&logo=svg&logoColor=black)

</div>
