# agenticaikorea.org

Agentic AI Korea 커뮤니티 웹사이트 저장소다. 이 저장소는 공개 저장소이고 이 파일도 공개된다.

## 구성

- 빌드 도구 없는 정적 사이트로 시작한다. 첫 화면은 `public/index.html` 한 장이다.
- 사이트에 올라가는 파일은 `public/` 안에만 둔다. `public/` 밖의 파일(이 파일, README 등)은 사이트 주소로 열리지 않는다.
- 배포는 Cloudflare Workers(정적 자산)로 한다. 첫 배포는 운영자가 직접 하고 그 뒤로는 Workers Builds가 `main`
  브랜치에 푸시될 때마다 자동으로 배포한다. Worker 설정은 `wrangler.jsonc`이고 Worker 이름 `agenticaikorea-org`는
  Cloudflare 쪽 이름과 같아야 한다. 사용자 도메인 `agenticaikorea.org`도 이 파일의 `routes`로 지정한다.
  이 파일에 계정 값과 토큰을 넣지 않는다. DNS 레코드, 메일 같은 Cloudflare 계정 쪽 설정은 이 저장소에서 하지 않는다.
- 로고는 `public/assets/`에 둔다. 로고 원본과 생성 스크립트는 운영진의 비공개 저장소에 있다.

## 지킬 것

- 이 저장소의 파일, 커밋 메시지, 이슈에 비공개 저장소 이름, 로컬 절대 경로, 연락처, 예산, 영수증을 적지 않는다.
- 에이전틱 AI 재단(AAIF)의 로고 마크를 넣지 않는다. 이 커뮤니티는 AAIF의 공식 조직이 아니다. 마크를 사용하려면
  재단의 허락을 먼저 받는다.
- 색은 검정 `#000000`, 흰색 `#FFFFFF`, 강조 주황 `#FF702D`를 기본으로 한다. 글꼴은 Instrument Sans다.
- 사이트에 실리는 한국어 문구는 운영자 명의로 나가는 글이다. 문구를 바꾸면 운영자의 검토를 받은 뒤 푸시한다.
- 자격증 할인 배너는 운영자 개인 사이트(`promo.kuberneteslab.dev`)로 연결한다. 할인율과 기간은 그 사이트의 공개
  정보만 사용하고 다른 할인 경로와 비교하는 문장을 넣지 않는다.
