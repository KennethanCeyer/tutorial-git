# Tutorial GIT


### 어떻게 깃을 사용하는지 빠르게 알아봅시다.
> Quick learn How to use the Git.

### 시작하며

##### 깃을 왜 사용하죠?

- 빠른 협업환경 조성
- 누가 언제 무엇을 왜 수정했는지 코드리뷰가 가능
- IssueTracker 및 Migrate 지원
- GitHub를 이용하여 자신의 git을 쉽게 전파, 공유가 가능
- Continuous Integration (지속적인 통합) 지원
- VisualStudio, Eclipse, Android Studio 등 많은 부분에서 Git연동 제공

- **결국 대게는 협업을 위해서 사용**

##### 깃이 어떤 역할을 하는건가요?

- 소스 병합
- 소스 리비전 관리
- 소스 배포
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

- 깃은 초기에 `git init` 작업을 진행합니다
- 혹여나 GitHub에서 클론을 받은경우 이 작업은 필요하지 않습니다.
- 아래 샘플 코드를 확인해주세요.

 ```shell
    git init
```
- `git init`을 하셨으면 Git 리모트를 설정하실 수 있습니다.
- Git 리모트란 Git을 원격저장소에 저장하는 앤드포인트를 의미합니다.

 ```shell
   git remote add origin https://github.com/KennethanCeyer/tutorial.git
```

- 깃의 리모트 URL을 이용하여 원격저장소에 저장된 파일을 컴퓨터로 복사해올 수 있습니다.
- 이때 `git clone`을 사용하여 복사를 시작합니다.

 ```shell
    git clone https://github.com/KennethanCeyer/tutorial.git
```

 - `git clone`을 통해 원격파일을 복사해오면, origin에는 기본적으로 클론해온 리모트 URL이 저장되있습니다.

----

#### 소스 기록, 업로드

- 소스를 업로드 하기 위해서는 `git add` 명령어를 이용합니다.
- 샘플을 참고하세요

 ```shell
    git add *
```

- ignore 파일이나, 삭제한 파일 이력까지 커밋을 하실 경우, `-f` 옵션을 이용합니다.

 ```shell
    git add * -f
```

- `git remote show origin`을 통해 origin에 리모트 주소가 잘 등록되었는지 확인해보세요.

 ![Refer2](http://www.nhpcw.com/upload/2016-01-06%2B12%253B06%253B22_010616120718.PNG)

----

#### 소스 커밋, 메시지 작성

- 소스를 커밋하시면 `Tracked` 상태에서 `Stage` 상태로 변경됩니다.
- 파일 추적상태의 경우 `git status` 명령을 이용해서 확인합니다.

 ```shell
    git status
 ```

- `git add` 이후 `git status`를 하면 아래와 같은 화면이 나옵니다.

 ![Refer01](http://www.nhpcw.com/upload/2016-01-06%2B11%253B59%253B51_010616120036.PNG)

- Stage 상태의 파일은 아직 기록된 상태가 아닙니다.
- 파일의 기록을 위해서는 `커밋` 작업이 필요합니다.
- `git commit` 명령을 통해 Stage 상태의 파일을 커밋할 수 있습니다.

 ```shell
    git commit -m "커밋 메시지를 적으시면 됩니다."
```

- `-m` 옵션을 이용하여 커밋 메시지를 작성하는 것을 권장합니다.
- 실수로 커밋을 하여, 다시 커밋을 할 경우 커밋을 덮어씌울 수 있습니다. 이때 `--amend` 옵션을 이용합니다.

 ```shell
    git add *
    git commit -m "UI 레이아웃 이슈 수정."
    
    // 수정사항 발생
    git add *
    git commit -m "UI 레이아웃 이슈 수정 및 관리자 벨리데이션 추가." --amend
```

----

#### 소스의 복원, 리셋

- 여러분이 git을 쓰는 이유중에 중요한 부분을 차지하는 영역입니다.
- 정상적으로 커밋된 히스토리는, 리비전으로 git에 관리됩니다.
- 실수로 잘못 작업하였거나, 예전 버전으로 롤백하여 적용할 경우 여러분은 예전 버전으로 리셋하실 수 있습니다.
- 리셋은 `git reset` 명령을 사용합니다.

 ```shell
    git reset HEAD^ --soft
```

- `git reset` 다음 인수로는 되돌리는 버전의 위치를 가리킵니다.
- 현재위치(HEAD)를 기준하여 상대적인 위치를 설정하거나, 특정 버전 리비전 고유의 해시값을 지정합니다.
- HEAD를 확인하시고 싶으면 `git reflog` 명령을 이용합니다.

 ![Refer3](http://www.nhpcw.com/upload/2016-01-06%2B12%253B16%253B32_010616121637.PNG)

- `git reset`의 옵션 중 리셋 특성을 정하는 `--soft, --hard, --mixed` 옵션이 있습니다.
- 위 옵션은 아래에서 자세히 설명합니다.

 - `--soft`는 약한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 보존합니다.
 - `--hard`는 강한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 버립니다.
 - `--mixed`는 중간특성의 리셋입니다, 되돌릴 때 기존의 인덱스는 버리고 워킹트리를 보존합니다.

- 되돌리는 위치의 경우 아래와 같은 타입이 있습니다.

 ```shell
    // 바로 이전 단계로 인덱스와 워킹트리를 버리고 리셋.
    git reset HEAD^ --hard 
    
    // 바로 두번째 전 단계로 인덱스와 워킹트리를 버리고 리셋.
    git reset HEAD~2 --hard 
    
    // 특정 리비전의 기록으로 인덱스는 버리고 워킹트리를 보존하여 리셋.
    git reset 991ee8c --mixed
```
