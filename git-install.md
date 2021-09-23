Git 설치 및 초기 세팅법
================

실무에서 바로 사용을 위한 간단 요약
--------------------------------------

##### 예시 코드는 (예시)라고 달아두었습니다. 해당부분은 설정하신 환경에 맞게 변경해주세요.

# 1. Git 설치
> 1. http://git-scm.com/downloads
> 2. 접속 후 해당 OS에 맞는 버전 설치
> 3. 참고 URL : https://goddaehee.tistory.com/216

# 2. Git 초기세팅
> 1. Git Bash 실행 (Git용 콘솔)
> 2. Git 버전 확인 (정상설치 확인위함)
>    git --version
> 4. Git 사용자 등록 (해당 등록을 통해 입력한 내용이 로그에 남습니다. init 후 설정해도 무관합니다.)
>    git config --global user.name "이름"  (예시)
>    git config --global user.email "이메일" (예시)
> 3. 로컬환경에 폴더생성 (C:\GitFolder)
>    mkdir 이용 또는 탐색기에서 생성
> 4. 해당 경로로 이동
>    cd /C/GitFolder (예시)
> 5. 초기화
>    git init
> 6. Git 현재 상태 확인
>    git status