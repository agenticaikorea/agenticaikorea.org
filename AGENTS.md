# agenticaikorea.org

Agentic AI Korea 커뮤니티 웹사이트 저장소다. 이 저장소는 공개 저장소이고 이 파일도 공개된다.

## 구성

- 빌드 도구 없는 정적 사이트로 시작한다. 첫 화면은 `public/index.html` 한 장이다.
- 사이트에 올라가는 파일은 `public/` 안에만 둔다. `public/` 밖의 파일(이 파일, README 등)은 사이트 주소로 열리지 않는다.
- 배포는 Cloudflare Workers(정적 자산)로 한다. 첫 배포는 운영자가 직접 하고 그 뒤로는 Workers Builds가 `main`
  브랜치에 푸시될 때마다 자동으로 배포한다. Worker 설정은 `wrangler.jsonc`이고 Worker 이름 `agenticaikorea-org`는
  Cloudflare 쪽 이름과 같아야 한다. 사용자 도메인 `agenticaikorea.org`도 이 파일의 `routes`로 지정한다.
  이 파일에 계정 값과 토큰을 넣지 않는다. DNS 레코드, 메일 같은 Cloudflare 계정 쪽 설정은 이 저장소에서 하지 않는다.
- 페이지는 `public/` 아래에서 만들고 고쳐 `main`에 push하면 된다. `wrangler.jsonc`의 `name`, `routes`, 바인딩(KV, D1, R2 등)을
  바꾸려면 push 전에 Cloudflare 계정을 관리하는 운영자(조훈)에게 먼저 알린다. 빌드에 사용하는 토큰은 이 도메인과 Worker 배포에
  필요한 권한만 가지고 있어서 바인딩을 더하면 권한이 없어 빌드가 실패한다. 빌드가 실패해도 공개 사이트는 이전 버전이 유지된다.
  `compatibility_date`처럼 Cloudflare 자원에 영향이 없는 값은 알리지 않아도 된다.
- 공개 전에 확인하려면 `main`이 아닌 브랜치에서 작업하고 `main`으로 PR을 연다. Workers Builds가 그 브랜치의 미리 보기를 만들고
  주소는 `<브랜치 이름>-agenticaikorea-org.<계정의 workers.dev 서브도메인>.workers.dev` 형태다. PR에 주소 댓글은 달리지 않는다.
  브랜치 이름은 소문자와 하이픈으로 짓는다. 미리 보기 주소는 아는 사람 누구나 열 수 있고 검색 엔진에는 노출되지 않는다.
- `wrangler.jsonc`에는 `"workers_dev": false`와 `"preview_urls": true`를 적어 둔다. 적지 않으면 운영 배포 때 미리 보기 주소가
  꺼진다. `workers_dev`는 공개 사이트와 같은 내용이 workers.dev 주소로 따로 열리지 않게 끈 값이다. 이 값들을 바꾸려면 운영자에게
  먼저 알린다.
- 한국어 페이지는 `/`, 영어 페이지는 `/en/`에 둔다. 머리 띠의 한국어/English 버튼으로 언어를 바꾼다. 브라우저 언어로 자동 전환하지 않는다.
  행사 후기 같은 게시물은 한국어로만 올린다. 게시물을 올리면 `/en/` 첫 화면 목록에 영어 제목과 한두 줄 요약을 더하고
  한국어 글이라고 표시한다. 영어판이 없는 한국어 게시물의 English 버튼은 `/en/`으로 연결한다.
- 로고는 `public/assets/`에 둔다. 로고 원본과 생성 스크립트는 운영진의 비공개 저장소에 있다.

## 지킬 것

- 이 저장소의 파일, 커밋 메시지, 이슈에 비공개 저장소 이름, 로컬 절대 경로, 연락처, 예산, 영수증을 적지 않는다.
- 에이전틱 AI 재단(AAIF)의 로고 마크는 재단의 허락을 먼저 받은 뒤에만 넣는다.
- 색은 검정 `#000000`, 흰색 `#FFFFFF`, 강조 주황 `#FF702D`를 기본으로 한다. 글꼴은 Instrument Sans다.
- 사이트에 실리는 한국어 문구는 운영자 명의로 나가는 글이다. 문구를 바꾸면 운영자의 검토를 받은 뒤 푸시한다.
- 자격증 할인 배너는 운영자 개인 사이트(`promo.kuberneteslab.dev`)로 연결한다. 할인율과 기간은 그 사이트의 공개
  정보만 사용하고 다른 할인 경로와 비교하는 문장을 넣지 않는다.
