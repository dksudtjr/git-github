# 1. git/github 기초

< git(버전관리 툴) 필요한 이유 >

1. 버전관리
바뀌기 전 내역들도 중간중간 저장.(나중에 언제 필요할지 모르기 때문)
폴더 내 상태를 과거로 되돌리거나
과거의 필요한 것만 챙겨서 특정시점으로 가져올 수 있음.

2. 협업
"프로젝트 폴더 전체"가 있어야 테스트 등을 할 수 있음.
이메일, 클라우드 등을 사용하기엔 복잡함.
에러 등 발생했을 때 누가 뭘 어떻게 건드렸는지 파악 쉬움.

< git >

$ cd (폴더 디렉토리)
$ git init : git 시작(폴더의 모든 수정내역들이 저장되는 .git(숨김폴더)공간 생성)


< 백업을 해보자 >

$ git add -A : 백업에 포함할 파일들, 일단 모두를 설정
$ git commit -m "(작업수행 내용)" : commit을 통해 폴더 전체 내용들 박제. 
				+ "해당 시점의 작업내역 코멘트"
				--> 각 버전의 변경사항만 기록(용량 차지 적음)

< 프로젝트를 과거로 되돌려보자 >

$ git logs: commit 내역들을 확인
$ git reset --hard 3r8da0 : 박제됐던 과거 상태로 복원(수정/삭제 파일은 복원, 새파일 삭제)

< 프로젝트의 branch를 따보자 >

main branch: 주가 되는 코드 작업
branch: 시도해 볼 부분 작업

$ git branch : 현재 branch 목록 --> 현재 branch는 앞에 "*"가 붙는다.
$ git branch "(브랜치 이름)" : 브렌치 땀
$ git merge "(브랜치 이름)" :  branch를 main에 합침


git서버/github 을 이용하면 git으로 commit한 내용들을 원격으로 저장가능.

<github>

git(카메라 앱): 버전관리를 위한 "소프트웨어"
github(유튜브): git을 통해 원격전송 된 내역들이 저장되는 공간을 제공하는 "서비스"


# 2. git

필요한 것
1. git소프트웨어 설치
2. vscode 설치

git사용법
1. git저장소 만들기
1-1 컴퓨터에서 원하는 위치에 프로젝트를 진행할 폴더를 생성
1-2 vscode로 해당 폴더 열기
1-3 파일 생성 --> git이 관리하도록 해보자
1-4 터미널에서 cd (해당폴더경로) 입력 
--> vscode에서 ctrl+~ 입력하면 하단에 현재폴더로 이동된 상태에서 터미널 열림

1-5 $ git init : 폴더의 모든 수정내역들이 저장되는 .git(숨김폴더) git저장소 생성 (해당 폴더가 git관리 하에 들어감)
1-6 $ git config --global user.name "(내 이름)"
	$ git config -- global user.email "(내 메일주소)"
	내 이름과 이메일 등록
1-7 숨김파일로 .git폴더 생성됨. (폴더의 모든 수정내역들이 저장되는 .git(숨김폴더)공간 생성)

2. 현재 시점 저장
2-1 $ git status : 해당 폴더 내 변화들과 캡슐 상태 확인 (untracked files: stage 안 됨)
		(changes to be commited: stage 완료)
2-2 $ git add -A: 해당 폴더 내 변화들을 "캡슐에 add" (스테이지)
2-3 $ git commit -m "(코멘트)" : 캡슐을 로컬저장소에 저장
2-4 $ git log : git 상태들 확인(일련번호 등) <-- vi화면이 뜨면 :q를 통해 나오거나 :wq를 통해 저장
 
3. 과거로 돌아가기 - reset(hard: 특정 때로 돌아가기(복구불가능)/ soft: 모든 로컬 변경사항 유지)
3-1 $ git log : 돌아갈 commit의 일련번호 앞 6자리 복사.
3-2 $ git reset (일련번호6자리) --hard

3. 과거로 돌아가기 - revert (반대되는 변화로 상쇄시킴, 즉, 특정 상태로 돌아가기(변화를 상쇄))
3-1 $ git log : 되돌릴 commit의 일련번호 앞 6자리 복사.
3-2 $ git revert (일련번호6자리)

4. 평행우주 - branch
4-1 $ git branch (브랜치 이름) :  새로운 브랜치 생성
4-2 $ git branch : 브랜치들 조회 (master: 메인 브랜치)
4-3 $ git checkout (대상 브랜치명) : 다른 브랜치로 이동


5. 다른 우주에서 가져오기 - merge (수정 파일 같은 경우/ 수정 파일 다른 경우)
5-1-1 $ git checkout master : 마스터 브랜치로 돌아 옴.
5-1-2 $ git merge (가져올 브랜치)  <-- 마스터로 병합 됨
5-1-3 $ git log --graph --all --decorate : 시각화 된 작업내역

5-2-1 $ git checkout master : 마스터 브랜치로 돌아 옴.
5-2-2 $ git merge (가져올 브랜치)  <-- 마스터로 병합 됨 <-- 같은 파일 같은 라인 수정한 경우 conflict!!
5-2-3 직접 파일 수정
5-2-4 $ git add -A
5-2-5 $ git commit <-- merge완료

6. 다른 우주에서 가져오기 - rebase (변경 내역이 한 줄로 깔끔하게 정리 )

7. 브랜치 삭제
7-1 $ git branch -D (삭제할 브랜치명)

- 특정 브랜치로 이동 - 
git checkout (브랜치명)

- 다른 브랜치의 변경사항 가져오기 -
git merge (대상 브랜치명)

- 다른 브랜치의 변경사항 가져오기(이력 깔끔히)
git rebase (대상 브랜치명)

- 브랜치 삭제 -
git branch -D (삭제할 브랜치명)


___________병합 전___________
<mater>
[dog파일] dog: mong (3시 커밋)
[cat파일] cat: tom (1시 커밋)
[mouse파일] mouse: jerry (1시 커밋)

<my-another-idea>
[dog파일] dog: snoopy 
[dinosaur파일] dinosaur: dooly 
[cat파일] cat: nyang (2시 커밋)

___________병합 후___________ 

[cat파일] dog: mong
[dog파일]  cat: nyang
[dinosaur파일] dinosaur: dooly





# 3 github

소스들을 업로드해서 저장하고 다른 개발자들과 공유할 수 있는 개발 플랫폼
git을 통해 원격전송 된 내역들이 저장되는 공간을 제공하는 "서비스"

내 소스들을 저장하고 협업할 수 있음.

1. github 사용법 ( remote, push )

1-1 repository 생성 <-- git으로 관리되는 프로젝트 폴더 하나가 원격으로 저장되는 공간

2. github에 소스 올리기
내 프로젝트를 레파지토리에 올려보자.

2-1 $ git status : 현재까지의 사항들이 commit 되어있는지 확인
2-2 $ git remote: 현 폴더의 원격 레파지토리 확인 (설정한 바가 없으므로 아무것도 뜨지 않음)
2-3 $ git remote add origin https://github.com/dksudtjr/git-github.git
	: "git-github" 레파지토리를 해당 폴더의 "origin"이라는 이름의 원격 저장소로 설정
2-4 $ git push -u origin master 
	: 해당 폴더의 현 브랜치에 커밋된 내용들을 origin이름의 원격 저장소에 master이름의 브랜치에 올림
2-5 github을 새로고침하면 로컬에서 푸시한 파일명과 커밋코멘트가 뜬다. (커밋코멘트 클릭하면 해당 커밋에서의 변화들 확인)
2-6 $ git remote: 추가한 원격 레파지토리 이름 출력

<파일 추가할 경우>
2-7 $ git add -A
2-8 $ git commit -m "add dog file"
2-9 $ git push origin master

3. 다루지 않을 파일 설정 ( .gitignore )
git으로 관리 및 gihub에 올릴 필요 없는 파일이 있을 경우 사용.
git ignore 패턴 참조 --> https://www.atlassian.com/git/tutorials/saving-changes/gitignore

3-1 프로젝트 폴더에 ".gitignore"파일을 생성 (숨김파일로 지정됨)
3-2 "secret-file"파일을 생성.
3-3 .gitignore파일에 특정 파일명(secret-file)을 입력하면 특정 파일은 git이 다루지 않음.
3-4 $ git status 입력하면 "secret-file"파일은 나타나지 않음.
3-4 $ git add -A 
3-5 $ git commit -m "add .gitignore"
3-6 $ git push
3-7 github을 확인해 보면 "secret-file"파일은 github에서도 보이지 않음.


4. github에서 소스 내려받기 ( clone )
private에서 초대: repository -> collaborators -> username or email

(내 컴퓨터의 [download-github]폴더에 github의 [git-github]폴더를 다운받는다고 가정하자)
4-1 컴퓨터에서 내려받을 위치의 폴더([download-github])를 vscode로 열고 터미널 실행(ctrl+~)
4-2 github의 repository에서 "clone or download"를 클릭해 url 복사
4-3 $ git clone (깃헙 레파지토리 url)
4-4 $ cd (내려받은 폴더명) : 내려받은 폴더에서 작업하려면 이동해야 함

5. 작업 주고받기 ( fetch/merge )

$ git fetch : 코드를 받아 옴 (작업한 코드의 충돌 방지) 
$ git pull : 코드를 받은 즉시 merge (충돌 가능)

협업 시, 항상 fetch/pull을 먼저 해줘야 함.
github에서 pull하기 전에 push할 수 없음.

A가 컴퓨터에서 작업을 수행하고 github에 올린다. 그 후, B가 다른 컴퓨터에서 내려받는다.
B는 github에 들어가지 않고 $ git fetch -> $ git status 를 이용해 변경내역을 확인할 수 있다.

5-1 A가 컴퓨터에서 작업을 수행하고 github에 올린다.
	작업수행 -> $ git add -A -> $ git commit -m "edit dog name" -> $ git push
5-2 B가 다른 컴퓨터에서 내려받는다. 
	$ git fetch -> $ git status : 커밋 몇 개가 뒤쳐저 있는지 확인 -> $ git pull origin(원격명) master(브랜치명)

6. 브랜치 주고받기

$ git checkout -b (브랜치명) : 브랜치를 만듦과 동시에 체크아웃 ($ git branch + $ git checkout 역할)
$ git fetch
$ git branch -a : 로컬과 원격 모두의 브랜치 조회
$ git checkout -b (로컬브랜치) (원격저장소/원격브랜치) : 로컬브랜치를 만들어서 원격저장소의 브랜치를 받음

7. 충돌 해결하기	




참고자료: 

얄팍한 코딩사전 - 가장 쉬운 Git 강좌
https://www.youtube.com/watch?v=FXDjmsiv8fI
https://www.youtube.com/watch?v=GaKjTjwcKQo

자주 사용하는 기초 git 명령어 정리
https://medium.com/@pks2974/%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B8%B0%EC%B4%88-git-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0-533b3689db81 

누구나 쉽게 이해하는 git 입문
https://backlog.com/git-tutorial/kr/
