# Upstation HUB 설치 안내

할 일(태스크)마다 AI를 붙여 일을 맡기는 작업 공간이에요. 처음 받는 분은 이 순서대로 하시면 돼요.

| 받기 | |
|---|---|
| **Windows** (64비트) | ⬇️ [Upstation-HUB-Setup.exe](https://github.com/khg629/UpstationHUB-download/releases/latest/download/Upstation-HUB-Setup.exe) |
| **맥** (M1 이상 애플 실리콘) | ⬇️ [Upstation-HUB-mac-arm64.zip](https://github.com/khg629/UpstationHUB-download/releases/latest/download/Upstation-HUB-mac-arm64.zip) · 인텔 맥은 지원하지 않아요 |

링크는 항상 최신 버전을 받아요. 바뀐 점은 [릴리스 목록](https://github.com/khg629/UpstationHUB-download/releases)에 있어요.

**이 안내는 Windows 기준이에요.** 맥은 [맨 아래](#맥에서-설치하기)를 보세요.

## 시작 전에 확인하기

HUB는 내 컴퓨터에 설치된 **AI 프로그램(CLI)** 을 불러서 일해요. 그래서 **AI 프로그램을 먼저 설치하고 로그인한 다음** HUB를 설치해요.

| AI | 필요한 계정 | |
|---|---|---|
| **Claude** (Claude Code) | Claude **Pro 또는 Max** 구독. 무료 플랜은 안 돼요. | **꼭 필요해요** → [1단계](#1단계-claude-설치-필수) |
| ChatGPT (Codex) | ChatGPT 계정. Plus 이상 권장 | 쓰고 싶을 때만 → [선택 A](#선택-a-chatgpt-codex) |
| Gemini (Antigravity) | 개인 Google 계정. 회사·학교 Workspace 계정은 안 돼요. | 쓰고 싶을 때만 → [선택 B](#선택-b-gemini) |

**준비물**: Windows 10(1809 이상) 또는 Windows 11, 64비트. 다 하면 15분쯤 걸려요.

### PowerShell 여는 법 (아래 단계에서 계속 써요)
키보드의 **Windows 키**를 누르고 `powershell`을 입력한 뒤 **Windows PowerShell**을 눌러요. 관리자 권한은 필요 없어요.
명령을 붙여 넣을 때는 **마우스 오른쪽 클릭** 또는 **Ctrl+V**, 실행은 **Enter**예요.

---

## 1단계. Claude 설치 (필수)

1. **Git 설치**: [git-scm.com/download/win](https://git-scm.com/download/win)에서 설치 파일을 받아 실행하고, 설정은 바꾸지 말고 **Next**만 눌러 설치해요. (Claude가 명령을 실행할 때 써요.)
2. PowerShell을 열고 아래 명령을 붙여 넣고 Enter를 눌러요.
   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```
3. 설치가 끝나면 **PowerShell 창을 닫고 새로 열어요.** (새 창이어야 방금 설치한 프로그램을 찾아요.)
4. 새 창에서 `claude`를 입력하고 Enter를 눌러요. 화면 색 같은 질문은 **Enter**로 넘어가요.
5. 로그인 방법을 물으면 **Claude 구독 계정**(Claude account with subscription)을 고르고, 브라우저에서 로그인한 뒤 **승인**(Authorize)을 눌러요.
   - 브라우저에 코드가 나오면 복사해서 PowerShell에 붙여 넣고 Enter를 눌러요.
6. 입력창이 나오면 성공이에요. `/exit`를 입력해 나와요.

ChatGPT나 Gemini도 쓰고 싶으면 아래 선택 단계를 하고, 아니면 바로 [2단계. HUB 설치](#2단계-hub-설치)로 가요.

### 선택 A. ChatGPT (Codex)
1. PowerShell에 아래 명령을 붙여 넣고 Enter를 눌러요.
   ```powershell
   powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"
   ```
2. **PowerShell 창을 닫고 새로 열어요.**
3. `codex login`을 입력해요. 브라우저가 열리면 **ChatGPT 계정으로 로그인**하고 승인해요.
4. `codex login status`를 입력해 **Logged in using ChatGPT**가 나오면 성공이에요.

### 선택 B. Gemini
1. PowerShell에 아래 명령을 붙여 넣고 Enter를 눌러요.
   ```powershell
   irm https://antigravity.google/cli/install.ps1 | iex
   ```
2. **PowerShell 창을 닫고 새로 열어요.**
3. `agy`를 입력하고 Enter를 눌러요. 화면 색 같은 질문은 **Enter**로 넘어가요.
4. 로그인 방법을 물으면 **Google 계정**(Google OAuth)을 고르고, 브라우저에서 개인 Google 계정으로 로그인해요.
5. 입력창이 나오면 성공이에요. `/exit`를 입력해 나와요.

---

## 2단계. HUB 설치

1. 설치 파일을 받아요: ⬇️ [Upstation-HUB-Setup.exe 받기](https://github.com/khg629/UpstationHUB-download/releases/latest/download/Upstation-HUB-Setup.exe)
2. 받은 `Upstation-HUB-Setup.exe`를 실행해요.
3. **"Windows의 PC 보호"** 파란 창이 뜨면 **추가 정보**를 누르고 **실행**을 눌러요. (코드 서명이 없어서 뜨는 경고예요.)
4. 설치 화면에서는 아무것도 바꾸지 말고 **다음**(또는 **설치**)을 눌러 진행하고, 마지막에 **마침**을 눌러요.
5. 시작 메뉴나 바탕화면의 **Upstation HUB**를 열어요.

---

## 3단계. HUB에서 연결 확인

1. HUB 오른쪽 위 **설정**(또는 **Ctrl + ,**)을 눌러요.
2. **에이전트 기본값**에서 AI 목록을 봐요. (ChatGPT는 목록에 **Codex**로 보여요.)
   - 이름만 보이면 연결 완료예요.
   - 이름 옆에 **— 미설치**가 붙어 있으면: HUB가 그 AI를 찾지 못했어요. 아래 "HUB 완전히 껐다 켜기"를 해 보고, 그래도 같으면 1단계를 다시 확인해요.
   - **— 로그인 필요**가 붙어 있으면: 1단계의 로그인을 다시 해요.
3. 태스크를 하나 만들고 가운데 입력창에 아무 일이나 적어 보내 보세요. AI가 답하면 준비 끝이에요. 🎉

> **HUB 완전히 껐다 켜기**
> 창의 X를 눌러도 HUB는 꺼지지 않고 작업 표시줄 오른쪽 아래(시계 옆 **^** 안)에 남아 있어요.
> 그 아이콘을 **오른쪽 클릭 › Upstation HUB 종료**를 누른 다음, 다시 열어요. HUB는 켤 때 AI를 찾아요.
> **AI를 새로 설치했다면 꼭 이렇게 껐다 켜야** HUB가 찾아요.

---

## 처음 써 보기

1. **태스크 만들기**: 왼쪽 위 "태스크 추가"에 할 일을 적고 **추가**. `#프로젝트이름`을 붙이면 그 프로젝트로 들어가요.
2. **AI에게 맡기기**: 가운데 입력창에 하고 싶은 일을 적고 보내요. AI가 일하는 동안 다른 태스크를 봐도 돼요. 끝나면 알림이 와요.
3. **작업 폴더 연결**: 태스크 위쪽 **폴더 연결**로 AI가 일할 폴더를 정해요. 연결하지 않으면 HUB 안의 태스크 전용 폴더에서 일해요.
4. **AI 고르기**: 입력창 아래에서 AI(Claude Code · Codex · Gemini)와 모델을 바꿀 수 있어요.
5. **권한**: 입력창 아래 방패 아이콘
   - **편집 허용** (기본, 권장): 파일 수정은 알아서, 위험할 수 있는 명령은 막아요.
   - **모두 허용**: 확인 없이 모든 명령을 실행해요. 믿을 수 있는 작업에만 쓰세요.
6. **AI 여러 개**: 태스크 위쪽 **+ AI 추가**로 같은 태스크에 AI를 더 붙여요. 예: Claude가 만들고 Codex가 검토. **나란히**를 누르면 대화를 옆으로 놓고 비교해요.
7. **메모와 결과물**: 태스크 오른쪽 창에 메모와 결과물이 있어요. AI도 메모를 읽고 쓰고, AI가 만든 파일은 결과물에 모여요.
8. **완료**: 다 끝난 태스크는 왼쪽 동그라미를 누르거나 **완료 → 다음**을 눌러요.

---

## 더 쓰기 (선택)

- **팀**: 위쪽 팀 탭을 고르면 그 팀 **팀장**에게 일을 맡길 수 있어요. 팀장이 계획을 세우고 팀 태스크로 나눠 줘요.
- **채팅**: 위쪽 **채팅**은 가볍게 묻고 답하는 곳이에요. 일이 커지면 **태스크로 만들기**를 눌러요.
- **Gmail · Notion 같은 서비스**: [claude.ai](https://claude.ai) › 설정 › 커넥터에서 연결한 뒤, HUB **설정 › 커넥터 허용**에서 켜요.
- **AI가 브라우저 쓰게 하기**: **설정 › AI 브라우저 조작**을 켜면, AI가 오른쪽 브라우저 창에서 페이지를 열고 읽고 눌러요.
- **휴대폰에서 보기**: **설정 › 원격 접속 · 밖에서 휴대폰으로**에서 QR을 띄우고 휴대폰으로 찍어요. (이 컴퓨터의 HUB가 켜져 있어야 해요.)

---

## 자주 묻는 것

**Q. AI에게 보냈는데 아무 반응이 없어요.**
설정 › 에이전트 기본값에서 그 AI 옆에 "미설치"나 "로그인 필요"가 있는지 보세요. PowerShell(맥은 터미널)에서 `claude`(또는 `codex login status`, `agy`)를 실행해 로그인이 살아 있는지 확인하고, HUB를 완전히 껐다 켜 보세요.

**Q. PowerShell에서 "용어가 cmdlet, 함수… 이름으로 인식되지 않습니다"가 나와요.**
설치 직후라면 PowerShell 창을 **모두 닫고 새로 열어** 다시 해 보세요. 그래도 안 되면 컴퓨터에서 로그아웃했다 다시 로그인해 보세요.

**Q. "Claude 서버가 붐벼서 답하지 못했어요"가 나와요.**
Claude 쪽 서버가 잠깐 몰린 거예요. HUB가 다른 Claude 모델로 먼저 넘겨 보고, 그래도 안 될 때만 이 문구가 나와요. 1~2분 뒤 다시 보내세요.

**Q. "모두 허용"인데도 명령이 막혔다고 나와요.**
지우는 명령처럼 위험할 수 있는 건 AI 프로그램 자체의 안전장치가 막아요. 권한 설정과는 무관해요. AI에게 다시 시키면 보통 안전한 방식으로 고쳐서 실행해요.

**Q. 사용량은 어디서 빠지나요?**
각자의 구독에서 빠져요. Claude는 Claude 플랜, Codex는 ChatGPT 플랜, Gemini는 Google 계정 한도를 써요. HUB 아래쪽 막대에 남은 양이 보여요.

**Q. 새 버전은 어떻게 받나요?**
HUB가 알아서 받아요. 새 버전이 준비되면 알림이 뜨고 맨 위에 파란 **업데이트** 버튼이 생겨요. 누르면 HUB가 다시 켜지면서 적용돼요(누르지 않아도 다음에 HUB를 껐다 켤 때 적용돼요). 지금 버전과 수동 확인은 설정 › **앱 업데이트**에 있어요. 내 태스크와 메모는 그대로 남아요.
설정에 **앱 업데이트**가 없다면 자동 업데이트 전 버전이에요. 이번 한 번만 맨 위 링크로 다시 받아 설치하세요.

**Q. 새 모델이 안 보여요.**
설정 › 에이전트 기본값 › **AI CLI 업데이트**를 눌러요.

---

## 맥에서 설치하기

M1 이상(애플 실리콘) 맥만 지원해요. 인텔 맥은 지원하지 않아요. 터미널은 **응용 프로그램 › 유틸리티 › 터미널**에 있어요.

1. **Claude 설치 (필수)**: 터미널에 아래를 붙여 넣고 Enter를 눌러요.
   ```
   curl -fsSL https://claude.ai/install.sh | bash
   ```
   터미널을 닫고 새로 연 뒤 `claude`를 입력해요. **Claude 구독 계정**으로 로그인하고, 입력창이 나오면 `/exit`로 나와요.
2. **선택**: ChatGPT는 `curl -fsSL https://chatgpt.com/codex/install.sh | sh` 후 `codex login`, Gemini는 `curl -fsSL https://antigravity.google/cli/install.sh | bash` 후 터미널을 새로 열고 `agy`.
3. **HUB 받기**: ⬇️ [Upstation-HUB-mac-arm64.zip 받기](https://github.com/khg629/UpstationHUB-download/releases/latest/download/Upstation-HUB-mac-arm64.zip)
4. zip을 풀고 `Upstation HUB.app`을 **응용 프로그램** 폴더로 옮겨요.
5. 터미널에서 아래를 한 번 실행해요. 안 하면 "손상되었기 때문에 열 수 없습니다"가 떠요.
   ```
   xattr -cr "/Applications/Upstation HUB.app"
   ```
6. 앱을 열고 위 **3단계**처럼 연결을 확인해요. (설정은 **⌘ ,**, 완전히 끄기는 화면 위 메뉴 막대의 HUB 아이콘 › **Upstation HUB 종료**)
