## GIT

### CONFIG 설정 (계정설정)

- 1 저장소 생성
```sh
mkdir myproject
cd myproject
git init
echo "# My Project" >> README.md
git add README.md
git commit -m "first commit"
```

- 2 계정 생성
```sh
- global : 별도 (local) 저장소별 계정 사용하지 않을경우 global 생략가능
git config --global user.name '사용자명' 
git config --global user.email '사용자이메일' 
```

```sh
- 저장소별 (local)계정 설정
git config --local user.name '사용자명'
git config --local user.email '사용자이메일'
```

- 3 저장소 연결
```sh
- dt-pricing
    git remote add origin https://oms-dev-scm.cloudzcp.io/dtp-common/oms-lib.git

    git push origin master 
```
### 브랜치(branch)

- 1 브랜치(branch) 생성
```sh
    git branch develop
    git checkout develop
or
    git checkout -b develop
```
>git checkout -b 브랜치 생성 후 이동

- 2 브랜치(branch) 원격저장소에 push
```sh
    git push origin develop
    git branch --set-upstream-to origin/develop
or
    git branch -u origin/develop
```
> -u 옵션은 --set-upstream-to 와 같다
```    
    결과 : Branch 'develop' set up to track remote branch 'develop' from 'origin'
```
- 3 브랜치(branch) 목록확인
```sh
    git branch -a 
```

- 4 브랜치(branch) 변경
```sh
    git checkout develop
```

- 5 브랜치(branch) 삭제
    - 1.1 Local Repository
    ```sh    
        git branch -d develop
    ```
    - 1.2 Remote Repository
    ```sh
        git push origin --delete develop
    ```

### GIT 사용하기
- 1 status : <br/>
    작업 디렉토리(working directory)와 스테이징 영역(staging area)의 상태를 확인
```sh
    git status
```
- 2 add : <br/>
    작업 위치(Working Directory 이하 WD) 폴더에 작업한 파일이 있을 경우 add를 통해서 staging Area로 옮길 수 있습니다. stagin Area는 commit을 진행하기 전의 임시 저장된 상태 정도로 생각하면 될 것 같습니다.
```
    git add <파일/디렉토리 경로>
    git add *
```

- 3 diff : <br/>
    HEAD와 워킹 디렉토리의 차이점을 보여주는 명령어
    - 3.1 로컬의 Branch간 비교
        ```sh
        git diff <branch명> <다른 branch명> 
        ```
    - 3.2 로컬과 리모트의 내용비교
        ```sh
        git diff <branch명> origin/<branch명>
        ```
    - 3.3 Commit 간 비교
        ```sh
        git diff <commit hash> <commit hash>
        ```
    - 3.4 pull request 내용과 비교<br/>
    (checkout remote branch 이름을 먼저 확인한 뒤)
        ```sh
        git diff <현재 브랜치> <checkout remote branch> 
        ```
    - 3.5 특정 커밋과 pull request 비교<br/>
    (heckout remote branch 이름을 먼저 확인한 뒤)
        ```sh
        git diff <현재 브랜치> <checkout remote branch> 
        ```
    - 3.6 마지막 커밋과 그 이전 커밋 비교
        ```sh
        git diff HEAD HEAD^ 
        ```
    - 3.7 마지막 커밋과 현재 수정사항 확인<br/>
    (아래 stage된 것과 아닌 것을 모두 확인하는 법이다. 주의 할 점은 untracking 파일은 비교에서 제외된다는 것이다.)
        ```sh
        git diff HEAD HEAD^ 
        ```
        - 3.7.1 현재 staged 된 수정사항 만 따로 확인
            ```sh
            git diff HEAD HEAD^ 
            ```
        - 3.7.2 현재 unstaged 된 수정사항만 확인
            ```sh
            git diff
            ```                     