# MCP Servers Documentation

이 문서는 Claude Code와 Z.AI 통합을 위해 사용할 수 있는 MCP(Model Context Protocol) 서버들에 대한 안내입니다.

## 📦 MCP 서버 목록

### 1. Vision MCP Server
- **용도**: 이미지 및 비디오 분석 기능 제공
- **문서**: [/devpack/mcp/vision-mcp-server](../mcp/vision-mcp-server)
- **사용**: Claude Code에서 이미지를 분석하거나 이미지 기반 작업을 처리할 때 사용합니다.

### 2. Search MCP Server
- **용도**: 웹 검색 기능 제공
- **문서**: [/devpack/mcp/search-mcp-server](../mcp/search-mcp-server)
- **사용**: Claude Code에서 최신 정보를 검색하거나 웹 자료를 찾을 때 사용합니다.

### 3. Reader MCP Server
- **용도**: 웹 페이지 읽기 및 파싱 기능 제공
- **문서**: [/devpack/mcp/reader-mcp-server](../mcp/reader-mcp-server)
- **사용**: Claude Code에서 웹 페이지의 내용을 읽거나 텍스트를 추출할 때 사용합니다.

### 4. Zread MCP Server
- **용도**: 향상된 읽기 기능 제공
- **문서**: [https://docs.z.ai/devpack/mcp/zread-mcp-server](https://docs.z.ai/devpack/mcp/zread-mcp-server)
- **사용**: Reader MCP 서버보다 더 발전된 기능이 필요할 때 사용합니다.

## 📝 설치 및 설정 방법

### 공통 요구사항
MCP 서버를 사용하기 위해 다음 사항이 필요합니다:
- Node.js 환경 (버전 18 이상)
- Claude Code가 설치되어 있어야 함
- Claude Code의 설정 파일(`~/.claude/settings.json`)에 접근 가능

### 자동 설정 (추천)

**Coding Tool Helper**를 사용하면 MCP 서버들을 자동으로 설치하고 설정할 수 있습니다.

```bash
# Coding Tool Helper 실행
npx @z_ai/coding-helper
```

실행 후 화면 안내에 따라 MCP 서버를 선택하고 설정할 수 있습니다.

### 수동 설정

각 MCP 서버의 문서를 참고하여 수동으로 설치하고 설정하세요.

### Claude Code에서 MCP 설정

Claude Code의 MCP 설정은 `~/.claude/claude_mcp_servers.json` 파일에 저장됩니다.

**구조 예시**:
```json
{
  "mcpServers": [
    {
      "command": "npx -y @zai/mcp-vision-server",
      "env": {}
    },
    {
      "command": "npx -y @zai/mcp-search-server",
      "env": {}
    },
    {
      "command": "npx -y @zai/mcp-reader-server",
      "env": {}
    }
  ]
}
```

## 📚 사용 예시

### 이미지 분석
1. Claude Code를 실행합니다.
2. "이미지를 분석해줘" 또는 유사한 명령어를 사용합니다.
3. 이미지 파일을 업로드하거나 분석 요청을 보냅니다.

### 웹 검색
1. Claude Code에 "최신 AI 뉴스는 무엇이야?"라고 묻습니다.
2. 검색 결과를 바탕화면 관련 기사나 기사를 찾을 수 있습니다.

### 웹 페이지 읽기
1. Claude Code에 "이 페이지의 주요 내용을 요약해줘"라고 요청합니다.
2. 텍스트를 추출하거나 요약된 내용을 바탕화면 본문 내용을 파악할 수 있습니다.

## 🔧 문제 해결

### MCP 서버가 설치되지 않음
- **증상**: Coding Tool Helper로 설치를 시도했으나 MCP 서버가 설치되지 않거나 실행되지 않습니다.
- **원인**: npm 패키지 지연, 인터넷 연결 문제, 또는 설치 스크립트 실행 오류
- **해결책**:
  1. 인터넷 연결을 확인합니다.
  2. 터미널을 사용하여 수동으로 MCP 서버를 설치합니다.
  3. 터미널을 사용하지 않고 Coding Tool Helper의 로그를 확인하여 문제를 파악합니다.

### Claude Code에서 MCP 서버를 찾지 못함
- **증상**: `~/.claude/claude_mcp_servers.json` 파일이 없거나 Claude Code에서 MCP 메뉴를 찾을 수 없습니다.
- **원인**: 파일 경로가 올바르지 않거나 Claude Code 버전이 MCP 기능을 지원하지 않을 수 있습니다.
- **해결책**:
  1. Claude Code가 MCP를 지원하는 최신 버전인지 확인합니다 (`claude --version`).
  2. `~/.claude/claude_mcp_servers.json` 파일을 수동으로 생성합니다.
  3. Claude Code의 [MCP 서버 관리] 기능을 사용하여 MCP 서버를 추가합니다.

## 📚 추가 리소스

- **[Z.AI Open Platform](https://z.ai/model-api)**: API 키 관리
- **[MCP 서버 문서](https://docs.z.ai/devpack/mcp/)**: MCP 서버 설치 및 사용 가이드
- **[Coding Tool Helper 문서](https://docs.z.ai/devpack/extension/coding-tool-helper)**: 자동화 도구 문서