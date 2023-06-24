# git
저장소의 종류
- 로컬 저장소(local) : 개인 전용
- 원격 저장소(remote) : 공유 전용

작업 트리(Work-Tree)
  폴더 또는 디렉터리를 의마한다.
스테이징 - add
  작업 트리를 커밋하기 전, 작업 트리의 파일 상태를 기록하는 임시 공간(인덱스)에 올리는 작업.
  커밋하기 전 반드시 커밋할 내용은 인덱스에 추가되어야 하며, 이를 스테이징이라고 한다.
  변경한 모든 파일을 커밋하지 않고, 원하는 파일만 골라서 스테이징을 하게 되면
  인덱스에 등록된 파일들만 커밋된다. 스테이징하지 않은 파일들은 커밋이 될 수 없다.

커밋 - commit
  새로운 버전을 만들 때 사용한다.
  예를 들어 A와 B라는 파일을 하나의 버전으로 관리하고자 할 때 사용한다.
  커밋 시 고유한 커밋 아이디가 부여되며, 원하는 버전으로 들어갈 때 커밋 아이디 중 앞 7글자를 사용한다.

브랜치(Branch)
  한 개의 저장소를 여러 갈래로 나누어 관리할 수 있다.
  각각의 독립된 Branch에서는 각각의 개발자들이 기존 버전과 비교를 하거나
  버그를 테스트하는 등 협업을 통해 필요한 목적으로 사용할 수 있다.
  커밋을 통한 버전 관리는 한 가지의 커밋 히스토리 경로를 가지지만
  브랜치를 나누면 커밋 히스토리를 여러 경로로 나누어 사용이 가능해진다.

  
//저장소 생성 및 연결
$ git init
$ git remote add origin [원격저장소 주소]
$ git branch -m master main

//파일 업로드
$ git pull (또는 git pull origin [브랜치 이름])
$ git add .
$ git commit -m "commit message"
$ git push (또는 git push origin [브랜치 이름])

//추가적인 명령어
$ git remote -v
$ git remote rm origin
$ git branch
$ git config --global init.defaultBranch [브랜치 이름]
$ git status
$ git rm --cached -r .


저장소를 처음 만드는 경우
1. 깃허브에 원격 저장소(repository) 만들기
  본인 깃허브 페이지의 Repository 탭에서 New 버튼을 누르면 저장소를 생성할 수 있다.
  저장소 이름을 적어주면 되는데(ex. my-cool-website), 컴퓨터에 있는 폴더랑 이름이 달라도 상관없다.
  저장소에 대한 설명파일도 있는게 좋다. "Add a README file"을 체크해 주자.
2. 로컬 저장소 만들기
  내 컴퓨터 폴더 중 깃허브에 올리려는 폴더에 마우스 우클릭하여 git bash를 열어주고 다음과 같이 입력한다.
  $ git init
3. 로컬 저장소와 원격 저장소 연결
  원격 저장소의 주소를 이용해 두 저장소를 연결한다.
  주소는 깃허브 저장소에서 초록색 "Code"버튼을 누르면 보이는 HTTPS 탭에 적힌 주소를 사용하면 된다.
  잘 모르겠으면 저장소 페이지 주소에서 뒤에 .git을 붙여주자.
  즉 형식은 다음과 같다: https://github.com/아이디/저장소이름.git
  $ git remote add origin [원격저장소 주소]

4. 파일 업로드 준비
   branch 개념은 따로 설명하진 않겠지만 대충 버전이라고 이해하면 된다.
  깃허브 저장소의 기본 branch 이름은 main이다. 따라서 파일도 main branch에 올려줘야 하는데,
  로컬 저장소에서는 branch 이름이 기본으로 master로 되어있다.
  원래 깃허브에서 기본 branch가 master였다가 노예제를 연상시킨다고 main으로 바뀌면서 이 차이가 생긴 것 같다.
  그러므로 먼저 branch 이름을 master에서 main으로 바꿔줘야 한다.
  $ git branch -m master main
5. 파일 올리기
  이제 드디어 파일을 올리는 단계다.
  총 3단계로 이루어지는데, add → commit → push 순서이다.
  $ git add .
  특정한 파일만 올리는 경우
  $ git add [파일/디렉토리]
  $ git commit -m "commit message"
  //로컬 저장소에서 원격 저장소로 올리기
$ git push origin [브랜치 이름]

//또는: 아래처럼 목적지 생략 가능 (현재 작업중인 브랜치로 push됨)
$ git push


