[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — 무료 클라우드 브라우저

GitHub Actions의 무료 Ubuntu 가상 머신으로 브라우저에서 원격으로 조작할 수 있는 클라우드 데스크톱을 만들어 보세요. Chrome이 내장되어 있습니다. 웹 페이지만 열면 인터넷에 연결된 클라우드 PC를 바로 쓸 수 있고, 다 쓰면 꺼두면 됩니다. 전 과정 무료입니다.

## ✨ 기능

- 🌐 Ubuntu 데스크톱 + Chrome 브라우저, 브라우저 안에서 바로 조작
- ⌨️ fcitx5 중국어 입력기(병음) 내장, `Ctrl+Space`로 중/영 전환
- 📋 휴대폰에서 복사한 중국어를 원격 데스크톱에 바로 붙여넣기 가능
- 🖱️ 데스크톱 오른쪽 클릭 메뉴에서 입력기 전환·Chrome 재시작을 한 번에
- 🌐 Cloudflare 터널로 접속, 공인 IP·포트 포워딩 불필요
- 🖱️ 휴대폰·태블릿·PC 모두 연결 가능(noVNC 웹 클라이언트)
- ⏱️ 1회 최대 약 6시간 실행, 언제든 취소 가능

## 🚀 사용 방법(포크 후 바로 사용)

### 1단계: 이 프로젝트 포크하기

이 페이지 오른쪽 위의 **Fork** 버튼을 클릭해 프로젝트를 본인 GitHub 계정으로 복사합니다. 포크가 끝나면 `사용자이름/cloud-browser` 저장소로 이동합니다.

> 💡 왜 포크하나요? GitHub Actions는 본인 계정의 저장소에서만 실행할 수 있어, 포크해야 실행 권한이 생깁니다.

### 2단계: 클라우드 브라우저 시작하기

1. 포크한 저장소 페이지에서 상단의 **Actions** 탭 클릭
2. 왼쪽에서 **Free Cloud Browser**를 찾아 클릭
3. 오른쪽의 **Run workflow** 버튼을 클릭하면 입력란 2개가 나타납니다:

| 매개변수 | 설명 |
|----------|------|
| VNC 비밀번호 | 데스크톱 연결 시 입력할 비밀번호. 최대 8자까지 유효, 영문+숫자로 설정(예: `abc12345`)하고 **꼭 메모**해 두세요. 일회용 비밀번호이니 평소 쓰는 비밀번호는 쓰지 마세요 |
| 실행 시간 | 이번 클라우드 데스크톱을 유지할 분 수. 기본 300(5시간), 최대 350 |

4. 초록색 **Run workflow**를 눌러 확정하면 클라우드 브라우저가 시작됩니다

### 3단계: 접속 주소 가져오기

1. Actions 페이지에서 방금 실행한 항목(맨 위, 노란 점이 실행 중)을 클릭
2. 가상 머신이 소프트웨어를 설치하고 터널을 만들 때까지 약 2~4분 대기
3. 빌드 단계를 클릭해 로그를 펼치고, 아래로 스크롤해 이런 형태의 주소를 찾으세요:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. 이 주소를 복사해 브라우저에서 열기(휴대폰 기본 브라우저로 충분)

### 4단계: 연결해서 사용하기

1. 열린 noVNC 페이지에서 **Connect** 클릭
2. 2단계에서 설정한 VNC 비밀번호 입력
3. Ubuntu 데스크톱과 Chrome이 보이면 바로 사용 🎉

> ⌨️ 입력기: 기본은 중국어 병음. **Ctrl+Space**로 중/영 전환, 또는 데스크톱에서 오른쪽 클릭 후 "입력기 전환 中/英" 선택.
> 📋 중국어 붙여넣기: 휴대폰에서 중국어를 복사한 뒤 원격 데스크톱에 바로 붙여넣으세요.

### 5단계: 다 쓰면 끄기

- Actions 페이지로 돌아가 해당 실행을 열고, 오른쪽 위 **Cancel run**으로 취소하면 가상 머신이 삭제되고 터널이 무효화됩니다
- 설정한 실행 시간이 지나면 자동으로 종료되니 계속 돌아갈 걱정은 없습니다

## ⚠️ 주의사항

- **주소는 매번 바뀝니다**: 이전 실행이 끝나면 옛 주소는 무효가 되니, 반드시 최신 실행 로그의 주소를 사용하세요
- **데이터는 저장되지 않습니다**: 가상 머신 삭제 후 브라우저 북마크·다운로드 파일·로그인 상태가 모두 지워지니, 중요한 파일은 미리 꺼내 두세요
- **비밀번호 규칙**: 영문과 숫자만, 8자 이내. 일회용 임시 비밀번호이니 평소 쓰는 비밀번호는 쓰지 마세요
- **Re-run을 누르지 마세요**: 새로 열 때는 **Run workflow**를 누르세요. Re-run은 이전 코드로 실행됩니다
- **연결이 느리거나 끊김**: 터널이 Cloudflare를 경유하므로 중국 내 접속 속도는 네트워크 상황에 달렸습니다. 쓸 만한 수준입니다

## 🛠️ 직접 바꿔 보고 싶다면?

워크플로 파일은 `.github/workflows/cloud-browser.yml`에 있습니다. GitHub 웹에서 바로 열어 편집할 수 있고, 커밋하면 즉시 반영됩니다.
