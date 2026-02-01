# Z.AI GLM Coding Plan Integration Guide

이 가이드는 개발 환경에 Claude Code와 Z.AI GLM Coding Plan을 통합하여 효율적으로 사용할 수 있도록 설정하는 방법을 안내합니다.

## 🎯 목적

개발자들이 Claude Code 또는 Cursor, Cline 등 다양한 코딩 도구를 사용할 때, Z.AI의 GLM 모델을 API를 통해 쉽게 이용할 수 있습니다. 이 가이드는 Z.AI 플랫폼과 API 설정을 통합하여 Claude Code 환경에 Z.AI 모델을 매핑하는 방법을 단계별로 설명합니다.

## 📋 사전 요구 사항

시작하기 전에 필요한 사항들입니다.

### 1. Z.AI 계정 및 API 키
- **Z.AI 오픈플랫폼 계정**: [https://z.ai/](https://z.ai/)에 접속하여 회원가입을 진행하세요.
- **API 키 생성**: [Z.AI Open Platform](https://z.ai/model-api) 접속 후 **[API Keys 관리](https://z.ai/manage-apikey/apikey-list)** 페이지로 이동하여 새로운 API 키를 생성하세요.
- **API 키 복사**: 생성된 API 키를 복사하여 나중에 사용할 수 있도록 안전하게 보관하세요. 키를 절대로 저장소에 노출하거나 공개 저장소에 커밋하지 마세요.

### 2. 개발 도구 환경
- **Node.js**: 버전 18 이상이 설치되어 있어야 합니다.
- **macOS**: 권한 문제 방지를 위해 [nvm](https://nodejs.org/en/download/) 사용하여 Node.js를 설치하는 것을 권장합니다. 직접 설치 시 권한 오류가 발생할 수 있습니다.
- **Windows**: [Git for Windows](https://git-scm.com/download/win)가 설치되어 있어야 합니다.

## 📦 설치 방법

### 1. 자동화 스크립트 (Coding Tool Helper) 사용

가장 간편하고 확실성 있는 방법입니다. `Coding Tool Helper`는 대화형 인터페이스를 제공하여 다양한 코딩 도구의 설정을 도와줍니다.

```bash
# Coding Tool Helper 실행
npx @z_ai/coding-helper
```

실행 후 화면 안내에 따라 다음을 수행합니다:
1. **도구 설치**: Claude Code, Cursor 등 원하는 도구 선택
2. **API 자격 증명**: Z.AI API 키 입력
3. **MCP 서버 구성**: Vision, Search, Reader 서버 추가
4. **모델 선호도**: GLM-4.7 또는 사용자 정의 모델 선택

### 2. 자동화 스크립트 (shell script) 사용

macOS 및 Linux 환경을 위한 자동 설정 스크립트를 사용할 수 있습니다.

```bash
# 설치 스크립트 다운로드 및 실행
curl -O https://cdn.bigmodel.cn/install/claude_code_zai_env.sh && bash ./claude_code_zai_env.sh
```

이 스크립트는 다음을 수행합니다:
- `~/.claude/settings.json` 파일을 생성하거나 수정합니다.
- 환경 변수(`ANTHROPIC_AUTH_TOKEN`, `ANTHROPIC_BASE_URL`, `API_TIMEOUT_MS`)를 설정합니다.
- 기본 모델 매핑을 구성합니다 (GLM-4.7).

**주의사항:**
- 이 스크립트는 Claude Code의 환경 설정 파일(`~/.claude/settings.json`)을 자동으로 관리합니다.
- 수동으로 설정 파일을 직접 수정할 필요가 없습니다.
- 새 터미널 창에서 설정을 적용하려면 Claude Code를 다시 시작해야 합니다.

## ⚙️ 수동 설정 방법

자동화된 설정을 수동으로 변경하고 싶거나, 자동화 스크립트를 사용하지 않으려는 경우 다음 방법을 사용하세요.

### 1. 설정 파일 직접 편집

Claude Code의 설정 파일은 `~/.claude/settings.json`에 위치합니다. 이 파일을 텍스트 에디터로 직접 열어서 수정할 수 있습니다.

```bash
# macOS / Linux
vi ~/.claude/settings.json

# Windows (CMD 또는 PowerShell)
notepad ~/.claude/settings.json
# Windows (PowerShell - 추천)
code $env:USERPROFILE\Documents\claude.json
notepad $env:USERPROFILE\Documents\claude.json
```

### 2. 환경 변수 설정 (선택 사항)

자동화 스크립트를 사용하지 않을 경우, 터미널에서 환경 변수를 설정해야 할 수도 있습니다. 그러나 대부분의 코딩 도구는 터미널 환경 변수를 직접 읽지 못하고, 시스템 레벨 레지스템 환경 변수만 읽을 수 있습니다.

따라서 자동화 도구나 Z.AI API 통합을 사용하는 것이 가장 권장되는 방법입니다.

### 3. Windows 사용자를 위한 가이드

Windows 환경에서는 PowerShell 사용을 권장합니다.

```powershell
# PowerShell에서 환경 변수 설정
# API 키 입력 (변수로 저장)
Read-Host -Prompt "Z.AI API 키를 입력하세요:" -AsSecureString
$env:USERPROFILE_API_KEY = Read-Host -AsSecureString
$env:USERPROFILE_API_KEY

# 설정 파일 업데이트
# settings.json의 env 섹션에 추가
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_AUTH_TOKEN', $env:USERPROFILE_API_KEY, 'User')
```

**팁키:**
- 환경 변수는 현재 PowerShell 세션에만 적용됩니다.
- 새 터미널 창을 열면 환경 변수가 초기화됩니다.
- 지속적인 설정을 위해서는 설정 파일(`~/.claude/settings.json`)을 사용하는 것이 좋습니다.
- 자동화 스크립트(Coding Tool Helper) 사용 시 자동으로 설정 파일을 관리해줍니다.

## ✅ 설치 확인

### 1. 상태 확인

설치가 올바르게 되었는지 확인합니다.

```bash
# Claude Code 버전 확인
claude --version

# 설정 파일 확인
cat ~/.claude/settings.json
```

### 2. 모델 매핑 확인

Claude Code에서 현재 사용 중인 모델을 확인할 수 있습니다.

```bash
# Claude Code 상태 확인
claude

# 모델 매핑 상태 확인 (/status 명령어)
/status
```

`/status` 명령어는 현재 Claude Code의 설정 상태와 사용 중인 모델을 보여줍니다. 여기서 기본 모델(GLM-4.7)이 자동으로 매핑되어 있는지, 사용자가 별도로 설정한 모델이 있다면 그 모델이 표시됩니다.

## 🔄 모델 매핑 이해하기

Claude Code와 Z.AI 통합은 기본적으로 다음 모델 매핑을 사용합니다.

| Claude Code 모델 | Z.AI API 모델 | 용도 |
|-------------------|------------------|------|
| Sonnet (기본) | GLM-4.7 | 일반 코딩 |
| Opus (고성능) | GLM-4.7 | 복잡한 작업 |
| Haiku (빠름) | GLM-4.5-Air | 빠른 응답 |

**매핑 원리:**
- Claude Code는 `ANTHROPIC_DEFAULT_SONNET_MODEL` 환경 변수를 보고, Sonnet 유형의 요청을 Z.AI의 GLM-4.7 모델로 전달합니다.
- `ANTHROPIC_DEFAULT_OPUS_MODEL` 환경 변수를 보고, Opus 유형의 요청을 GLM-4.7 모델로 전달합니다.
- `ANTHROPIC_DEFAULT_HAIKU_MODEL` 환경 변수를 보고, Haiku 유형의 요청을 Z.AI의 GLM-4.5-Air 모델로 전달합니다.

사용자는 `settings.json` 파일에서 이 환경 변수들을 변경하여 원하는 모델을 선택할 수 있습니다. 예를 들어 빠른 응답이 필요할 때 `ANTHROPIC_DEFAULT_HAIKU_MODEL`을 `glm-4.5-air`로 설정하면, Haiku 모델이 사용됩니다.

## 🔧 문제 해결

### 설치 중 오류

**1. 권한 오류 (macOS)**
- **증상**: `npm install -g @anthropic-ai/claude-code` 명령어 실행 시 `EACCES: permission denied` 오류 발생
- **해결책**: [nvm](https://nodejs.org/en/download/) 사용하여 Node.js를 설치하세요. `sudo` 권한 없이 설치를 시도해 보세요.

**2. 설정이 적용되지 않음**
- **증상**: `settings.json`을 수정했는데 Claude Code에서 변경사항이 반영되지 않음
- **원인**: 환경 변수가 캐시되거나, Claude Code가 설정 파일을 다시 읽지 못했을 수 있습니다.
- **해결책**:
  1. 새 터미널 창을 열어서 Claude Code를 완전히 종료하세요.
  2. 터미널 창에서 `source ~/.zshrc` 또는 `source ~/.bash_profile` 명령어를 실행하여 환경 변수를 다시 로드한 후 Claude Code를 다시 시작하세요.
  3. `settings.json` 파일이 올바른 형식인지 확인하세요 (쉼표표, 중괄호 등 JSON 문법 오류가 없는지 확인).

**3. 모델이 인식되지 않음**
- **증상**: Claude Code에서 `/status`를 입력해도 알 수 없는 모델명이 표시됩니다.
- **원인**: 사용자가 `settings.json`에서 모델 매핑 환경 변수를 설정하지 않았거나, 혹은 잘못된 설정값 때문에 모델 인식에 실패했을 수 있습니다.
- **해결책**:
  1. `settings.json` 파일에 올바른 모델 매핑 예시를 추가하세요 (아래 **모델 매핑 이해하기** 섹션 참고).
  2. 또는 `/status` 명령어 대신 `claude` 명령어를 입력하여 환경설정 메뉴를 확인하고 사용 중인 모델을 선택하세요.

### 인증 오류

**증상**: Claude Code 실행 시 "API key 오류" 또는 "Unauthorized" 메시지가 표시됨
- **원인**: API 키가 올바르지 않거나, 유효기가 만료되었을 수 있습니다.
- **해결책**:
  1. [Z.AI Open Platform](https://z.ai/model-api)에 접속하여 API 키의 유효기와 만료일을 확인하세요.
  2. 올바른 API 키로 `settings.json` 파일을 업데이트하세요.
  3. 터미널 창을 닫고 다시 열어서 설정을 적용하세요.

### MCP 서버 연결 실패

**증상**: MCP 서버 목록에 서버가 보이지만 연결이 안 됩니다.
- **원인**: Claude Code에서 MCP 서버를 사용하려고 할 때, MCP 서버가 설치되어 있지 않거나 제대로 구성되지 않았을 수 있습니다.
- **해결책**:
  1. 각 MCP 서버(Vision, Search, Reader, Zread)를 개별로 설치한 후 `~/.claude/claude_mcp_servers.json` 파일에 수동으로 등록하세요.
  2. [Coding Tool Helper](https://docs.z.ai/devpack/extension/coding-tool-helper)를 사용하여 MCP 서버 설치 및 설정을 자동화하세요.

## 📚 추가 리소스

- **[Z.AI 문서](https://docs.z.ai/)**: 공식 문서와 API 레퍼런스를 확인하세요.
- **[GLM Coding Plan 페이지](https://z.ai/subscribe)**: 요금제과 혜택을 확인하세요.
- **[Coding Tool Helper 문서](https://docs.z.ai/devpack/extension/coding-tool-helper)**: 자동화 도구의 기능과 사용법에 대해 더 자세히 알아보세요.
- **[MCP 서버 문서](https://docs.z.ai/devpack/mcp/)**: Vision, Search, Reader, Zread MCP 서버의 설치 및 사용법이 안내되어 있습니다.

## 🎯 요약

이 가이드를 따르면 개발 환경에서 Claude Code와 Z.AI GLM Coding Plan을 통합하여 효율적으로 설정하고 사용할 수 있습니다. 주요 내용은 다음과 같습니다.

1. **준비**: Z.AI 계정 생성, Node.js 및 Git 설치
2. **설치**: Coding Tool Helper 또는 자동화 스크립트를 사용하여 환경 설정
3. **구성**: `~/.claude/settings.json` 파일을 편집하여 모델 매핑 및 기타 설정을 수행
4. **검증**: `claude --version` 및 `/status` 명령어로 설치와 설정 상태를 확인

Z.AI의 GLM 모델을 사용하면 Claude Code의 기본 성능을 유지하면서 API 사용량을 늘리고 비용을 절감할 수 있습니다. 자동화 도구를 활용하면 복잡한 설정 과정도 간소화되어 개발 생산성이 향상됩니다.

특히 **Coding Tool Helper**를 사용하는 것을 강력 추천합니다. 이 도구는 GUI 환경에서 Claude Code, Cursor, Cline 등 여러 코딩 도구의 설정을 통합해서 관리해줍니다. CLI 명령어보다 직관적이고 시각적인 피드백을 제공하여 초보 사용자도 쉽게 설정을 완료할 수 있습니다.