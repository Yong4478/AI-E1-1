📄 [기술 보고서] 로컬 개발 및 실행 환경 구축 명세서

1. 시스템 개요 및 환경 명세 (System Environment Specification)
본 환경은 애플리케이션의 안정적인 개발, 버전 관리, 그리고 향후 컨테이너화 기반의 배포를 고려하여 구성된 로컬 호스트(Local Host) 기반의 개발 환경입니다.

Operating System (OS): Windows
로컬 개발 및 테스트를 수행하는 메인 호스트 운영체제.

Containerization: Docker (Version: 29.9.2-2)
애플리케이션의 실행 환경을 격리하고, OS에 구애받지 않는 일관된 배포 환경(Container)을 구축하기 위한 플랫폼.

Version Control System (VCS): Git (Version: 2.56.0.windows.4)
소스 코드의 이력 관리, 브랜치 전략 수행 및 원격 저장소(Repository)와의 동기화를 위한 분산 버전 관리 시스템.

Language Runtime: Python 3.15.3
메인 애플리케이션 구동을 위한 핵심 인터프리터 및 런타임 환경.

Integrated Development Environment (IDE): Visual Studio Code
코드 작성, 터미널 제어, 디버깅 및 Git 연동을 통합적으로 수행하기 위한 개발 도구.

docker --version: 29.9.2
어플리케이션 개발 및 배포를 위한 플랫폼

2. 환경 구축 프로세스 (Setup Process)
런타임 환경 구성: 공식 배포처(python.org)를 통해 Windows 아키텍처에 맞는 Python 바이너리를 설치하고, 전역(Global)에서 접근 가능하도록 시스템 환경 변수를 구성함.
버전 관리 및 컨테이너 도구 연동: Git CLI 및 Docker Engine을 설치하여 로컬 환경에서의 형상 관리 및 컨테이너 빌드 기반을 마련함.
통합 개발 환경(IDE) 세팅: VS Code를 설치하고, 내장 터미널(PowerShell)을 통해 런타임 및 시스템 명령어의 정상 호출 여부를 연동함.

3. 환경 검증 및 테스트 (Verification)
구축된 환경의 무결성을 확인하기 위해 CLI(Command Line Interface) 기반의 버전 검증 및 테스트 스크립트 실행을 진행하였습니다.


설명: VS Code 내장 터미널에서 python --version, git --version, docker --version 명령어를 차례로 호출하여, 각 모듈이 시스템 PATH에 정상적으로 매핑되어 있음을 확인하는 캡처 화면.

<img width="3840" height="2160" alt="스크린샷(4)" src="https://github.com/user-attachments/assets/05996f1a-8a53-405b-a1a8-4e07f63723dd" />

4. 트러블슈팅 및 이슈 해결 (Troubleshooting)
환경 구축 과정에서 발생한 주요 이슈와 이에 대한 원인 분석 및 해결 방안을 아래와 같이 기술합니다.

🔴 Issue 1: CLI 환경 내 런타임 명령어 인식 실패 (CommandNotFoundException)

현상 (Symptom):
VS Code 터미널(PowerShell)에서 애플리케이션 실행을 위해 python 명령어를 호출하였으나, 해당 용어를 cmdlet, 함수, 스크립트 파일 등으로 인식할 수 없다는 ObjectNotFound 예외가 발생함.

원인 분석 (Root Cause):
Windows 운영체제의 시스템 환경 변수(Environment Variables)인 PATH에 Python 실행 파일(python.exe)이 위치한 절대 경로가 등록되지 않아, 쉘(Shell) 환경에서 해당 바이너리를 탐색하지 못함.

해결 방안 (Resolution):
Python 설치 마법사(Installer)를 재실행하여 설정 변경(Modify) 모드로 진입한 후, Add python.exe to PATH 옵션을 명시적으로 활성화함. 이후 VS Code 프로세스를 완전히 종료하고 재시작하여 갱신된 환경 변수를 터미널 세션에 적용함으로써 명령어 호출 문제를 해결함.

🔴 Issue 2: 런타임 바이너리 탐색 불가 ("No installed Python found!")

현상 (Symptom):
명령어 실행 시 시스템 내에 설치된 Python 런타임을 전혀 찾을 수 없다는 치명적(Fatal) 에러 메시지가 출력됨.

원인 분석 (Root Cause):
로컬 호스트 내에 Python 인터프리터가 물리적으로 설치되어 있지 않거나, 이전 설치 과정에서의 레지스트리 꼬임 현상으로 인해 시스템이 런타임의 존재 자체를 식별하지 못하는 상태로 확인됨.

해결 방안 (Resolution):
Python 공식 홈페이지를 통해 최신 버전의 Windows용 설치 패키지(AMD64)를 새로 다운로드함. 기존의 불완전한 환경을 배제하고 클린 설치(Clean Install)를 진행하였으며, 설치 과정에서 시스템 경로 자동 추가 옵션을 필수로 지정하여 런타임 환경을 정상적으로 복구 및 구축함.

해결 (Solution)파이썬 공식 홈페이지(python.org)에 접속하여 윈도우용 최신 설치 파일을 다운로드하고, 처음부터 깔끔하게 재설치(PATH 추가 포함)를 진행하여 문제를 해결함.
