# Coding Tool Helper Documentation

`Coding Tool Helper`는 개발 환경 설정을 도와주는 대화형 자동화 도구입니다. 이 도구는 Claude Code, Cursor, Cline 등 다양한 코딩 도구의 설정을 통합하여 관리해줍니다.

## 📋 기능

### 1. 자동 설치
- Claude Code, Cursor 등 다양한 코딩 도구의 자동 설치 지원
- Z.AI API 자격 증명 자동 처리
- MCP 서버(Vision, Search, Reader 등)의 일괄 설정 및 설치

### 2. 설정 관리
- `~/.claude/settings.json` 파일의 자동 수정
- 환경 변수 설정 (API 키, 모델 매핑 등)
- MCP 서버 설정 파일(`~/.claude/claude_mcp_servers.json`) 자동 생성

### 3. 대화형 인터페이스
- 사용자 친화한 명령어 프롬프트 제공
- 직관적인 파일 편집 기능 (선택된 도구의 config 파일 바로 열기)
- 설정 상태 실시간 확인

### 4. 다중 도구 지원
- 하나의 도구에서 여러 코딩 툴(예: Claude Code, Cursor)을 동시에 사용할 수 있는 환경 지원

## 🚀 사용법

### 설치 및 실행

```bash
# Coding Tool Helper 실행
npx @z_ai/coding-helper
```

실행 후 화면 안내에 따라 다음 단계를 수행합니다:

1. **도구 선택**: Claude Code, Cursor, Cline 등 사용할 도구를 선택합니다.
2. **API 키 입력**: Z.AI API 키를 입력합니다.
3. **MCP 서버 설정**: Vision, Search, Reader 등 필요한 MCP 서버를 선택하고 설정합니다.
4. **확인**: 설정이 올바르게 적용되었는지 확인합니다.

## 🎯 주요 기능

### 1. 자동 환경 구성
Coding Tool Helper는 시스템 환경(OS, Node.js 버전 등)을 감지하고, 각 도구에 맞는 설치 스크립트를 자동으로 적용합니다.

### 2. 통합 설정 관리
`~/.claude/settings.json` 파일을 중앙하여 모든 도구(Claude Code, Cursor, Cline, MCP 서버 등)의 설정을 한 곳에서 관리할 수 있습니다. 이를 통해 설정의 중복을 방지하고 일관성을 유지할 수 있습니다.

### 3. 직관적인 파일 편집
특정 도구를 선택하면 해당 도구의 설정 파일을 텍스트 에디터나 VS Code에서 바로 열 수 있습니다. 이를 통해 복잡한 설정 작업이 훨씬 쉬워집니다.

## 📚 지원 도구

현재 Coding Tool Helper는 다음 도구들을 지원합니다:

- **Claude Code**: 터미널 기반 AI 코딩 도구
- **Cursor**: AI가 강화된 VS Code 확장
- **Cline**: VS Code AI 파트너
- **Windsurf**: AI 코딩 도구

## 🔧 사용자 정의

### 1. 개발자
- CLI 명령어에 익숙한 사용자
- 복잡한 설정 작업을 간소화하고 싶어하는 사용자

### 2. IT 관리자
- 다중 환경 설정 관리
- 표준화된 설정 프로세스를 유지하고자는 사용자

## 🎯 요약

Coding Tool Helper는 코딩 도구 사용 환경을 설정하는 복잡한 문제를 해결하고, 개발 생산성을 높여줍니다.