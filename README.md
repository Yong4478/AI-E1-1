📋 [보고서] 퀴즈 게임 개발 및 실행 환경 구축 결과
1. 개발 및 실행 환경 (Environment)

OS: Windows

Docker version: 29.9.2-2

Git: 2.56.0.windows.4

Python:2026.10

IDE: Visual Studio Code

2. 환경 설정 검증 (Verification)

<img width="3840" height="2160" alt="스크린샷(3)" src="https://github.com/user-attachments/assets/1c5c17ba-4dc7-49a9-83d9-236c2c8552c0" />


트러블슈팅 (Troubleshooting)

1. 인증 및 권한 오류 (Authentication Failed)

문제 상황: 코드를 GitHub에 올리려고(Push) 할 때, "권한이 없습니다(403 Forbidden)" 또는 "로그인 정보가 잘못되었습니다"라는 메시지가 뜨며 전송이 실패하는 경우입니다.

원인: GitHub 계정의 비밀번호가 바뀌었거나, Visual Studio에 저장된 인증 토큰(Token)이 만료되었을 때 발생합니다.

해결 방안:

계정 재연동: Visual Studio 오른쪽 상단의 [계정 아이콘]을 클릭하여 GitHub 계정을 로그아웃했다가 다시 로그인합니다.

자격 증명 관리자 수정:
Windows 검색창에 '자격 증명 관리자' 입력 후 실행.
[Windows 자격 증명] 탭에서 git:https://github.com 항목을 찾아 제거합니다.
Visual Studio에서 다시 Push를 시도하면 새로운 로그인 창이 뜨며 인증을 갱신할 수 있습니다.

2. 병합 충돌 발생 (Merge Conflict)

문제 상황: GitHub 서버에 있는 코드와 내 컴퓨터의 코드가 같은 줄을 서로 다르게 수정했을 때, "충돌로 인해 Pull/Push를 완료할 수 없습니다"라는 메시지가 뜨는 경우입니다.

원인: 협업 중이거나 다른 기기에서 작업한 내용을 반영하지 않은 상태에서 동일한 파일을 수정했을 때 발생합니다.

해결 방안 (Visual Studio 내장 도구 활용):

충돌 파일 확인: [Git 변경 내용] 창에 '충돌' 상태로 표시된 파일을 더블 클릭합니다.

병합 편집기 사용: Visual Studio가 제공하는 '병합 편집기(Merge Editor)' 화면이 열립니다.

코드 선택: 왼쪽(서버 코드)과 오른쪽(내 코드) 중 어떤 것을 반영할지 체크박스로 선택하거나, 하단의 결과 창에서 직접 코드를 수정합니다.

병합 수락: 수정이 완료되면 [병합 수락] 버튼을 누르고 커밋(Commit)하여 충돌을 마무리합니다.

증상 (Issue):

명령어 실행 시 설치된 파이썬을 찾을 수 없다는 메시지 출력.

원인 (Cause):

로컬 PC에 파이썬이 정상적으로 설치되어 있지 않거나, 기존 설치 경로가 꼬여서 시스템이 파이썬을 전혀 인식하지 못하는 상태.

해결 (Solution)파이썬 공식 홈페이지(python.org)에 접속하여 윈도우용 최신 설치 파일을 다운로드하고, 처음부터 깔끔하게 재설치(PATH 추가 포함)를 진행하여 문제를 해결함.
