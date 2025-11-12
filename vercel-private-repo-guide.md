# Vercel 비공개 레포지토리 배포 가이드

## 개요
GitHub 레포지토리를 비공개로 전환해도 Vercel에서 자동 배포는 정상적으로 작동합니다. 다만 몇 가지 확인사항이 있습니다.

---

## ✅ 비공개 레포지토리 지원

Vercel은 **비공개(Private) 레포지토리**를 완전히 지원합니다. GitHub, GitLab, Bitbucket의 비공개 레포지토리 모두 사용 가능합니다.

---

## 🔍 확인해야 할 사항

### 1. GitHub OAuth 권한 설정

Vercel이 비공개 레포지토리에 접근하려면 적절한 권한이 필요합니다.

**확인 방법:**
1. Vercel 대시보드 → Settings → Git
2. GitHub 연결 상태 확인
3. 필요시 "Reconnect" 또는 권한 재설정

**필요한 권한:**
- ✅ Repository access (레포지토리 접근)
- ✅ Repository metadata (레포지토리 메타데이터)
- ✅ Contents (코드 내용 읽기)
- ✅ Pull requests (PR 정보)
- ✅ Workflow (GitHub Actions - 선택사항)

### 2. 기존 프로젝트 상태 확인

**이미 배포 중인 프로젝트:**
- 레포지토리를 비공개로 전환해도 **기존 배포는 자동으로 계속 작동**합니다
- Vercel은 이미 연결된 레포지토리에 대한 권한을 가지고 있기 때문입니다

**새로 연결하는 경우:**
- 레포지토리를 비공개로 만든 후 Vercel에 연결하려면
- Vercel이 해당 레포지토리에 접근할 수 있는 권한이 있는지 확인 필요

---

## 🚨 주의사항

### 1. 권한 문제 발생 시

만약 배포가 실패하거나 레포지토리를 찾을 수 없다는 오류가 발생하면:

**해결 방법:**
```
1. Vercel 대시보드 → Settings → Git
2. GitHub 연결 해제 후 재연결
3. 권한 요청 시 "모든 레포지토리" 또는 해당 레포지토리 선택
4. 프로젝트 재연결
```

### 2. 팀/조직 레포지토리

**조직(Organization)의 비공개 레포지토리:**
- Vercel 팀 계정이 해당 조직의 멤버여야 합니다
- 또는 조직 관리자가 Vercel 앱에 접근 권한을 부여해야 합니다

**확인 방법:**
- GitHub 조직 설정 → Third-party access → Vercel 권한 확인

### 3. 빌드 로그 접근

비공개 레포지토리의 경우:
- ✅ Vercel 대시보드에서 빌드 로그는 정상적으로 확인 가능
- ✅ 배포 상태도 정상적으로 표시됨
- ✅ 환경 변수 설정도 동일하게 작동

---

## 📋 체크리스트

레포지토리를 비공개로 전환하기 전/후 확인사항:

- [ ] Vercel과 GitHub 연결 상태 확인
- [ ] Vercel이 레포지토리에 접근할 수 있는 권한 확인
- [ ] 기존 배포가 정상 작동하는지 확인
- [ ] 자동 배포 설정이 활성화되어 있는지 확인
- [ ] 환경 변수가 올바르게 설정되어 있는지 확인
- [ ] (조직 레포지토리인 경우) 조직 권한 확인

---

## 🔄 레포지토리 전환 후 확인

### 1. 즉시 확인
```bash
# 레포지토리를 비공개로 전환한 직후
- Vercel 대시보드에서 프로젝트 상태 확인
- 최근 배포 기록 확인
```

### 2. 테스트 배포
```bash
# 작은 변경사항을 커밋하여 자동 배포 테스트
git commit --allow-empty -m "test: verify deployment"
git push
```

### 3. 배포 로그 확인
- Vercel 대시보드 → Deployments → 최신 배포 클릭
- 빌드 로그가 정상적으로 표시되는지 확인

---

## 💡 추가 정보

### Vercel의 레포지토리 접근 방식

1. **OAuth 토큰 사용**: GitHub OAuth를 통해 레포지토리에 접근
2. **Deploy Key (선택사항)**: 일부 경우 Deploy Key 사용 가능
3. **Webhook**: GitHub에서 푸시 이벤트를 Vercel로 전송

### 비공개 레포지토리의 장점

- ✅ 코드 보안 강화
- ✅ 내부 프로젝트 관리 용이
- ✅ Vercel 기능은 공개/비공개 모두 동일하게 작동

---

## ❓ 문제 해결

### 문제: 배포가 실패하거나 레포지토리를 찾을 수 없음

**해결책:**
1. Vercel Settings → Git → GitHub 재연결
2. 권한 요청 시 해당 레포지토리 또는 "All repositories" 선택
3. 프로젝트 Settings → Git → Repository 재연결

### 문제: 빌드는 성공하지만 자동 배포가 안 됨

**해결책:**
1. Vercel 프로젝트 Settings → Git 확인
2. "Production Branch" 설정 확인
3. GitHub Webhook 설정 확인 (일반적으로 자동 설정됨)

### 문제: 조직 레포지토리 접근 불가

**해결책:**
1. GitHub 조직 설정 확인
2. Vercel 팀이 조직의 멤버인지 확인
3. 조직 관리자에게 Vercel 앱 권한 요청

---

## 📞 지원

문제가 계속되면:
- Vercel 공식 문서: https://vercel.com/docs
- Vercel 지원팀: support@vercel.com
- GitHub 통합 가이드: https://vercel.com/docs/concepts/git

---

## 결론

✅ **비공개 레포지토리로 전환해도 Vercel 배포는 정상 작동합니다.**

다만, Vercel이 레포지토리에 접근할 수 있는 권한이 있는지 확인하는 것이 중요합니다. 대부분의 경우 기존 연결이 있다면 문제없이 작동하지만, 문제가 발생하면 위의 해결책을 참고하세요.
