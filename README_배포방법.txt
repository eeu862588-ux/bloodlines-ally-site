# Bloodlines Ally — 배포 안내

## 구성
- `index.html`: 모바일 대응 아군 닉네임 등록/검색/삭제 사이트
- `supabase.sql`: 공유 데이터베이스 테이블 및 공개 접근 정책

## 1. Supabase 데이터베이스 만들기
1. https://supabase.com 에서 가입하고 새 프로젝트를 만듭니다.
2. 프로젝트의 **SQL Editor**를 열고 `supabase.sql` 전체 내용을 붙여 넣어 실행합니다.
3. Project Settings / API (또는 Connect 화면)에서 Project URL과 **publishable key / anon key**를 복사합니다.
4. `index.html`을 편집하고 아래 두 값을 실제 값으로 바꿉니다.
   - `YOUR_SUPABASE_URL`
   - `YOUR_SUPABASE_ANON_KEY`
5. **service_role key 또는 secret key는 절대 HTML에 넣지 마세요.** 브라우저에 공개되는 키는 RLS 정책으로 제한해야 합니다.

## 2. 무료로 Cloudflare Pages에 배포
1. https://github.com/new 에서 새 **Public** 저장소를 만듭니다. 예: `bloodlines-ally`
2. `index.html`을 저장소 최상위에 올립니다.
3. https://dash.cloudflare.com 에 로그인하고 **Workers & Pages → Create → Pages → Connect to Git**으로 GitHub 저장소를 연결합니다.
4. 프레임워크는 `None` 또는 `Static HTML`을 선택하고 Build command는 비워 두고, output directory는 `/` 또는 저장소 루트로 지정합니다.
5. 배포를 완료하면 `https://프로젝트이름.pages.dev` 형태의 주소가 생성됩니다. Cloudflare 대시보드의 현재 안내를 따라 설정하세요.

대안: GitHub Pages도 정적 사이트 호스팅이 가능합니다. `index.html`과 Supabase 연결을 설정한 뒤 저장소 Settings → Pages에서 배포할 수 있습니다.

## 기능과 한계
- 모든 방문자가 같은 Supabase 데이터베이스를 사용하므로 목록을 공유합니다.
- 검색은 등록된 목록에서 닉네임 일부를 찾습니다.
- 닉네임은 Roblox username 형식(영문/숫자/밑줄, 3~20자)만 허용합니다.
- 이 사이트는 Roblox 게임 서버나 플레이어 팀을 실시간으로 확인하지 않습니다.
- 공개 정책이므로 누구나 등록 및 삭제할 수 있고, 악의적인 삭제/스팸이 가능할 수 있습니다. 널리 공개하기 전에는 로그인, 관리자 권한, 속도 제한, 신고/복구 기능을 추가하는 것이 좋습니다.
- Supabase 무료 프로젝트에는 사용량 제한 및 비활성 일시 중지 조건이 있을 수 있습니다. 현재 한도는 공식 요금 안내를 확인하세요.
