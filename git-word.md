Git 기본 명령어
==========

실무에서 바로 사용을 위한 요약
---------------------------------

##### 예시 코드는 (예시)라고 달아두었습니다. 해당부분은 설정하신 환경에 맞게 변경해주세요.
##### CLI환경 기준으로 작성하였습니다. 
##### 자주 사용하는 명령어만 정리하였습니다.

# Git원리
> ![Alt text](./img/993CCF4B5F17C75211.png)

# 1. 로컬환경 명령어
### 1-1. status
> * Git 저장소의 상태를 알려주는 명령

	git status   #전체
	git status -s   #간략화

### 1-2. init
> * Git 저장소 생성(초기화)    
> 원하는 경로의 원하는 폴더에 자유롭게 저장소 생성가능(C 바로아래에 폴더 생성을 추천합니다.)

	git init

### 1-3. add
> * 스테이지에 추가하는 명령    
> 새로 생성한 파일을 스테이지에 추가하고 싶다면 반드시 실행해야합니다.

	git add 파일명.php #(예시)

### 1-4. commit
> * 로컬저장소에 올리는 명령
<pre>
<code>
git commit    #스테이지에 있는 (add해서 올린) 파일들을 전체 커밋하는 명령어

git commit -a    #add 명령어를 생략하고 바로 워킹트리(일반적으로 작업하는 로컬폴더) -> 스테이지 -> 로컬저장소로 업로드할때 사용

git commit -m "코멘트"   #커밋할때 코멘트를 달아 어떤 작업내용인지 로그를 남깁니다. (규칙에 따라 남기기) (**제일 많이 사용)

</code>
</pre>
# 2. 원격환경 명령어 (사용전 신중히)
### 2-1. remote
> * 원격저장소 연결
<pre>
<code>
git remote add origin https://github.com/JangYuJungCPZ/Git.git    #git remote add [원격저장소이름] [원격저장소주소]

git remote -v   #원격저장소 목록 조회
</code>
</pre>
### 2-2. push
> * 원격저장소에 업로드    
> 현재 브랜치(원격용 작업 공간)에서 새로 생성한 커밋들을 원격저장소에 업로드    
> fatal: The current branch master has no upstream branch. 오류가 날 경우 git push -u [원격저장소이름] [브랜치명] 의 명령어로 업스트림 지정

	git push [원격저장소이름] [브랜치명] # 통상 첫번째 원격저장소이름은 origin으로 등록합니다.(remote 할때)

### 2-3. clone / pull / fetch
> * 원격저장소에서 가져오기 [clone / pull / fetch]

# 3. 중요 명령어