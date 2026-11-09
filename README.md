📋 [보고서] 퀴즈 게임 개발 및 실행 환경 구축 결과
1. 개발 및 실행 환경 (Environment)

OS: Windows

Docker version: 29.9.2-2

Git: 2.56.0.windows.4

Python:2026.10

IDE: Visual Studio Code

2. 환경 설정 검증 (Verification)

<img width="3840" height="2160" alt="스크린샷(3)" src="https://github.com/user-attachments/assets/1c5c17ba-4dc7-49a9-83d9-236c2c8552c0" />

3. 트러블슈팅 (Troubleshooting)
🔴 Case 1: 터미널에서 파이썬 명령어 인식 불가 오류

증상 (Issue):
VS Code 터미널에서 python main.py 실행 시, " 'python' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다 " 라는 오류 발생.
원인 (Cause):
윈도우 환경 변수(PATH)에 파이썬 실행 경로가 등록되지 않아, 시스템이 python 명령어를 찾지 못함.
해결 (Solution):
파이썬 설치 파일을 다시 실행하여, 하단의 Add python.exe to PATH 옵션을 체크한 뒤 설치를 진행함. 이후 VS Code를 완전히 재시작하여 변경된 환경 변수를 적용함.
🔴 Case 2: "No installed Python found!" 오류

증상 (Issue):
명령어 실행 시 설치된 파이썬을 찾을 수 없다는 메시지 출력.
원인 (Cause):
로컬 PC에 파이썬이 정상적으로 설치되어 있지 않거나, 기존 설치 경로가 꼬여서 시스템이 파이썬을 전혀 인식하지 못하는 상태.
해결 (Solution):
파이썬 공식 홈페이지(python.org)에 접속하여 윈도우용 최신 설치 파일을 다운로드하고, 처음부터 깔끔하게 재설치(PATH 추가 포함)를 진행하여 문제를 해결함.
