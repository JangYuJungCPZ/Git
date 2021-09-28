Git 기본 명령어
==========

실무에서 바로 사용을 위한 요약~
---------------------------------

##### 예시 코드는 (예시)라고 달아두었습니다. 해당부분은 설정하신 환경에 맞게 변경해주세요.
##### CLI환경 기준으로 작성하였습니다. 
##### 자주 사용하는 명령어만 정리하였습니다.

# Git원리
> ![Alt text](./img/993CCF4B5F17C75211.png)

# 0. 한번만 사용하는 명령어 / 자주사용하는 명령어
## 0-1. 한번만
> 1. git init 또는 git clone
> 2. git remote
## 0-2. 자주
> 1. git add
> 2. git commit
> 3. git push
> 4. git log
> 5. git branch
> 6. git checkout
> 7. git merge
> 
# 1. 로컬환경 명령어
## 1-1. status
> * Git 저장소의 상태를 알려주는 명령

	git status   # 전체
	git status -s   # 간략화

## 1-2. init
> * Git 저장소 생성(초기화)    
> 원하는 경로의 원하는 폴더에 자유롭게 저장소 생성가능(C 바로아래에 폴더 생성을 추천합니다.)

	git init

## 1-3. add
> * 스테이지에 추가하는 명령    
> 새로 생성한 파일을 스테이지에 추가하고 싶다면 반드시 실행해야합니다.

	git add 파일명.php # (예시)

## 1-4. commit
> * 로컬저장소에 올리는 명령
<pre>
<code>
git commit    # 스테이지에 있는 (add해서 올린) 파일들을 전체 커밋하는 명령어

git commit -a    # add 명령어를 생략하고 바로 워킹트리(일반적으로 작업하는 로컬폴더) -> 스테이지 -> 로컬저장소로 업로드할때 사용

git commit -m "코멘트"   # 커밋할때 코멘트를 달아 어떤 작업내용인지 로그를 남깁니다. (규칙에 따라 남기기) (**제일 많이 사용)

</code>
</pre>
# 2. 원격환경 명령어 (사용전 신중히)
## 2-1. remote
> * 원격저장소 연결
<pre>
<code>
git remote add origin https://github.com/JangYuJungCPZ/Git.git    # git remote add [원격저장소이름] [원격저장소주소]

git remote -v   # 원격저장소 목록 조회
</code>
</pre>
## 2-2. push
> * 원격저장소에 업로드    
> 현재 브랜치(원격용 작업 공간)에서 새로 생성한 커밋들을 원격저장소에 업로드    
> fatal: The current branch master has no upstream branch. 오류가 날 경우 git push -u [원격저장소이름] [브랜치명] 의 명령어로 업스트림 지정

	git push [원격저장소이름] [브랜치명] # 통상 첫번째 원격저장소이름은 origin으로 등록합니다.(remote 할때)
	git push [원격저장소이름] [로컬브랜치명:원격브랜치명]  # 로컬 브랜치명과 원격 브랜치명이 다를때  # git push origin develop/12345:master_207

## 2-3. clone / fetch / pull
> * 원격저장소에서 가져오기
### 2-3-1. clone
> * 로컬 또는 원격저장소를 클론으로 복제할때 사용.    
해당 명령어는 기존에 작업한 내용을 병합하지 않고 그대로 가져오기에 프로젝트 시작전 세팅시 처음 불러올때 사용합니다.

	git clone https://github.com/JangYuJungCPZ/Git.git   # git clone <저장소 주소> (예시)
	git clone https://github.com/JangYuJungCPZ/Git.git Git2   # git clone <저장소 주소> [새로운 폴더명] (예시)

### 2-3-2. fetch
> * 원격저장소 소스코드를 불러와 로컬저장소(커밋히스토리공간)에 생성    
> 이후 merge를 해주면 pull과 동일한 명령이 실행됩니다.    
> 바로 병합이 아니라 따로 확인해야하거나 별도의 작업을 진행해야할때 주로 사용합니다.

	git fetch [원격저장소이름] [브랜치명]   # git fetch origin master (예시)

### 2-3-3. pull (**많이 사용)
> * pull = fetch(불러오기) + merge(병합)    
> 로컬 소스코드에 원격저장소 소스코드를 덮어씌우는데, 양쪽의 변경사항을 전부 합쳐서 저장합니다.    

	git pull [원격저장소이름] [브랜치명]   # git pull origin master (예시)


# 3. Branch (중요)
## 3-0. HEAD
> * 현재 작업중인 브랜치를 가리킵니다. (즉, 현재 작업중인 브랜치의 커밋을 가리킵니다.)
> * 모든 작업은 HEAD가 가리키는 브랜치에서 이루어집니다. HEAD의 위치를 주의해주세요.
## 3-1. branch
> * 브랜치 조회/생성하기

	git branch  # 로컬 저장소의 브랜치 목록 조회 -v 옵션 사용시 마지막 커밋도 함께 표시합니다.
	git branch [브랜치이름] [커밋체크섬]  # 새로운 브랜치 생성(브랜치이름으로) 커밋체크섬을 주지 않으면 HEAD로 부터 브랜치 생성합니다. # git branch newbranch master
	git branch -f [브랜치이름] [커밋체크섬]  # 이미 있는 브랜치를 다른 커밋으로 옮기고 싶을때 사용합니다. # git branch -f newbranch2 master 
	git branch -d [브랜치이름]  # 특정 브랜치를 삭제할때 사용 (HEAD 브랜치와 병합되지 않은 브랜치는 삭제 불가)
	git branch -D [브랜치이름]  # 브랜치를 강제로 삭제하는 명령 (매우 조심해서 사용)

## 3-2. checkout
> * 브랜치로 체크아웃 (HEAD를 옮김)    
> * 작업하고자 하는 브랜치로 체크아웃 후 작업해야합니다.

	git checkout [브랜치이름]  # 특정브랜치로 체크아웃합니다. # git checkout newbranch
	git checkout -b [브랜치이름] [커밋체크섬]  # 특정 커밋에서 브랜치를 새로 생성하고 동시에 체크아웃합니다. 자주사용합니다. # git checkout -b newbranch3 master

## 3-3. merge
> * 병합

	git merge [대상 브랜치]  # 현재 브랜치(HEAD)와 대상 브랜치를 병합할때 사용합니다. 병합커밋(merge commit)이 새로 생기는 경우가 많습니다.

## 3-4. rebase
> * 재배치

	git rebasc [대상 브랜치]  # 내 브랜치의 커밋들을 대상 브랜치에 재배치합니다. (꼬일 수 있음 조심해서 사용)

## 3-5. reset
> * merge또는 push를 했을때 오류가 나는 경우 현재 브랜치를 특정 커밋으로 되돌릴때 사용합니다.

	git reset --hard [이동할커밋체크섬]  # 현재 브랜치를 지정 커밋으로 옮긴다. 폴더의 내용도 함께 변경됩니다.

> * 커밋체크섬은 git log를 통해 알 수 있습니다. 하지만 복잡하고 길어서 간단한 오류로 한두단계의 커밋만 이동해도 될 경우 아래의 명령어를 사용합니다.

	git reset --hard HEAD~[숫자]  # 1은 부모커밋, 그 이후로 숫자가 커질수록 위쪽의 커밋으로 이동합니다.
	git reset --hard HEAD^[숫자]  # 1은 부모커밋, HEAD^2는 두번째 부모커밋. 병합커밋처럼 부모가 둘 이상인 커밋에만 의마가 있습니다.

## 3-6. tag
> * 태그를 남깁니다.

	git tag -a -m "메세지" [태그이름] [브랜치]  # 주석이 있는 태그생성. 메시지와 태그이름은 필수이고 브랜치명은 생각하면 HEAD에 생성합니다. # git tag -a -m "테스트" v0.1 master
	git push [원격저장소별명] [태그이름]  # 원격저장소에 태그를 업로드  # git push origin v0.1

# 4. log
> * 로그를 조회합니다. 대표적으로 자주 사용하는 조회 형식만 입력하였습니다.

	git log  # 로그 전체 조회
	git log --oneline  # 로그 전체 간략조회
	git log --oneline --graph --all # 로그 전체 그래프 조회 (자주사용) (-n1 / -n2 형식을 뒤에 붙이면 최근 몇건만 조회해옵니다.)
	git log -p -n2  # 최근 두건 수정된 로그의 수정부분 확인(diff)

