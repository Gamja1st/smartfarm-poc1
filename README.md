# 🌱 SmartFarm PoC (Proof of Concept)

스마트팜 환경 제어 및 데이터 모니터링 시스템의 타당성을 검증하기 위한 PoC 프로젝트입니다.  
**Material for MkDocs**와 **GitHub Pages**를 활용하여, 프로젝트 문서와 개발/실험 일지(블로그)를 하나의 정적 웹사이트로 배포하도록 구성되어 있습니다.

---

## 🌐 문서 및 블로그 사이트

GitHub Pages가 활성화되면 다음 주소에서 확인하실 수 있습니다:
> `https://Gamja1st.github.io/smartfarm-poc1/`

---

## 📁 프로젝트 구조

```text
smartfarm-poc1/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Pages 자동 배포 워크플로
├── docs/                       # 웹사이트에 빌드되는 마크다운 콘텐츠
│   ├── index.md                # 메인 홈 페이지 (개요 및 대시보드)
│   ├── requirements.md         # 요구사항 정의서
│   ├── inventory.md            # 하드웨어/센서 장비 인벤토리
│   ├── architecture/
│   │   └── index.md            # 시스템 아키텍처 및 하드웨어 구성
│   ├── experiments/
│   │   └── index.md            # 실험 계획 및 로드맵
│   └── blog/                   # 블로그 / 개발 일지
│       ├── index.md            # 블로그 메인
│       └── posts/              # 일자별 포스트 (*.md)
│           ├── 2026-10-15-poc-kickoff.md     # 🇰🇷 국문 킥오프 글
│           └── 2026-10-15-poc-kickoff-en.md  # 🇺🇸 영문 킥오프 글
├── mkdocs.yml                  # MkDocs 테마 및 플러그인 설정
├── requirements-docs.txt       # MkDocs 파이썬 의존성
└── README.md                   # 저장소 안내 문서
```

---

## 🇺🇸 About This Project (English Summary)

**SmartFarm PoC** is an open hardware and software experiment to coax 6-year-old potted citrus trees into bearing fruit on a southeast-facing apartment balcony.

* **The Problem**: Potted citrus trees produce beautiful blossoms every spring, but all fruit drops prematurely due to a lack of sunlight (direct sun disappears after 2 PM).
* **The Solution**: Supplementary grow lights, real-time light monitoring & DLI (Daily Light Integral) calculation, fail-safe water tank pump, and an experimental servo-driven solar reflector (Heliostat).
* **The Philosophy**: Inspired by the **Stone Soup** fable—dropping the first stone into the pot to invite makers, embedded devs, and balcony gardeners around the world to share advice and build together!

Read the kickoff story: [Kickoff Post (EN)](docs/blog/posts/2026-10-15-poc-kickoff-en.md)


---

## 💻 로컬에서 미리보기 실행 방법

로컬에서 웹 브라우저로 사이트를 실시간 미리보며 문서를 작성할 수 있습니다.

```bash
# 1. 가상환경 생성 및 활성화
python3 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 2. 필수 패키지 설치
pip install -r requirements-docs.txt

# 3. 로컬 서버 시작
mkdocs serve
```

브라우저에서 [http://127.0.0.1:8000](http://127.0.0.1:8000)으로 접속하면 핫리로드(저장 시 자동 갱신)되는 문서를 확인할 수 있습니다.

---

## 🚀 GitHub에 올리고 블로그 배포하는 방법

1. **GitHub에 새 Repository 생성**
   - 저장소 이름: `smartfarm-poc1` (Public 권장)

2. **현재 로컬 코드를 원격 저장소에 Push**
   ```bash
   git add .
   git commit -m "feat: initial commit for smartfarm citrus poc project"
   git remote add origin https://github.com/Gamja1st/smartfarm-poc1.git
   git branch -M main
   git push -u origin main
   ```

3. **GitHub 저장소 설정에서 Pages 활성화**
   - GitHub 저장소 페이지의 **Settings** 탭으로 이동
   - 좌측 메뉴의 **Pages** 클릭
   - **Build and deployment > Source** 항목을 `Deploy from a branch` 대신 **`GitHub Actions`**로 선택
   - 잠시 후 **Actions** 탭에서 `Deploy MkDocs to GitHub Pages` 워크플로가 자동 실행되며 사이트가 배포됩니다.

4. **새 글(블로그/실험 일지) 작성하기**
   - `docs/blog/posts/YYYY-MM-DD-제목.md` 파일을 생성하여 마크다운으로 작성하고 `push`하면 자동으로 사이트에 새 글이 반영됩니다.

