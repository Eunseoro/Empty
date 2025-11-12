# GitHub Codespace 생성 가이드

## 개요
이미 작업 중인 GitHub 레포지토리에서 GitHub Copilot을 사용하기 위해 Codespace를 생성하는 방법을 안내합니다.

---

## 🚀 Codespace 생성 방법

### 방법 1: GitHub 웹 인터페이스에서 생성 (가장 간단)

#### 단계별 가이드

1. **레포지토리 접속**
   - GitHub에서 해당 레포지토리로 이동
   - 레포지토리 페이지 상단의 **"Code"** 버튼 클릭

2. **Codespace 탭 선택**
   - "Code" 드롭다운 메뉴에서 **"Codespaces"** 탭 클릭
   - 또는 직접 URL: `https://github.com/[사용자명]/[레포지토리명]` → 상단 "Code" 버튼

3. **Codespace 생성**
   - **"Create codespace on main"** (또는 현재 브랜치명) 클릭
   - 또는 **"+"** 버튼 클릭

4. **생성 대기**
   - Codespace가 생성되는 동안 대기 (보통 1-2분)
   - 생성 완료 후 자동으로 새 탭에서 VS Code 웹 에디터가 열림

---

### 방법 2: 특정 브랜치에서 생성

1. **브랜치 선택**
   - 레포지토리 페이지에서 원하는 브랜치로 전환
   - "Code" → "Codespaces" → **"Create codespace on [브랜치명]"** 클릭

---

### 방법 3: 고급 설정으로 생성

1. **Codespace 설정**
   - "Code" → "Codespaces" → **"..." (점 3개)** 클릭
   - **"New with options..."** 선택

2. **설정 옵션**
   - **Machine type**: 
     - 2-core (기본, 무료)
     - 4-core (유료)
     - 8-core (유료)
   - **Region**: 가장 가까운 지역 선택
   - **Branch**: 생성할 브랜치 선택

3. **생성**
   - **"Create codespace"** 클릭

---

## 💻 Codespace에서 GitHub Copilot 사용하기

### 1. Copilot 활성화 확인

**Codespace는 기본적으로 GitHub Copilot이 활성화되어 있습니다.**

확인 방법:
- Codespace가 열리면 우측 하단에 Copilot 아이콘 확인
- 또는 설정에서 확인: Settings → Features → GitHub Copilot

### 2. Copilot 사용 방법

#### 자동 완성
- 코드를 입력하면 자동으로 제안이 나타남
- `Tab` 키로 제안 수락
- `Esc` 키로 제안 거부

#### 인라인 제안
- 주석을 작성하면 코드 제안이 나타남
- 예: `// function to calculate fibonacci` 입력 시 함수 코드 제안

#### 챗 기능 (Copilot Chat)
- `Ctrl + L` (Windows/Linux) 또는 `Cmd + L` (Mac)로 챗 열기
- 코드에 대한 질문이나 요청 가능

---

## ⚙️ Codespace 설정 및 커스터마이징

### 1. devcontainer 설정 (선택사항)

레포지토리에 `.devcontainer/devcontainer.json` 파일을 추가하여 환경을 커스터마이징할 수 있습니다.

**예시 파일 생성:**
```json
{
  "image": "mcr.microsoft.com/devcontainers/javascript-node:18",
  "features": {},
  "customizations": {
    "vscode": {
      "extensions": [
        "dbaeumer.vscode-eslint",
        "esbenp.prettier-vscode"
      ]
    }
  },
  "forwardPorts": [3000, 8000],
  "postCreateCommand": "npm install"
}
```

### 2. 환경 변수 설정

- Codespace Settings → Secrets and variables → Codespaces
- 환경 변수 추가 가능

---

## 📋 Codespace 관리

### Codespace 목록 확인

1. **GitHub 웹에서**
   - GitHub 프로필 → **"Codespaces"** 메뉴 클릭
   - 또는 `https://github.com/codespaces` 직접 접속

2. **활성 Codespace 확인**
   - 실행 중인 Codespace 목록 확인
   - 중지, 삭제, 이름 변경 등 관리 가능

### Codespace 중지/삭제

**중지:**
- Codespace 목록에서 **"..."** → **"Stop codespace"**
- 또는 Codespace 내에서: Command Palette (`Ctrl+Shift+P`) → "Codespaces: Stop Current Codespace"

**삭제:**
- Codespace 목록에서 **"..."** → **"Delete"**
- ⚠️ 삭제하면 복구 불가능하므로 주의

---

## 💰 비용 정보

### 무료 사용량
- GitHub Free 계정: 월 60시간 (2-core 머신)
- GitHub Pro 계정: 월 120시간 (2-core 머신)
- GitHub Team/Enterprise: 더 많은 시간 제공

### 유료 옵션
- 4-core 머신: 시간당 $0.18
- 8-core 머신: 시간당 $0.36
- 스토리지: 월 $0.07/GB

**참고:** Codespace를 사용하지 않을 때는 중지하여 비용을 절약하세요.

---

## 🔧 문제 해결

### 문제: Codespace 생성이 실패함

**해결책:**
1. 브라우저 캐시 삭제 후 재시도
2. 다른 브라우저에서 시도
3. GitHub 상태 페이지 확인: https://www.githubstatus.com
4. 레포지토리 권한 확인

### 문제: Copilot이 작동하지 않음

**해결책:**
1. Codespace Settings → Features → GitHub Copilot 활성화 확인
2. GitHub 계정에 Copilot 구독이 있는지 확인
3. Codespace 재시작
4. 브라우저 확장 프로그램이 충돌하는지 확인

### 문제: Codespace가 느림

**해결책:**
1. 더 가까운 Region 선택
2. 더 큰 Machine type 사용 (유료)
3. 불필요한 확장 프로그램 비활성화
4. Codespace 재시작

---

## 🎯 모범 사례

### 1. Codespace 사용 시
- ✅ 작업이 끝나면 Codespace 중지 (비용 절약)
- ✅ 중요한 변경사항은 커밋/푸시
- ✅ 환경 변수는 Secrets에 저장
- ✅ devcontainer.json으로 환경 일관성 유지

### 2. Copilot 활용
- ✅ 명확한 주석 작성으로 더 나은 제안 받기
- ✅ 제안된 코드는 항상 검토 후 사용
- ✅ 보안에 민감한 코드는 직접 작성
- ✅ Copilot Chat으로 코드 설명 요청

---

## 📚 추가 리소스

- **GitHub Codespace 문서**: https://docs.github.com/en/codespaces
- **GitHub Copilot 문서**: https://docs.github.com/en/copilot
- **devcontainer 스펙**: https://containers.dev
- **Codespace 상태 확인**: https://github.com/codespaces

---

## 🎉 빠른 시작 체크리스트

- [ ] GitHub 레포지토리 접속
- [ ] "Code" 버튼 → "Codespaces" 탭 클릭
- [ ] "Create codespace on main" 클릭
- [ ] Codespace 생성 대기 (1-2분)
- [ ] VS Code 웹 에디터에서 작업 시작
- [ ] GitHub Copilot 자동 완성 사용
- [ ] 작업 완료 후 Codespace 중지

---

## 결론

GitHub Codespace는 레포지토리에서 바로 클릭 몇 번으로 생성할 수 있으며, GitHub Copilot이 기본적으로 활성화되어 있어 바로 사용할 수 있습니다. 웹 브라우저만 있으면 어디서든 개발 환경에 접근할 수 있어 매우 편리합니다.
