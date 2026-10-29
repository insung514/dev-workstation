# Development Workstation

## 1. 프로젝트 개요

WSL2와 Ubuntu를 기반으로 개발 환경을 구성하고,
Docker를 이용해 웹 서버를 실행하며,
Git과 GitHub를 이용해 프로젝트를 관리하는 실습이다.

## 2. 실행 환경

- OS: Windows + WSL2
- Linux: Ubuntu
- Shell: Bash
- 컨테이너 엔진: Docker Desktop
- 웹 서버: Nginx Alpine
- 버전 확인 명령:
  - `docker --version`
  - `git --version`

## 3. 수행 체크리스트

- [x] 터미널에서 파일과 디렉터리 생성 및 관리
- [x] 파일 및 디렉터리 권한 변경
- [x] Docker 버전 및 엔진 상태 확인
- [x] hello-world 컨테이너 실행
- [x] Ubuntu 컨테이너 내부에서 명령 실행
- [x] Dockerfile 작성 및 커스텀 이미지 빌드
- [x] 포트 매핑을 이용한 웹 서버 실행
- [x] Bind Mount를 이용한 HTML 변경 확인
- [x] Docker Volume 데이터 영속성 확인
- [x] Git 커밋 및 GitHub 푸시
- [ ] 운영 명령 로그 및 증거 자료 정리
- [ ] 필수 항목 검증 및 제출 자료 최종 확인

## 4. 프로젝트 구조

```text
dev-workstation/
├── Dockerfile
├── README.md
├── memo.txt
├── memo-renamed.txt
├── logs/
├── screenshots/
└── site/
    └── index.html
```

## 5. 도구 버전

- Git: 2.53.0
- Docker: 29.9.2

## 6. 파일 권한 확인 결과

| 대상 | 권한 | 의미 |
|---|---|---|
| memo.txt | 644 (-rw-r--r--) | 소유자는 읽기/쓰기, 그 외는 읽기 |
| site | 755 (drwxr-xr-x) | 소유자는 전체 권한, 그 외는 읽기/탐색 |

확인 명령: `stat -c '%A %a %n' memo.txt site`

## 7. 문제 해결 기록

### 사례 1: Docker 명령 실행 권한 문제
- 원인: 현재 사용자가 Docker 그룹에 포함되지 않았을 수 있다.
- 해결: `sudo usermod -aG docker $USER` 실행 후 Ubuntu 터미널을 재시작하고 `groups` 명령으로 확인했다.

### 사례 2: 웹 서버 포트 접근 문제
- 확인: `docker ps`로 컨테이너 상태와 포트 매핑을 확인했다.
- 해결 및 검증: `curl http://localhost:8081`로 웹 페이지 HTML이 반환되는 것을 확인했다.

## 8. 최종 검증 결과

- [x] Docker 이미지 빌드 성공
- [x] Nginx 웹 서버 포트 매핑 확인
- [x] Bind Mount HTML 변경 결과 확인
- [x] Docker Volume 데이터 영속성 확인
- [x] GitHub 저장소에 프로젝트 업로드
