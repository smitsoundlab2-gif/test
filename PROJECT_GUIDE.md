# 🗂️ 김비서 대시보드 프로젝트 작업 가이드

**작업 날짜**: 2026년 5월 6일  
**작업자**: 윤성경 (Claude Code)  
**프로젝트**: 마케팅팀 통합 관리 대시보드

---

## 📋 목차

1. [프로젝트 개요](#프로젝트-개요)
2. [폴더 구조](#폴더-구조)
3. [작업 내용 상세](#작업-내용-상세)
4. [파일별 설명](#파일별-설명)
5. [기술 스택](#기술-스택)
6. [배포 및 실행](#배포-및-실행)
7. [앞으로의 개선 사항](#앞으로의-개선-사항)

---

## 프로젝트 개요

### 목표
마케팅팀의 **일일 운영 관리**를 위한 통합 대시보드 및 분석 도구 제공

### 핵심 기능
- ✅ 실시간 대시보드 (할 일, 일정, 프로젝트, 매출)
- ✅ 데이터 시각화 (차트, 프로세스 플로우)
- ✅ 회의록 작성 및 관리
- ✅ 웹사이트 분석 및 피드백
- ✅ 다크/라이트 모드
- ✅ GitHub 통합 및 Vercel 배포

---

## 폴더 구조

```
워크숍-실습/
├── 1_보고서/                    # 6개 파일
│   ├── 보고서_초안.txt
│   ├── 보고서_수정.txt
│   ├── 보고서_최종.txt
│   ├── 보고서_최종_진짜최종.txt
│   ├── 영수증_정리.txt
│   └── temp.csv
│
├── 2_메모/                      # 4개 파일
│   ├── 기획_메모.txt
│   ├── 메모.txt
│   ├── 아이디어_메모_0301.txt
│   └── 피드백.txt
│
├── 3_업무/                      # 핵심 파일 ⭐
│   ├── index.html               # Vercel 리다이렉트
│   ├── dashboard.html           # 📊 메인 대시보드
│   ├── chart.html               # 📈 매출 분석 차트
│   ├── diagram.svg              # 🔄 프로세스 플로우
│   ├── report.html              # 🔍 웹사이트 분석
│   ├── meeting-result.html      # 📋 회의록 템플릿
│   └── 김비서-데이터/
│       ├── 매출데이터.csv
│       ├── 업무목록.csv
│       ├── 주간일정.txt
│       ├── 프로젝트현황.csv
│       └── 회의록.txt
│
├── 4_기타/                      # 3개 파일
│   ├── 나중에정리.txt
│   ├── 링크모음.txt
│   └── 무제.txt
│
├── .claude/
│   └── settings.local.json
│
├── .env                         # 🔐 환경변수 (로컬, Git 제외)
├── .env.example                 # 템플릿 (Git 포함)
├── .gitignore                   # Git 제외 파일
├── README.md                    # 프로젝트 소개
├── vercel.json                  # Vercel 배포 설정
└── PROJECT_GUIDE.md             # 이 파일
```

---

## 작업 내용 상세

### 1️⃣ 폴더 정리 (초기 작업)

**목표**: 파일 27개를 용도별로 분류

**진행 과정**:
```bash
# 1. 4개 하위 폴더 생성
mkdir 1_보고서 2_메모 3_업무 4_기타

# 2. 파일 이동
mv 보고서*.txt → 1_보고서/
mv 메모*.txt → 2_메모/
mv 할일.txt 회의실.txt → 3_업무/
mv 링크모음.txt 나중에정리.txt 무제.txt → 4_기타/

# 3. 원본 폴더 삭제
rm -rf 정리해줘/
```

**결과**:
- ✅ 27개 파일 정렬
- ✅ 용도별 분류 완료
- ✅ 폴더 구조 명확화

---

### 2️⃣ Dashboard.html 생성

**파일 크기**: 30,749 bytes (30KB)  
**라인 수**: ~600줄

**주요 기능**:

#### 1. 글래스모피즘 디자인
```css
background: rgba(255,255,255,0.65);
backdrop-filter: blur(24px);
border: 1px solid rgba(255,255,255,0.85);
border-radius: 20px;
```

#### 2. 다크/라이트 모드
- CSS 변수 활용 (`:root` 스타일)
- localStorage에 테마 저장
- 시스템 기본값 자동 감지

**테마 색상**:
```
라이트: #e8edf8 → #f0e8ff → #ffe8f5 (파스텔)
다크:   #0f0f23 → #1a0a2e → #0d1a2e (딥 네이비)
```

#### 3. 4가지 섹션

| 섹션 | 내용 | 데이터 출처 |
|------|------|-----------|
| 할 일 목록 | 9개 과제, 우선순위 색상 | 업무목록.csv |
| 이번 주 일정 | 월~금 13개 이벤트 | 주간일정.txt |
| 프로젝트 진행률 | 6개 프로젝트, 진행바 | 프로젝트현황.csv |
| 매출 요약 | 카테고리별 판매액 | 매출데이터.csv |

#### 4. 네비게이션 메뉴
```html
<nav class="nav-menu">
  <a href="dashboard.html" class="nav-item active">📊 대시보드</a>
  <a href="meeting-result.html" class="nav-item">📋 회의록</a>
  <a href="chart.html" class="nav-item">📈 매출 현황</a>
  <a href="diagram.svg" class="nav-item">🔄 업무 프로세스</a>
  <a href="report.html" class="nav-item">🔍 사이트 분석</a>
</nav>
```

현재 페이지는 파란색 그라데이션으로 강조됨

---

### 3️⃣ Chart.html 생성

**파일 크기**: 16,034 bytes (16KB)  
**기술**: Canvas API (외부 라이브러리 없음)

**2가지 차트**:

#### 1. 월별 매출 추이 (선 그래프)
```
1월: 46,499,000원 ━━━●━━━
2월: 24,507,000원 (부분) ━●
```

- 점 위에 값 표시
- 그리드 라인 포함
- Y축 범위 자동 계산

#### 2. 제품별 매출 비교 (막대 그래프)
```
무선 이어폰    ████████████ 28,836,000원
텀블러         ██████        11,525,000원
블루투스 스피커 ███████       9,600,000원
보조배터리     ████           9,030,000원
무선 충전기    ███            5,850,000원
에코백         ███            6,165,000원
```

- 매출 높은 순서로 정렬
- 제품별 누적 합계
- 숫자에 자동 쉼표 포맷팅

**CSV 데이터 처리**:
```javascript
// 인라인 데이터 (30행)
const csvData = [
  { date: '2026-01-05', product: '무선 이어폰', category: '전자기기', amount: 4005000 },
  ...
];

// 월별 집계
monthlyData['01'] = 46,499,000;
monthlyData['02'] = 24,507,000;

// 제품별 집계
productData['무선 이어폰'] = 28,836,000;
```

---

### 4️⃣ Diagram.svg 생성

**파일 크기**: 2,934 bytes  
**형식**: SVG (벡터)

**5단계 프로세스**:
```
기획 ──→ 제작 ──→ 검토 ──→ 배포 ──→ 분석
(핑크)  (주황)   (노랑)   (초록)   (파랑)
```

**디자인 특징**:
- 둥근 사각형 (rx="16")
- 파스텔 색상 5가지
- 화살표로 단계 연결
- 드롭 섀도우 효과
- 영문 레이블 포함

**SVG 구조**:
```xml
<svg viewBox="0 0 800 200">
  <rect x="30" y="50" width="120" height="100" rx="16" fill="#fdd7e4" />
  <text x="90" y="110">기획</text>
  <line x1="155" y1="100" x2="175" y2="100" />
</svg>
```

---

### 5️⃣ Report.html 생성

**파일 크기**: 14,501 bytes (14.5KB)

**분석 대상**: SubTrackr.kr (구독 관리 SaaS)

**9개 분석 카드**:

| 카드 | 내용 | 항목 수 |
|------|------|--------|
| 사이트 구조 | 6개 섹션 | 6개 |
| 디자인 & 색상 | 브랜드, 스타일 | 3개 |
| 주요 기능 | AI, 추적, 알림 등 | 6개 |
| 잘한 점 | 프라이버시, 무료 | 6개 |
| 개선점 | 분석, 내보내기 | 6개 |
| 기술적 특징 | AI 엔진, 보안 | 3개 |
| UX/UI 분석 | 네비, CTA, 계층 | 6개 |
| 타겟 & 포지셀 | 고객, 경쟁자 | 3개 |
| 종합 평가 | 4.2/5.0 | 3개 |

**디자인 요소**:
- 카드 호버 시 위로 부상
- 배지별 색상 분류
- 메트릭 박스로 항목 정리
- 반응형 그리드

---

### 6️⃣ Meeting-result.html 생성

**파일 크기**: 12,000 bytes (12KB)

**4가지 섹션**:

#### 1. 회의 정보
- 회의 제목
- 회의 날짜 & 시간
- 참석자
- 장소

#### 2. 회의 내용
- 주요 안건
- 결정 사항
- 다음 회의 일정

#### 3. 액션 아이템
- 체크박스 리스트
- 담당자, 마감일
- 새 과제 추가 필드

#### 4. 비고
- 추가 의견 입력
- 저장/초기화 버튼

**JavaScript 기능**:
```javascript
// localStorage 자동 저장
document.querySelectorAll('input, textarea').forEach(el => {
  el.addEventListener('change', () => {
    localStorage.setItem('meetingForm', JSON.stringify(formData));
  });
});

// 페이지 로드 시 복원
window.addEventListener('load', () => {
  const saved = localStorage.getItem('meetingForm');
  if (saved) { /* 복원 */ }
});
```

---

### 7️⃣ GitHub 연결 및 배포

#### .env 파일 설정
```env
# GitHub Fine-grained Token
GITHUB_TOKEN=github_pat_[토큰값]

# GitHub Repository
GITHUB_REPO=smitsoundlab2-gif/test
GITHUB_REPO_URL=https://github.com/smitsoundlab2-gif/test
```

#### Git 초기화 및 커밋

**커밋 히스토리**:
```
db1442b 설정: Vercel 배포 설정 추가
2067371 문서: 프로젝트 README 작성
cb4d1d7 추가: 회의록 템플릿 파일 생성
ecfa732 settings 업데이트
bdc2096 초기 커밋: 마케팅팀 대시보드, 매출 분석, 프로세스 플로우, 웹사이트 분석 리포트
```

**푸시 방법**:
```bash
source .env
git remote set-url origin "https://smitsoundlab2-gif:${GITHUB_TOKEN}@github.com/smitsoundlab2-gif/test.git"
git push origin main
```

#### Vercel 배포

**vercel.json**:
```json
{
  "outputDirectory": "3_업무",
  "rewrites": [{
    "source": "/(.*)",
    "destination": "/index.html"
  }]
}
```

**배포 현황**:
- ✅ Build Completed (35ms)
- ✅ Deployment completed
- ✅ 자동 재배포 활성화

---

## 파일별 설명

### HTML 파일 작성 공통 패턴

```html
<!DOCTYPE html>
<html lang="ko" data-theme="light">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>제목</title>
  <style>
    /* CSS 변수로 테마 관리 */
    :root {
      --text-primary: #1a1a2e;
      --card-bg: rgba(255,255,255,0.65);
      --card-shadow: 0 8px 32px rgba(80,60,180,0.10);
    }
    
    [data-theme="dark"] {
      --text-primary: #e0e0e0;
      --card-bg: rgba(255,255,255,0.06);
    }
  </style>
</head>
<body>
  <!-- 헤더 -->
  <header>
    <h1>제목</h1>
  </header>
  
  <!-- 네비게이션 -->
  <nav class="nav-menu">
    <!-- 링크 -->
  </nav>
  
  <!-- 콘텐츠 -->
  <div class="container">
    <!-- 카드들 -->
  </div>
  
  <script>
    // 테마 토글
    // 네비게이션 활성화
  </script>
</body>
</html>
```

---

## 기술 스택

### 프론트엔드
- **HTML5** — 시맨틱 마크업
- **CSS3** — 그라데이션, 블러, 애니메이션
- **Vanilla JavaScript** — 외부 라이브러리 없음
- **Canvas API** — 차트 렌더링
- **SVG** — 벡터 다이어그램

### 저장 & 관리
- **localStorage** — 브라우저 로컬 저장
- **CSV/TXT** — 데이터 소스
- **.env** — 환경변수

### 배포 & 버전 관리
- **GitHub** — 코드 저장소
- **Git** — 버전 관리
- **Vercel** — 자동 배포

---

## 배포 및 실행

### 로컬 실행

```bash
cd /Users/yoon-bible/Downloads/워크숍-실습/3_업무
python3 -m http.server 9999
```

**접속**: `http://localhost:9999/dashboard.html`

### Vercel 배포

자동 배포 (GitHub push 시):
1. push → GitHub
2. GitHub 감지 → Vercel 자동 빌드
3. 1-2분 후 배포 완료

**배포 URL**: GitHub Deployments 탭 확인

---

## 앞으로의 개선 사항

### 📌 우선순위 높음

- [ ] Vercel 배포 URL 안정화
- [ ] README 스타일시트 추가
- [ ] GitHub Pages 적용
- [ ] CSV 데이터 동적 로드 (fetch API)

### 📌 우선순위 중간

- [ ] 데이터베이스 연결 (Firebase/MongoDB)
- [ ] 사용자 인증 (OAuth)
- [ ] 실시간 알림 기능
- [ ] 데이터 내보내기 (CSV, PDF)
- [ ] 모바일 앱 (React Native)

### 📌 우선순위 낮음

- [ ] 다국어 지원 (i18n)
- [ ] 접근성 개선 (WCAG)
- [ ] SEO 최적화
- [ ] 성능 최적화 (Lighthouse 90+)
- [ ] PWA 변환

---

## 🚀 다음 아이디어 진행 방법

### 새로운 페이지 추가하기

```bash
# 1. 새 HTML 파일 생성 (기존 파일 복사)
cp dashboard.html new-page.html

# 2. 네비게이션 메뉴에 링크 추가
# → dashboard.html, chart.html 등의 nav-menu 수정

# 3. 콘텐츠 작성

# 4. 커밋 & 푸시
git add new-page.html
git commit -m "추가: 새 페이지 생성"
git push origin main
```

### 데이터 변경하기

```bash
# 1. CSV/TXT 파일 수정 (3_업무/김비서-데이터/)
# 2. HTML 파일의 데이터 업데이트
# 3. 커밋 & 푸시
```

### 스타일 변경하기

```bash
# 1. CSS 변수 수정 (:root 섹션)
# 2. 색상 팔레트 변경
# 3. 브라우저 캐시 삭제 후 새로고침
# 4. 커밋 & 푸시
```

---

## 📚 참고 자료

### 생성된 파일
- `README.md` — 프로젝트 공개 문서
- `.env.example` — 환경변수 템플릿
- `.gitignore` — Git 제외 파일
- `vercel.json` — Vercel 배포 설정

### 데이터 소스 위치
```
3_업무/김비서-데이터/
├── 매출데이터.csv (31행)
├── 업무목록.csv (11행)
├── 주간일정.txt (34행)
├── 프로젝트현황.csv (7행)
└── 회의록.txt (27행)
```

### Git 명령어 치트시트

```bash
# 상태 확인
git status

# 파일 추가
git add [파일명]

# 커밋
git commit -m "메시지"

# 푸시 (자동 인증)
source .env
git remote set-url origin "https://smitsoundlab2-gif:${GITHUB_TOKEN}@github.com/smitsoundlab2-gif/test.git"
git push origin main

# 로그 확인
git log --oneline -5
```

---

## 💡 핵심 팁

1. **CSS 변수 활용** — 색상을 한 곳에서 관리
2. **localStorage** — 사용자 입력 자동 저장
3. **Canvas API** — 외부 라이브러리 없이 차트 제작
4. **네비게이션 메뉴** — 모든 페이지에 동일한 메뉴 추가
5. **Git 토큰** — `.env` 파일에 저장, `.gitignore` 추가
6. **Vercel** — GitHub push 시 자동 배포

---

## 📞 문제 해결

### 404 에러 발생 시
```bash
# 서버 재시작
pkill -9 python3
cd 3_업무
python3 -m http.server 9999
```

### 배포 실패 시
- vercel.json 확인
- index.html 존재 확인
- git push 다시 실행

### localStorage 데이터 초기화
```javascript
// 브라우저 콘솔에서
localStorage.clear();
```

---

<div align="center">

**이 문서를 기반으로 언제든지 새로운 아이디어를 진행할 수 있습니다! 🚀**

**GitHub**: https://github.com/smitsoundlab2-gif/test

</div>
