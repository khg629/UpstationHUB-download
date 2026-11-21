# Upstation HUB 사용 설명서

태스크마다 AI(Claude · Codex · Gemini)를 붙여 일을 맡기는 작업 허브예요. 처음 받는 분은 이 순서대로 하시면 돼요.

**[최신 버전 받기 →](https://github.com/khg629/UpstationHUB-download/releases/latest)**

| 운영체제 | 받을 파일 |
|---|---|
| Windows (64비트) | `Upstation-HUB-Setup-<버전>.exe` |
| macOS (M1 이상 애플 실리콘) | `Upstation-HUB-<버전>-mac-arm64.zip` · 인텔 맥은 지원하지 않아요 |

---

## 1. HUB 설치

### Windows
1. `Upstation-HUB-Setup-<버전>.exe`를 실행해요.
2. "Windows의 PC 보호" 창이 뜨면 **추가 정보 → 실행**을 눌러요. (코드 서명이 없어서 뜨는 경고예요.)

### macOS
1. zip을 풀고 `Upstation HUB.app`을 **응용 프로그램** 폴더로 옮겨요.
2. 터미널(응용 프로그램 › 유틸리티 › 터미널)을 열고 아래를 한 번 실행해요. 안 하면 "손상되었기 때문에 열 수 없습니다"가 떠요.
   ```
   xattr -cr "/Applications/Upstation HUB.app"
   ```
3. 앱을 열어요.

---

## 2. AI 연결하기

HUB는 컴퓨터에 설치된 AI 프로그램(CLI)을 불러 써요. **Claude는 꼭 필요하고**, Codex와 Gemini는 쓰고 싶을 때만 설치하면 돼요.

| AI | 필요한 계정 | 필수 |
|---|---|---|
| Claude (Claude Code) | Claude Pro 또는 Max 구독 | ✅ |
| Codex | ChatGPT Plus 이상 구독 | 선택 |
| Gemini (Antigravity CLI) | Google 계정 | 선택 |

> 명령어는 **터미널**(맥) 또는 **PowerShell**(윈도우: 시작 메뉴에서 "PowerShell" 검색)에 붙여 넣고 Enter를 누르면 돼요.
> **설치가 끝나면 터미널을 닫았다가 새로 열어야** 다음 명령이 인식돼요.

### ① Claude (필수)
설치:
- 맥: `curl -fsSL https://claude.ai/install.sh | bash`
- 윈도우: `irm https://claude.ai/install.ps1 | iex`

로그인: 새 터미널에서 `claude`를 실행하면 브라우저가 열려요. Claude 계정으로 로그인하고, 터미널에 "Welcome"이 보이면 `/exit`로 나와요.

윈도우는 [Git for Windows](https://git-scm.com/download/win)도 설치해 두는 걸 권장해요.

### ② Codex (선택)
1. [Node.js](https://nodejs.org) LTS 버전을 먼저 설치해요.
2. 설치: `npm i -g @openai/codex` (맥은 `brew install --cask codex`도 돼요)
3. 로그인: `codex`를 실행하고 **Sign in with ChatGPT**를 골라 ChatGPT 계정으로 로그인해요.

윈도우에서는 Codex가 아직 시험 단계라 잘 안 될 수 있어요.

### ③ Gemini (선택)
설치:
- 맥: `curl -fsSL https://antigravity.google/cli/install.sh | bash`
- 윈도우: `irm https://antigravity.google/cli/install.ps1 | iex`

로그인: 새 터미널에서 `agy`를 실행하고 Google 계정으로 로그인해요.

### ④ 연결 확인
1. AI를 설치하고 로그인했으면 **HUB를 완전히 껐다가 다시 켜요.** HUB는 켤 때 AI를 찾아요.
   - 맥: 화면 위 메뉴 막대의 HUB 아이콘 › **Upstation HUB 종료** (창만 닫으면 백그라운드에 남아 있어요)
2. **설정(⌘, / Ctrl+,) › 에이전트 기본값**에서 AI 목록을 봐요.
   - 이름만 보이면 연결 완료
   - **— 미설치**: 설치가 안 됐거나 HUB가 못 찾았어요. 설치 후 HUB를 다시 켰는지 확인하세요.
   - **— 로그인 필요**: 터미널에서 다시 로그인하세요.

---

## 3. 처음 써 보기

1. **태스크 만들기**: 왼쪽 위 "태스크 추가"에 할 일을 적고 **추가**. `#프로젝트이름`을 붙이면 그 프로젝트로 들어가요.
2. **AI에게 맡기기**: 가운데 입력창에 하고 싶은 일을 적고 보내요. AI가 일하는 동안 다른 태스크를 봐도 돼요. 끝나면 알림이 와요.
3. **작업 폴더 연결**: 태스크 위쪽 **폴더 연결**로 AI가 일할 폴더를 정해요. 연결하지 않으면 HUB 안의 태스크 전용 폴더에서 일해요.
4. **AI 고르기**: 입력창 아래에서 AI(Claude Code · Codex · Gemini)와 모델을 바꿀 수 있어요.
5. **권한**: 입력창 아래 방패 아이콘
   - **편집 허용** (기본, 권장): 파일 수정은 알아서, 위험할 수 있는 명령은 막아요.
   - **모두 허용**: 확인 없이 모든 명령을 실행해요. 믿을 수 있는 작업에만 쓰세요.
6. **AI 여러 개**: 태스크 위쪽 **+ AI 추가**로 같은 태스크에 AI를 더 붙여요. 예: Claude가 만들고 Codex가 검토. **나란히**를 누르면 대화를 옆으로 놓고 비교해요.
7. **메모**: 태스크마다 메모가 있어요. AI도 이 메모를 읽고 써요.
8. **완료**: 다 끝난 태스크는 왼쪽 동그라미를 누르거나 **완료 → 다음**을 눌러요.

---

## 4. 더 쓰기 (선택)

- **Gmail · Notion 같은 서비스**: [claude.ai](https://claude.ai) › 설정 › 커넥터에서 연결한 뒤, HUB **설정 › 커넥터 허용**에서 켜요.
- **AI가 브라우저 쓰게 하기**: **설정 › AI 브라우저 조작**을 켜면, AI가 오른쪽 브라우저 창에서 페이지를 열고 읽고 눌러요.
- **휴대폰에서 보기**: **설정 › 원격 접속 · 밖에서 휴대폰으로**에서 QR을 띄우고 휴대폰으로 찍어요. 밖에서도 HUB 화면을 볼 수 있어요. (이 컴퓨터의 HUB가 켜져 있어야 해요.)

---

## 자주 묻는 것

**Q. AI에게 보냈는데 아무 반응이 없어요.**
설정 › 에이전트 기본값에서 그 AI가 "미설치"나 "로그인 필요"인지 보세요. 터미널에서 `claude`(또는 `codex`, `agy`)를 직접 실행해 로그인이 살아 있는지 확인하고, HUB를 다시 켜 보세요.

**Q. "모두 허용"인데도 명령이 막혔다고 나와요.**
지우는 명령처럼 위험할 수 있는 건 AI 프로그램 자체의 안전장치가 막아요. 권한 설정과는 무관해요. AI에게 다시 시키면 보통 안전한 방식으로 고쳐서 실행해요.

**Q. 사용량은 어디서 빠지나요?**
각자의 구독에서 빠져요. Claude는 Claude 플랜, Codex는 ChatGPT 플랜, Gemini는 Google 계정 한도를 써요. HUB 아래쪽 막대에 남은 양이 보여요.

**Q. 새 모델이 안 보여요.**
설정 › 에이전트 기본값 › **AI CLI 업데이트**를 눌러요.
