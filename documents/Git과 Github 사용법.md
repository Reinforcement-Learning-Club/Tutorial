# Git과 Github 사용법

Git을 설치하면 Git의 사용 환경을 설정해 주어야 한다. 환경 설정은 한 컴퓨터에서 한 번만 진행하면 된다.
Git을 설치한 후, 가장 먼저 해야하는 것은 사용자 이름과 이메일 주소를 설정하는 것이다 (commit을 할 때 이 정보가 사용됨).

Command line에 다음과 같이 입력하여 사용자 이름과 이메일 주소를 설정할 수 있다.

`> git config --global user.name "<사용자 이름>"`

`> git config --global user.email <이메일 주소>`


설정한 내용은 `git config --list` 명령으로 확인할 수 있다.

사용자 이름과 이메일 주소를 설정한 후에는 저장소 (repository)를 초기화해야한다. 
먼저, Git 저장소를 적용할 폴더를 생성해보자. 저장소는 해당 경로의 directory에 생성된다.

윈도우 기준으로 폴더를 생성하는 명령어는 `mkdir <폴더 이름>` 이다.
test란 이름을 가진 폴더를 생성해보자.

`> mkdir test`

만들어진 test 폴더로 이동한 후 저장소를 초기화할 것이다.
`cd <directory 경로>` 명령어는 change directory란 뜻으로 입력한 경로로 directory를 변경한다.
test 폴더로 경로를 변경해보자.

`> cd test`

Git 저장소를 초기화하는 명령어는 `git init`이다. 초기화를 한 후, 해당 directory를 확인하면 .git 폴더가 생성된 것을 알 수 있다 (숨김 파일로 되어있으므로 숨김을 해제해야 볼 수 있음). .git 폴더에는 저장소에 필요한 뼈대 파일이 들어있다.

`> git init`

```
Initialized empty Git repository in C:/Users/User/GitHub/test/.git/
```

초기화는 기존 저장소를 clone 할 때에는 하지 않는다. 기존 저장소를 복사하는 방법은 추후에 배우기로 한다.


`git status` 명령어는 현재 저장소의 상태를 나타낸다. 저장소를 초기화하였다면 이 명령어를 실행하면 다음과 같은 메세지를 볼 수 있을 것이다.

`> git status`

```
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

저장소 초기화만으로는 아직 어떤 파일도 관리하지 않는 상태이다. Git이 파일을 관리하게 하려면 저장소에 파일을 추가하고 commit 해야한다.
메모장을 열어 아무 말이나 적은 후 현재 directory에 저장해보자.
해당 파일을 저장소에 추가하는 방법은 `git add <파일명.확장자>` 명령어를 사용하는 것이다.

`> git add 나나나.txt`

특정 파일이 아니라 추가되거나 변경된 모든 파일을 저장소에 추가하고 싶다면 파일명 대신 `.` 을 입력한다.

`> git add .`

`git add` 명령어로 파일을 추가한 후에는 commit을 해야한다. commit이란 변경된 사항을 저장소에 기록하는 것이다.
commit은 `git commit -m <커밋 메세지>` 명령어로 수행된다. commit 명령어는 `-m`이란 옵션과 commit message를 입력해야한다.
commit message는 어떠한 변경 사항이 생긴 것인지 나타낸다.

`> git commit -m "test commit"`

```
1 file changed, 1 insertion(+) 
create mode 100644 "나나나.txt"
```


Git을 사용하는 목적 중에는 버전 컨트롤 이외에 다른 사람들과의 협업도 있을 것이다. 다른 사람들과 함께 일을 하기 위해서는 인터넷이나 네트워크 어딘가에 저장소가 있어야 한다. Github는 인터넷상에 원격 저장소를 사용할 수 있는 웹 서비스를 제공한다. 
먼저, [RLC](https://github.com/Reinforcement-Learning-Club/Tutorial)을 클릭하여 우리 동아리의 원격 저장소에 들어가보자.
해당 사이트는 우리 동아리의 원격 저장소이다. 
원격 저장소를 이용하면 다른 사람과 함께 데이터를 관리할 수 있으며 변경 사항을 검토하고 의견을 나눌 수 있다.


원격 저장소를 우리 로컬 환경으로 가져와야 해당 저장소의 파일을 수정 및 변경할 수 있을 것이다.
`git clone` 명령어는 원격 저장소를 로컬 환경에 복제한다.
다음과 같이 복제하고자 하는 원격 저장소의 웹 url을 입력하면 원격 저장소가 우리의 로컬 환경에 복제된다.

`> git clone https://github.com/Reinforcement-Learning-Club/Tutorial.git`

```
Cloning into 'Tutorial'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 13 (delta 0), reused 7 (delta 0), pack-reused 0
Receiving objects: 100% (13/13), 4.17 KiB | 2.09 MiB/s, done.
```

해당 directory 경로에 가보게 되면 Tutorial이란 이름의 폴더가 생긴 것을 알 수 있다.
즉, Tutorial란 원격 저장소를 우리의 로컬 환경으로 복제해온 것이다.
`cd` 명령어로 해당 directory로 경로를 변경해보자.

`cd Tutorial`

이제 우리가 파일을 수정, 변경, 추가 등을 한 후, 앞서 배운 `git add`와 `git commit` 명령어로 저장소에 변경사항을 추가하고 기록한다.
원격 저장소를 복제해 온 경우 `git init` 명령어를 실행한다면 이전 기록이 초기화 되므로 주의하도록 하자.

로컬 환경과는 다르게 원격 저장소에 변경 사항을 반영하고 다른 사람에게 공유하려면 `git push <원격 저장소 이름> <브랜치 이름>` 명령어를 추가로 실행해야한다.
`git push` 명령어는 원격 저장소 이름과 브랜치 이름을 입력해야하는데 이것들은 무엇일까?

원격 저장소를 복제해온 경우 원격 저장소 이름은 origin으로 자동 설정된다. 따라서 특별한 경우를 제외하고 원격 저장소 이름은 origin으로 입력하면 된다.
그렇다면 브랜치란 무엇일까? 브랜치란 독립적인 작업을 진행하기 위해 사용된다.
각각 생성된 브랜치는 서로에게 영향을 받지 않는다.

예를 들어 A와 B, 두 사람이 함께 작업을 하고 있다고 가정하자.
A가 수정한 코드가 B가 작업하고 있는 코드에 바로 영향을 준다면 B라는 사람은 A가 수정하는 내용을 계속해서 확인하며 작업을 해야할 것이다.
A 또한 B의 수정 내용에 영향을 받기 때문에 제대로된 일을 할 수 없을 것이다.

브랜치는 이러한 문제를 피할수 있게 해준다.
main branch는 저장소의 주 브랜치로 저장소에 변경사항을 직접적으로 처리하는 브랜치이다.
즉, 함께 일하고 있는 사람들이 모두 main branch로 일을 하게 된다면 앞서 말한 문제가 똑같이 발생할 것이다.
이제 우리는 영향을 주지도, 받지도 않는 브랜치를 만들고 작업을 진행할 것이다.
먼저 `git status` 명령어로 현재 저장소의 상태를 보면 main branch인 것을 알 수 있다.

`> git status`
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

새로운 브랜치는 `git checkout -b <새로운 브랜치 이름>` 명령어로 만들 수 있다.

`git checkout -b beomjin1`
```
Switched to a new branch 'beomjin1'
```

다시 `git status` 명령어를 실행한다면 다음과 같이 브랜치가 beomjin1으로 바뀐 것을 알 수 있다.

`> git status`
```
On branch beomjin1
nothing to commit, working tree clean
```

브랜치는 꼭 한 사람당 하나씩만 생성해야하는 것은 아니다.
브랜치를 변경하는 명령어는 `git checkout <변경할 브랜치 이름>`이다.

`> git checkout main`
```
Switched to branch 'main'
Your branch is up to date with 'origin/main'
```

브랜치를 다시 beomjin1으로 바꾼 뒤, 현재 directory에 자신의 이름으로 된 폴더를 하나 생성해보자.

`> git checkout beomjin1`

`> midkr Beomjin`

만들어진 이름 폴더에 메모장 파일을 하나 생성해서 놓아보자. 
그 후에 `git status` 명령어를 입력하면 다음과 같이 저장소가 추적하지 않는 새로운 파일이 생겼다는 메세지를 볼 수 있다.
```
On branch beomjin1
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Beomjin/

nothing added to commit but untracked files present (use "git add" to track)
```

저장소에 이를 추가하고 기록하려면 `add`와 `commit`을 진행한다.

`> git add .`

`> git commit -m "just test"`
```
[beomjin1 1228d1e] just test
 1 file changed, 1 insertion(+)
 create mode 100644 Beomjin/test.txt
```

이제 다른 사람에게 변경된 사항을 공유하고 원격 저장소에 이를 반영하기 위해 `git push <원격 저장소 이름> <브랜치 이름>` 명령어를 실행한다.

`> git push origin beomjin1`
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 20 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 359 bytes | 359.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'beomjin1' on GitHub by visiting:
remote:      https://github.com/Reinforcement-Learning-Club/Tutorial/pull/new/beomjin1
remote:
To https://github.com/Reinforcement-Learning-Club/Tutorial.git
 * [new branch]      beomjin1 -> beomjin1
```

`push`를 진행한 후에 Github의 해당 저장소에 들어가게되면 "compare & pull request" 버튼이 활성화 된 것을 알 수 있다.
PR (pull request)란 `push`한 변경된 사항을 main branch에 병합하기 전 다른 사람들에게 알리고 변경 사항을 논의 및 검토를 하는 것이다.
"compare & pull request" 버튼을 누른 후, 해당 commit에 대한 변경된 사항을 입력한 후 "create pull request" 버튼을 누르면 PR이 생성된다.
다른 사람들 (협업자들, reviewer들)의 검토가 끝난 후 main branch로의 병합이 승인되면 main branch로 병합되어 저장소에 변경 사항이 반영된다.


원격 저장소에 변경된 최신 사항을 자신의 로컬저장소에 반영하고자 한다면 `git pull <원격 저장소 이름> <브랜치 이름>`을 실행한다.
일반적으로는 main branch을 가져오지만 때에 따라 생성된 특정 branch의 변경사항을 가져올 수도 있다.

`> git pull origin main`
```
From https://github.com/Reinforcement-Learning-Club/Tutorial
 * branch            main       -> FETCH_HEAD
Updating e0ec3f3..07500cf
Fast-forward
```
