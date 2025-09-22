# 김개발 포트폴리오 (AI-Lecture)

정적 HTML/CSS/JS로 구성된 개인 포트폴리오 사이트입니다. 반응형 UI, 부드러운 스크롤, 섹션별 스크롤 애니메이션, 타이핑 효과, 스킬 바 애니메이션, 모바일 내비게이션 등을 제공합니다.

## 주요 기능
- 헤더/내비게이션: 고정 헤더, 현재 섹션 활성화, 모바일 햄버거 메뉴
- 히어로: 다국어 멀티 타이핑 효과, 페이드 인, CTA 버튼
- 소개: 간단 소개 및 통계 카드
- 기술: IntersectionObserver 기반 스킬 바 애니메이션
- 경력: 타임라인 레이아웃과 스크롤 인 애니메이션
- 프로젝트: 카드 호버 효과, 기술 태그, 링크 버튼
- 연락처: 정보/소셜 링크/폼(프론트 유효성 검사)
- 전역: 부드러운 스크롤, ESC/외부 클릭/리사이즈 시 모바일 메뉴 닫기

## 폴더 구조
```
/Users/insanebear/Projects/AI-Lecture/
├── index.html   # 마크업(섹션 구성 및 데이터 속성)
├── style.css    # 전체 스타일(반응형/애니메이션 포함)
└── script.js    # 상호작용 및 애니메이션 로직
```

## 기술 스택
- HTML5, CSS3
- 바닐라 JavaScript (ES6+)
- Google Fonts: Noto Sans KR

## 실행 방법
1. 프로젝트를 클론 또는 다운로드합니다.
2. 아래 파일을 브라우저로 직접 열면 동작합니다.
   - `index.html`
3. 별도 빌드/런타임이 필요 없는 정적 사이트입니다.

## 페이지 구성
- `#home` 히어로: 이름, 멀티 타이핑(`.typing-text[data-texts]`), 커서(`.cursor`), CTA 버튼
- `#about` 소개: 소개 문구, 경력/프로젝트/만족도 통계
- `#skills` 기술: 카테고리(Frontend/Backend/Database/DevOps), 진행 바 애니메이션
- `#experience` 경력: 타임라인 레이아웃(교차 정렬), 항목별 리스트
- `#projects` 프로젝트: 카드형 목록, 기술 태그, 링크 버튼
- `#contact` 연락처: 이메일/전화/위치, 소셜 링크, 문의 폼

## 상호작용과 애니메이션 개요 (script.js)
- DOMContentLoaded 이후 초기화
- 모바일 메뉴 토글: `.hamburger` ↔ `.nav-menu.active`
- 내비게이션 스무스 스크롤 및 현재 섹션 활성화
- 스크롤에 따른 헤더 배경/그림자 변경
- 스킬 바 애니메이션: `IntersectionObserver`로 `.skill-progress[data-width]` 너비 적용 및 1회 실행
- 멀티 타이핑: `multiTypeWriter(element, texts, typeSpeed, deleteSpeed, pauseTime)`
- 히어로 타이핑: `typeWriter`로 `.hero-title` 초기 텍스트 타이핑
- AOS 유사 스크롤 애니메이션: `.timeline-item, .project-card, .skill-category`에 페이드/슬라이드 인
- 접근성/UX: ESC/외부 클릭/리사이즈 시 모바일 메뉴 닫기, 전역 부드러운 스크롤
- 초기 페이드 인: `body`에 opacity 전환
- 유틸: `utils.debounce`, `utils.throttle` 및 60fps 목표 스크롤 핸들러 샘플

## 스타일 개요 (style.css)
- 기본 리셋과 타이포그래피, 컨테이너 레이아웃
- 고정 헤더, 링크 호버 언더라인 애니메이션
- 히어로 그라데이션 배경, 이름 그라데이션 텍스트, 타이핑 하이라이트/섬광 효과, 커서 깜박임
- 섹션별 레이아웃(About/Skills/Experience/Projects/Contact)과 카드/타임라인/그리드
- 버튼 스타일(Primary/Secondary/Outline)
- 반응형: 768px, 480px 브레이크포인트 대응

## 커스터마이징 가이드
- 이름/타이틀/문구: `index.html`의 각 섹션 텍스트 수정
- 멀티 타이핑 문구: 히어로의 `.typing-text` 요소 `data-texts` JSON 배열 변경
- 스킬 퍼센트: `.skill-progress`의 `data-width="NN%"` 값 조정
- 프로젝트 카드: `#projects` 섹션에 카드 블록을 복제/수정하여 추가
- 색상/테마: `style.css`의 그라데이션/포인트 컬러(`#3498db`, `#2ecc71`, `#667eea`, `#764ba2`) 변경

## 양식(폼) 동작
- 현재는 프론트엔드 유효성 검사 및 성공 알림만 수행합니다.
- 실제 전송을 위해서는 백엔드 엔드포인트 또는 서버리스 함수 연동이 필요합니다.

## 접근성/성능 참고
- 키보드 ESC/외부 클릭으로 모바일 메뉴 닫기 지원
- 스크롤 이벤트에 `throttle` 적용 샘플 포함
- `IntersectionObserver`로 스킬 바 애니메이션 지연 로딩

## 알려진 제약/개선 제안
- 폼 제출: 백엔드 연동 미구현
- 내비게이션 활성화 오프셋: 고정 헤더 높이에 따라 조정 필요
- AOS 유사 애니메이션은 인라인 스타일 기반으로, 클래스로 전환하면 유지보수 용이
- 전역 `scroll-behavior`는 일부 브라우저 호환성 차이 존재

## 라이선스
- 별도 라이선스 명시가 없으므로 내부/개인용 참고용으로 가정합니다. 공개 배포 시 라이선스를 추가하세요.

## 크레딧
- 폰트: Google Fonts(Noto Sans KR)
- 아이콘 플레이스홀더: 이모지

---
이 README는 `index.html`, `script.js`, `style.css`의 실제 구현을 기반으로 생성되었습니다.
