# 프로젝트 연결 및 Git 동기화 방법 가이드

이 문서는 프로젝트의 Git 원격 저장소 연결 상태를 확인하고, 코드 동기화(Push & Pull) 및 새 프로젝트 연결 방법을 안내하기 위해 작성되었습니다.

---

## 1. 기존 프로젝트 동기화 방법 (현재 todolist 프로젝트)

로컬 작업 내용과 원격 저장소(GitHub)를 동기화하는 기본 흐름입니다.

### ① 원격 저장소의 최신 변경 사항 가져오기 (Pull)
공동 작업자나 다른 기기에서 올린 최신 코드를 로컬로 가져옵니다.
```powershell
git pull origin main
```

### ② 내가 수정한 내용을 원격 저장소에 올리기 (Push)
1. **변경 사항 확인**: 어떤 파일이 수정되었는지 확인합니다.
   ```powershell
   git status
   ```
 2. **스테이징**: 저장할 파일들을 선택합니다. (전체 선택 시 `.` 사용)
   ```powershell
   git add .
   ```
 3. **커밋 생성**: 변경 내용에 대한 설명(메시지)을 기록합니다.
   ```powershell
   git commit -m "작업 내용 설명 작성"
   ```
 4. **원격 저장소 업로드**: GitHub에 코드를 전송하여 동기화합니다.
   ```powershell
   git push origin main
   ```

---

## 2. 새로운 프로젝트를 GitHub에 연결하는 방법

새로운 로컬 프로젝트를 만들어 GitHub 원격 저장소와 처음 연결할 때 사용하는 방법입니다.

### 방법 A. 로컬 프로젝트를 먼저 만든 후 GitHub에 연결할 때
1. **Git 저장소 초기화**: 프로젝트 폴더에서 Git을 시작합니다.
   ```powershell
   git init
   ```
 2. **파일 추가 및 커밋**:
   ```powershell
   git add .
   git commit -m "First commit"
   ```
 3. **기본 브랜치명을 `main`으로 설정**:
   ```powershell
   git branch -M main
   ```
 4. **GitHub 원격 저장소 주소 등록**:
   ```powershell
   git remote add origin <GitHub 저장소 URL>
   ```
 5. **첫 Push (원격 브랜치 연결)**:
   ```powershell
   git push -u origin main
   ```

### 방법 B. GitHub 저장소를 먼저 만들고 가져올 때 (Clone)
GitHub에서 생성한 빈 저장소를 로컬로 복제해 오면 자동으로 원격 연결(`origin`)이 설정됩니다.
```powershell
git clone <GitHub 저장소 URL>
```

---

> [!WARNING]
> **OneDrive 사용 시 주의사항**
> 현재 프로젝트가 **OneDrive 동기화 폴더** 내에 위치해 있습니다. OneDrive의 실시간 동기화와 Git의 파일 제어가 충돌할 경우, `.git` 폴더가 손상되거나 파일이 잠기는 오류가 발생할 수 있습니다. 
> 
> 안정적인 개발 환경을 위해 프로젝트 폴더는 OneDrive 동기화 범위 밖(예: `C:\Users\USER\projects` 등)에 두고, 코드 백업 및 버전 관리는 **Git과 GitHub**를 통해서만 동기화하시는 것을 권장합니다.
