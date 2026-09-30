# 페이지 업데이트 방법

`index.html` 을 새 버전으로 바꾸면 1~2분 뒤 https://qeandas.github.io/yearend-tax-2026/ 에 반영됩니다.
아래 셋 중 편한 방법 하나를 쓰면 됩니다.

| 상황 | 방법 |
|---|---|
| 리눅스 VM 에서 작업 중 | [A. PC — 터미널](#a-pc--터미널-리눅스-vm) |
| 아무 PC 의 웹 브라우저 | [B. PC — 웹 브라우저](#b-pc--웹-브라우저) |
| 핸드폰 | [C. 핸드폰 — 웹 브라우저](#c-핸드폰--웹-브라우저) |

> **올리기 전 확인** — 파일 이름은 정확히 `index.html` 이어야 합니다.
> 백업 파일(`index.html_20260930` 등)이나 비밀번호·개인정보가 든 파일은 올리지 않습니다.
> 저장소가 공개라서 올린 것은 누구나 볼 수 있습니다.

---

## A. PC — 터미널 (리눅스 VM)

저장소 위치는 `/CLAUDE/yearend-tax-2026` 입니다.

**1. 저장소 폴더로 이동**

```bash
cd /CLAUDE/yearend-tax-2026
```

**2. GitHub 의 최신 상태를 먼저 받기**

웹이나 핸드폰으로 올린 적이 있으면 로컬이 뒤처져 있으므로, 항상 먼저 받습니다.

```bash
git pull
```

**3. 새 파일을 저장소에 덮어쓰기**

```bash
cp /home/qeandas/20260930/index.html /CLAUDE/yearend-tax-2026/index.html
```

**4. 무엇이 바뀌었는지 확인**

`modified: index.html` 이 보이면 정상입니다.

```bash
git status
```

**5. 바뀐 파일을 커밋 대상으로 올리기**

```bash
git add index.html
```

**6. 커밋하기 (따옴표 안은 변경 내용 요약)**

로컬에 "이 시점의 파일"을 기록합니다. 아직 GitHub 에는 안 올라갑니다.

```bash
git commit -m "feat: 주의 사항 문구 수정"
```

**7. GitHub 로 올리기**

이 순간 GitHub 에 반영되고, 페이지 재배포가 시작됩니다.

```bash
git push
```

---

## B. PC — 웹 브라우저

git 설치 없이 Windows 등 아무 PC 에서 할 수 있습니다.

1. https://github.com/qeandas/yearend-tax-2026 접속 (로그인 필요)
2. 오른쪽 위 **Add file** → **Upload files**
3. 새 `index.html` 을 끌어다 놓기 — 같은 이름이면 기존 파일을 **덮어씁니다**
4. 아래 **Commit changes** 칸에 변경 요약 입력 (예: `feat: 주의 사항 문구 수정`)
5. **Commit directly to the `main` branch** 가 선택된 상태로 **Commit changes** 클릭

**간단한 글자 수정만 할 때:** 저장소에서 `index.html` 클릭 → 오른쪽 위 연필 아이콘(Edit) → 수정 → **Commit changes...**

> 웹으로 올린 뒤 나중에 터미널(A)로 작업한다면, 꼭 `git pull` 부터 하세요.
> 안 하면 `git push` 가 거절됩니다(GitHub 쪽이 더 최신이라서).

---

## C. 핸드폰 — 웹 브라우저

GitHub 앱은 파일 업로드를 지원하지 않으므로 **Chrome/Safari 같은 웹 브라우저**를 씁니다.

1. 새 `index.html` 을 핸드폰에 저장해 둡니다 (카카오톡 나에게 보내기, 구글 드라이브, 메일 첨부 등에서 "다운로드")
2. 브라우저에서 https://github.com/qeandas/yearend-tax-2026 접속 (로그인 필요)
3. **Add file** → **Upload files**
   - 버튼이 안 보이면 브라우저 메뉴에서 **데스크톱 사이트** 를 켭니다
4. **choose your files** 를 눌러 저장해 둔 `index.html` 선택
5. 변경 요약 입력 → **Commit changes**

**간단한 글자 수정만 할 때:** `index.html` 클릭 → 연필 아이콘 → 수정 → **Commit changes**.
파일이 길어서 핸드폰으로는 오타 수정 정도만 권합니다.

> 핸드폰에서 GitHub 에 로그인해 두면 그 폰으로 공개 페이지를 바꿀 수 있습니다.
> GitHub 계정에 **2단계 인증(2FA)** 을 켜 두세요.

---

## 반영 확인

1. 저장소의 **Actions** 탭 → `pages build and deployment` 가 초록 체크가 되면 배포 완료 (보통 1~2분)
2. https://qeandas.github.io/yearend-tax-2026/ 열기
3. 옛날 화면이 보이면 브라우저 캐시 때문입니다
   - PC: `Ctrl + F5` (강력 새로고침)
   - 핸드폰: 시크릿 탭으로 열거나 잠시 뒤 다시 열기

## 잘못 올렸을 때

- **웹:** 저장소 → `index.html` → **History** 에서 이전 버전을 열어 **Raw** 로 내용 복사 → 다시 올리기
- **터미널:** 직전 커밋을 취소하는 새 커밋을 만들어 올립니다 (이력은 지우지 않으므로 안전)

  ```bash
  cd /CLAUDE/yearend-tax-2026 && git pull && git revert --no-edit HEAD && git push
  ```
