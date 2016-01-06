# Tutorial GIT

[![Join the chat at https://gitter.im/KennethanCeyer/tutorial-git](https://badges.gitter.im/KennethanCeyer/tutorial-git.svg)](https://gitter.im/KennethanCeyer/tutorial-git?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

### 어떻게 깃을 사용하는지 빠르게 알아봅시다.
> Quick learn How to use the Git.

- 읽는데 걸리는 예상시간 `15분`
- 다 외우기 위하여 반복 학습이 필요한 횟수 `3번`

- 개발 회사에 다니시지만 Git을 모르신다면 바로 읽어주세요.
- Git을 도입할지 망설이시는 관리자, 담당자분들은 바로 읽어주세요.
- 2명이상의 협업을 하는 스타트업, 인디 개발자는 도입을 고려해주세요.

- 잘못 기술되었거나, 추가되었으면 하는 내용은 kennethan@nhpcw.com으로 형식 상관없이 보내주시면
 
 3일 내 반영하(도록 노력하)겠습니다.

### 시작하며

##### 깃을 왜 사용하죠?

- 빠른 협업환경 조성
- 누가 언제 무엇을 왜 수정했는지 코드리뷰가 가능.
- IssueTracker 및 Migrate 연동 지원.
- GitHub를 이용하여 자신의 git을 쉽게 전파, 공유가 가능.
- Continuous Integration (지속적인 통합) 지원.
- VisualStudio, Eclipse, Android Studio 등 많은 부분에서 Git연동 제공.

- **결국 대게는 협업을 위해서 사용**

##### 깃이 어떤 역할을 하는건가요?

- 소스 병합
- 소스 리비전 관리
- 소스 릴리즈
- 소스 태깅
- 소스 기록, 업로드
- 소스 변경사항 검토

##### 깃은 어디에서 지원하나요?

- Windows
- Mac
- Linux, Unix 계열

----

### 깃의 기능

#### 깃의 설정 (클라이언트)
- 처음 시작하는 것이라면 git의 config 과정을 진행해야합니다.
- `git config` 명령어를 이용하여 계정에 대한 정보를 설정합니다.

 ```bash
$ git config --global user.name "Kenneth"
$ git config --global user.email "kennethan@nhpcw.com"
```

- 깃은 초기에 `git init` 작업을 진행합니다
- 혹여나 GitHub에서 클론을 받은경우 이 작업은 필요하지 않습니다.
- 아래 샘플 코드를 확인해주세요.

 ```bash
$ git init
```
- `git init`을 하셨으면 Git 리모트를 설정하실 수 있습니다.
- Git 리모트란 Git을 원격저장소에 저장하는 앤드포인트를 의미합니다.

 ```bash
$ git remote add origin https://github.com/KennethanCeyer/tutorial.git
```

- 깃의 리모트 URL을 이용하여 원격저장소에 저장된 파일을 컴퓨터로 복사해올 수 있습니다.
- 이때 `git clone`을 사용하여 복사를 시작합니다.

 ```bash
$ git clone https://github.com/KennethanCeyer/tutorial.git
```

- `git clone`을 통해 원격파일을 복사해오면, origin에는 기본적으로 클론해온 리모트 URL이 저장되있습니다.

----

#### SSH 접속설정

- 깃 연결을 보다 안전하고 빠르게 하기 위해서는 `SSH Key` 등록을 권장합니다.
- 이미 존재하는 문서로 [SSH 생성 가이드](https://git-scm.com/book/ko/v1/Git-%EC%84%9C%EB%B2%84-SSH-%EA%B3%B5%EA%B0%9C%ED%82%A4-%EB%A7%8C%EB%93%A4%EA%B8%B0)를 참고하시거나 아래 절차를 따라주시면 됩니다.
- 우선 `ssh-keygen`으로 SSH Key를 생성하시면 됩니다.

 ![Refer SSH](http://www.pigno.se/static/assets/images/git_tutorial_refer_ssh.png)
 
- SSH Key를 생성하셨으면 ~/[사용자 폴더]/.ssh/에 파일이 존재하는 것을 확인하실 수 있습니다.

 ![Refer folder ssh](http://www.pigno.se/static/assets/images/git_tutorial_refer_ssh_folder.png)
 
- 생성한 키 중 `id_rsa.pub`는 GitHub에 등록해주셔야 합니다.
- 아래 절차를 따라해주시면 됩니다.
- [GitHub 홈페이지](http://www.github.com)를 접속하셔서 로그인을 해주세요.
- Profile 중 `Settings` 메뉴를 눌러주세요 (아래 그림을 참고해주세요.)

 ![Refer Setting](http://www.pigno.se/static/assets/images/git_tutorial_settings.png)
 
- Settings 화면 중 우측 사이드메뉴에서 `SSH and GPG keys`를 클릭해주세요.

 ![Refer SSH Keys](http://www.pigno.se/static/assets/images/git_tutorial_settings_sshkey.png)
 
- SSH Keys 화면에서 `New SSH key` 버튼을 찾아 클릭 해주세요.

 ![Refer New SSH key](http://www.pigno.se/static/assets/images/git_tutorial_refer_new_ssh_key.png)
 
- 입력 화면에 아까전의 `id_rsa.pub`의 내용을 입력해주시면 됩니다.

 ![Refer SSH contents](http://www.pigno.se/static/assets/images/git_tutorial_refer_ssh_pub_input.png)
 
**Q. SSH 설정을 해도 아이디와 비밀번호를 물어봐요!**

> 접속 정보에서 Use SSH를 클릭해 SSH 접속 정보를 이용하시기 바랍니다.

![SSH connection string](http://www.pigno.se/static/assets/images/git_tutorial_use_sshkey.png)

이때, `git remote set-url` 명령어를 이용하여 기존의 원격지 주소를 수정해야 합니다.

![SSH remote set-url](http://www.pigno.se/static/assets/images/git_tutorial_refer_set_url.png)

 ```bash
# 혹시 HTTPS 주소를 Remote URL로 사용하는지 체크해주세요.
# Remote URL은 ssh 포맷을 사용해주셔야 ssh 인증을 통해 아이디/비밀번호 입력을 넘어가실 수 있습니다.
    
# origin의 Remote URL 변경방법.
$ git remote set-url origin git@github.com:KennethanCeyer/tutorial-git.git
    
# origin의 Remote URL이 제대로 변경됬는지 체크해주세요.
$ git remote show origin
```

----

#### 소스 기록, 업로드

- 소스를 업로드 하기 위해서는 `git add` 명령어를 이용합니다.
- 샘플을 참고하세요

 ```bash
$ git add *
```

- ignore 파일이나, 삭제한 파일 이력까지 커밋을 하실 경우, `-f` 옵션을 이용합니다.

 ```bash
$ git add * -f
```

- `git remote show origin`을 통해 origin에 리모트 주소가 잘 등록되었는지 확인해보세요.

 ![Remote show origin](http://www.pigno.se/static/assets/images/git_tutorial_refer_remote_origin.png)

----

#### 소스 커밋, 메시지 작성

- 소스를 커밋하시면 `Staged` 상태의 파일이 히스토리로 기록되고 적재됩니다.
- 파일 추적상태의 경우 `git status` 명령을 이용해서 확인합니다.

 ```bash
$ git status
 ```

- `git add` 이후 `git status`를 하면 아래와 같은 화면이 나옵니다.

 ![Git add files](http://www.pigno.se/static/assets/images/git_tutorial_refer_add.png)

- Staged 상태의 파일은 아직 기록된 상태가 아닙니다.
- 파일의 기록을 위해서는 `커밋` 작업이 필요합니다.
- `git commit` 명령을 통해 Staged 상태의 파일을 커밋할 수 있습니다.

![Git commit](http://www.pigno.se/static/assets/images/git_tutorial_refer_commit.png)

- `-m` 옵션을 이용하여 커밋 메시지를 작성하는 것을 권장합니다.
- 실수로 커밋을 하여, 다시 커밋을 할 경우 커밋을 덮어씌울 수 있습니다. 이때 `--amend` 옵션을 이용합니다.

 ```bash
$ git add *
$ git commit -m "UI 레이아웃 이슈 수정."

# 수정사항 발생
$ git add *
$ git commit -m "UI 레이아웃 이슈 수정 및 관리자 벨리데이션 추가." --amend
```

----

#### 소스 업데이트, 커밋된 내용 다운로드

- 상대방이 커밋한 파일은 명령어를 통해서 직접 업데이트를 하셔야 동기화가 됩니다.
- 이때 사용하는 명령어는 `git pull`과 `git fetch`가 있습니다.

 ```bash
# master 브랜치를 pull하여 업데이트
$ git pull origin master
  
# master 브랜치를 fetch하여 업데이트
$ git fetch origin master
```

- Pull과 Fetch의 차이점은 merge 작업을 하느냐 안하느냐로 나뉘어지며.
- Pull은 Fetch + Merge 작업이라고 생각하시면 됩니다.

----

#### 소스의 복원, 리셋

- 여러분이 git을 쓰는 이유중에 중요한 부분을 차지하는 영역입니다.
- 정상적으로 커밋된 히스토리는, 리비전으로 git에 관리됩니다.
- 실수로 잘못 작업하였거나, 예전 버전으로 롤백하여 적용할 경우 여러분은 예전 버전으로 리셋하실 수 있습니다.
- 리셋은 `git reset` 명령을 사용합니다.

 ```bash
$ git reset HEAD^ --soft
```

- `git reset` 다음 인수로는 되돌리는 버전의 위치를 가리킵니다.
- 현재위치(HEAD)를 기준하여 상대적인 위치를 설정하거나, 특정 버전 리비전 고유의 해시값을 지정합니다.
- HEAD를 확인하시고 싶으면 `git reflog` 명령을 이용합니다.

 ![Git reset options](http://www.pigno.se/static/assets/images/git_tutorial_reset.gif)

- `git reset`의 옵션 중 리셋 특성을 정하는 `--soft, --hard, --mixed` 옵션이 있습니다.
- 위 옵션은 아래에서 자세히 설명합니다.

 - `--soft`는 약한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 보존합니다.
 - `--hard`는 강한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 버립니다.
 - `--mixed`는 중간특성의 리셋입니다, 되돌릴 때 기존의 인덱스는 버리고 워킹트리를 보존합니다.

- 되돌리는 위치의 경우 아래와 같은 타입이 있습니다.

 ```bash
# 바로 이전 단계로 인덱스와 워킹트리를 버리고 리셋.
$ git reset HEAD^ --hard 
    
# 바로 두번째 전 단계로 인덱스와 워킹트리를 버리고 리셋.
$ git reset HEAD~2 --hard 
    
# 특정 리비전의 기록으로 인덱스는 버리고 워킹트리를 보존하여 리셋.
$ git reset 991ee8c --mixed
```

----

#### 브랜치

- 브랜치는 한국말로 가지(branch)입니다.
- git에서는 마치 가지를 펼치듯 하나의 근본에서 여러 갈래로 쪼개어 관리할 수 있습니다.

 ![Git branch](http://www.pigno.se/static/assets/images/git_tutorial_branch.png)
 이미지 출처 [StackOverflow](http://stackoverflow.com/questions/23142731/push-a-feature-branch-to-develop-branch-using-git)


- branch의 특징은 아래와 같습니다.

 - 기본은 master 브랜치라고 불리며, 필수로 제공되는 브랜치이다.
 - 서로다른 브랜치들은 같은 조상을 가지고 있다.

- 브랜치를 새로 만드신다면 `git branch [브랜치명]`으로 생성합니다.
- 아래 명령라인에서는 new라는 브랜치를 생성하고 있습니다.

 ```bash
$ git branch new
```

- master 기준으로 new를 브랜치(가지치기)하면 master와 똑같은 소스코드가 new에도 적용됩니다.
- 하지만 이 이후로 new에서 코드를 수정하면, master와 new는 서로 다른 코드가 되기 때문에 갈라집니다.

- 생성된 new 브랜치로 접속하기 위해서는 `git checkout [브랜치명]`을 이용합니다.

 ```bash
$ git checkout new
```

 - 생성과정과 브랜치 이동과정을 동시에 하고자 하면 `git checkout`에 `-b` 옵션을 이용합니다.

 ```bash
# 브랜치 new를 생성과 동시에 체크아웃.
$ git checkout -b new
```

- 생성한 브랜치는 현재 로컬에 저장되어 있습니다.
- 협업 작업에서는 생성한 브랜치를 원격 저장소에 등록해주어야 합니다.
- 이때는 `git push [브랜치명]`을 이용합니다.

 ```bash
$ git push new
```

- 브랜치 생성 및 등록의 과정은 아래 화면과 같습니다.

 ![Git new branch](http://www.pigno.se/static/assets/images/git_tutorial_new_branch.png)

- 브랜치의 삭제는 `git branch` 명령에서 `-d` 옵션을 사용합니다.

 ![Git delete branch](http://www.pigno.se/static/assets/images/git_tutorial_delete_branch.png)

- 삭제된 브랜치 또한 원격 저장소에 반영을 해야합니다.
- 이때 브랜치 명 앞에 콜론(:)을 붙여주어야 하니 이 점 주의해주세요.

----

#### 깃 머지와 리베이스

- 브랜치를 사용하는 과정에서 가장 중요한 머지와 리베이스 등의 병합 기법입니다.
- 서로 다른 브랜치에서 서로 다른 코드가 개발되었고, 실제 배포에서 이를 합쳐야 할 때 사용합니다.
- 병합 방식에서는 크게 `git merge`와 `git rebase`가 존재합니다.
- 머지 방식과 리베이스 방식의 차이는 아래 이미지를 확인해주세요.

 ![Difference between merge and rebase](http://www.pigno.se/static/assets/images/git_tutorial_merge_rebase.png)
 
 이미지 출처 [http://git.mikeward.org/](http://git.mikeward.org/)

- 아래는 머지해야 하는 상황을 구현해봤습니다.
- `master`에서 `sub` branch가 생성되었으며, master 브랜치에서 sub 브랜치를 머지하고자 합니다.
- 파일 구성은 아래와 같습니다.

 ```plaintext
* master -> some_file.txt의 내용
* 1번째 단계 HEAD
I'm a file.
```

 ```plaintext
* sub -> some_file.txt의 내용
* 2번째 단계 HEAD (최신)
I'm a file.
    
Inserted new line from the sub branch.
```

- 자세한 부분은 해당 깃의 `Tutorial/Merge`를 참고해주세요.

 ```bash
$ git checkout -f master
$ git merge sub
# 현재 브랜치 master, 대상 브랜치 sub.
# master에서 sub를 머지합니다.
# HEAD -> master
# sub  -> sub
```

- 머지 이후 master에서 파일을 보면, 아래와 같은 내용을 얻습니다.

 ```plaintext
* merge 이후 master -> some_file.txt
I'm a file.
    
Inserted new line from the sub branch.
```

----

#### 충돌과 해결

- git으로 merge, rebase 수행시 충돌(conflict)가 발생 할 수 있습니다.
- 이는 같은 조상을 기준으로, 서로 다른 두개의 브랜치가 같은 소스코드를 변경했을 때 발생합니다.
- 아래는 샘플 환경입니다. `Tutorial/Conflict`를 참고해주세요.

 ```plaintext
* master -> some_file.txt의 내용
Apple
```

- 위는 `master` 브랜치의 some_file.txt의 내용이다.
- 아래는 해당 브랜치를 복제한 `sub` 브랜치이며, 복제 이후 한번 내용을 수정하였다.

 ```plaintext
* sub -> some_file.txt의 내용
* 2번째 단계 HEAD
Banana
```

- 이후 master에서도 내용을 변경하여 버전을 업데이트 합니다.
 
 ```plaintext
* master -> some_file.txt의 내용
* 2번째 단계 HEAD(sub랑 단계가 겹침)
Strawberry
```

- 둘 모두 버전이 같으나 같은 라인에서 변경사항이 발생했습니다.
- 이 경우 충돌이 발생합니다.
- 충돌이 발생한 some_file.txt를 열어보면 아래와 같은 내용을 보실 수 있습니다.

 ```plaintext
* 머지 이후 master -> some_file.txt (충돌)
<<<<<<< HEAD
Strawberry
=======
Banana
>>>>>>> sub
```

- 여기서 `HEAD`는 현재 브랜치(master)를 의미합니다.
- HEAD와 sub의 각각 내용을 보여주고 있는데 꺽쇠(<, >), 이퀄(=)기호가 없도록 문장 하나를 선택해서 반영해주어야
- 충돌이 해결 될 수 있습니다.
- 여기서는 `master` 브랜치의 Strawberry를 선택하여 충돌을 해결하겠습니다.

 ```plaintext
* 머지 이후 master -> some_file.txt (수정)
Strawberry
```

- 수정이 되었다면 머지 해결을 위해 `git add`와 `git commit`으로 충돌(conflict)을 해결하세요.

 ```bash
$ git add *
$ git commit -m "Solved the conflict issue."
```
