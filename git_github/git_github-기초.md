# Git & GitHub 기초

## Git 설치 후 사전 설정

Git을 설치 후에는 자신이 누군지 설정해야 한다.
```
git config --global user.email "<사용자 이메일>"
git config --global user.name "<사용자 이름>"
```

## Git 버전 관리 시작

1. GitBash 혹은 터미널에서 관리하고자 하는 프로젝트 폴더까지 이동한다.  
2. `git init` 명령어를 통해 현재 프로젝트 폴더를 Git으로 관리할 것임을 명시한다.

## Git의 파일 관리 절차

![Git](image.png)
- `git status` 명령어를 통해 어떤 파일이 추가되거나 변경되었는지 확인할 수있다.
- `git add <파일명>` 명령어를 통해 추가되거나 변경된 파일을 commit 대상으로 지정한다.
- `git add -all` 모든 추가되거나 변경된 파일을 commit 대상으로 지정한다.
- `git commit -m "commit message"` commit 대상으로 지정된 파일들의 변경점을 최종적으로 git에 기록한다.


## Git에서 관리하지 않을 파일 지정

- `.gitignore` 파일을 생성해 파일에 관리하지 않을 파일명들을 입력한다.


## 파일 기록을 취소하는 방법

1. `git add` 진행 전일 경우
    - `git restore <파일 이름>` 
2. `git add` 까지만 이루어지고 commit 되지는 않은 경우
    - `git restore --staged <파일 이름>` 으로 add를 취소하는 것이 가능하다.
3. `git commit` 까지 이루어진 경우
    - `git reset HEAD^` `git reset HEAD^^` 을 이용해 한 단계 혹은 두 단계 까지 commit을 취소하는 것이 가능하다.
    - `git reset HEAD~<숫자>` 을 이용해 원하는 단계 만큼 commit을 취소하는 것이 가능하다
    - `git log` 를 사용하면 지금까지 저장된 commit들의 해시코드가 나타나는데 `git reset <해시코드 앞 6자리>` 를 이용해 원하는 단계의 commit으로 복구 가능하다.
    - `git push` 까지 이루어진 상황에서는 가급적 사용하지 않는 것이 좋다.
 

## SSH를 통한 GitHub와 컴퓨터 연동

1. GitBash 혹은 터미널에서  `ssh-keygen` 명령어를 통해 ssh 키를 생성한다.
2. `cd .ssh` 명령어를 통해 .ssh 폴더로 이동하고 `cat id_rsa.pub` 명령어를 통해 생성된 키를 확인한다.
3. **GitHub** 홈페이지의 **Settings** 페이지에서 **SSH and GPG keys** 메뉴에 생성된 ssh키를 등록한다.


## GitHub에서 프로젝트 가져오기

1. **GitHub**에서 가져올 프로젝트 리포지토리의 Http, 혹은 SSH 주소를 복사한다.
2. GitBash 혹은 터미널에서 프로젝트를 가져오고자 하는 위치로 이동 후 `git clone <복사한 주소>` 명령어를 사용한다.
3. 이후 GitHub에 업로드 된 내용으로 프로젝트를 갱신하고 싶다면 `git pull` 명령어를 사용한다.


## 컴퓨터의 프로젝트를 GitHub로 올리기

1. **GitHub**에서 프로젝트를 업로드 할 리포지토리를 생성 후 Git 주소를 복사한다.
2. GitBash 혹은 터미널에서 업로드 할 프로젝트로 이동 후 명령어를 아래와 같이 입력한다.
    ```
    git remote add origin <Git 주소>
    git push --set-upstream origin main(혹은 master)
    ```
3. 이 후 GitHub에 프로젝트를 업로드 하고싶다면 add -> commit 절차를 수행 후 `git push` 명령어를 사용한다.

## Conflict가 발생할 때

같은 파일에 대해 commit 이력이 다른 파일이 merge되는 경우 충돌이 발생할 수 있다.  
이 때 `git pull`을 사용하여 파일을 내려받게 되면 Conflict가 발생한 부분에 GitHub상의 코드와 로컬 프로젝트의 코드가 혼재되어 나타나게 되는데 이 부분을 수정한 후 다시 add -> commit -> push의 절차를 밟으면 된다.