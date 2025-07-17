### 7/17 수업 


**Remote Repository  (원격 저장소)** 

다양한 원격 저장소 서비스 

⇒ GitLab /GitHub /Bitbucket

### 로컬 & 원격 저장소

### git remote

git remote add origin(추가하는 원격 저장소 별칭) remote_repo_url(추가하는 원격 저장소 주소)

로컬 저장소에 원격 저장소 추가 

별칭을 사용해 로컬 저장소 한 개에 여러 원격 저장소를 추가 할 수 있음. 

**깃허브에서 레포지토리 만들 때,**

**Initialize this repository with ⇒ 로컬에서 init 했으면 체크하면 안된다!!** 

별칭을 사용해 로컬 저장소 한 개에 여러 원격 저장소를 추가 할 수 있음.

(일단 remote는 연결만 해놓는거지 동기화 하는게 아님)

### git push

git push origin master 

원격 저장소에 commit 목록을 업로드 

(오리진이라는 이름의 원격 저장소에 마스터라는 이름의 브랜치를 푸쉬해줘)

+) 최초 push시에는 GitHub으로부터 인증서(git credential) 발급이 필요

+) 해당 원격 저장소에 push 할 수 있는 권한이 있는지 확인하기 위해서 

![image.png](attachment:b9ffe47a-35c7-40cb-a79a-d1e203528ff5:image.png)

git pull origin master : 원격 저장소의 변경사항만을 받아옴(업데이트) ⇒ 로컬 100개 (clone)

git clone remote_repo_url

(원격 저장소 전체를 복제 (다운로드) 

**+)clone으로 받은 프로젝트는 이미  git init이 되어있음** 

### git ignore

Git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는데 사용되는 텍스트 파일

프로젝트에 따라서 공유하지 않아야 하는 것들도 존재하기 때문 

**⇒ git ignore 예시**

.gitignore 파일 생성 (파일 명 앞에 . 생성, 확장자 없음)

그리고 그 안에 무시 해야 하는 파일을 넣으면 된다

하지만 이미  git의 관리를 받은 이력이 있는 파일이나 디렉토리는 나중에 gitignore에 작성해도 적용되지 않는다.

(git rm —cached 명령어를 통해 git 캐시에서 삭제가 필요함) 

[gitignore.io](http://gitignore.io) 사이트를 통해서 깃이그노어 파일 생성해주는 거 있음

GitHub(깃허브)  :  (포트폴리오용으로 일단 젤 많이 쓰고)

1. 프로젝트 협업
2. 개인 포트폴리오

 

GitHub 활용하기

- TIL을 통해 내가 학습하는 것을 기록
- 개인, 팀 프로젝트 코드를 공유 ⇒ 개발 면접 지원 시, 본인의 GitHub 주소를 공유해 어떤 프로젝트들을 진행했고, 어떤 코드를 작성했는지 공유하고 평가 받기 위해 사용
- 오픈 소스 프로젝트에 기여

**README.md 파일?**

프로젝트에 대한 설명, 사용 방법, 문서화 된 정보 등을 포함하는 역할

Markdown 형식으로 작성되며, 프로젝트의 사용자, 개발자, 혹은 기여자들에게 프로젝트에 대한 전반적인 이해와 활용 방법을 제공하는데 사용 

주로 프로젝트의 소개, 설치 및 설정 방법, 사용 예시, 라이선스 정보, 기여 방법 등을 포함

반드시 저장소 최상단에 위치해야 원격 저장소에서 올바르게 출력됨.

**git 기타 명령어**

- **git remote -v :** 현재 로컬 저장소에 등록된 원격 저장소 목록 보기
- **git remote rm 원격_저장소_이름 :** 현재 로컬 저장소에 등록된 원격 저장소 삭제

### Git Revert / Git reset

**git revert :** 특정 commit을 없었던 일로 만드는 작업

**git revert <commit id(커밋 해시 아이디)>** : revert 명령어 

“재설정”, 단일 커밋을 실행 취소 하는 것

프로젝트 기록에서 commit을 없었던 일로 처리 후 그 결과를 새로운 commit으로 추가함

![image.png](attachment:656c9ca7-7430-4c85-85a5-8a20c378b035:image.png)

그러니까 이 커밋을 없앴다는 것도 역사로 남기겠다는거지 (기록에서 커밋이 사라지지는 않음) 

**리버트 명령어 쓰고, 열린 콘솔창을 :wq로 끄고 나오면 끝!**

**Git revert 정리** 

- 변경 사항을 안전하게 실행 취소할 수 있도록 도와주는 순방향 실행 취소 작업
- commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit을 생성
- git에서 기록이 손실되는 것을 방지하며 기록의 무결성과 협업의 신뢰성을 높임

**revert 추가 명령어** 

- 공백을 사용해 여러 commit을 한꺼번에 실행 취소 가능
- `  ..  `을 사용해 범위를 지정하여 여러 커밋을 한꺼번에 실행 취소 가능
- commit 메시지 작성을 위한 편집기를 열지 않음  (—no-edit)
- 자동으로 commit하지 않고, Staging Area에만 올림(이후에 직접 커밋해야함) 대신 이 기능은 여러 커밋을 revert 할 때 하나의 커밋으로 묶는 것이 가능 (—no-commit)

**git reset :** 특정 commit으로 되돌아가는 작업

**git reset [옵션] <commit id>**

![image.png](attachment:776a716b-e858-4a05-8ddb-67995465d4a4:image.png)

**reset의 3가지 옵션**

**—soft, —mixed, —hard**

reset은 과거 commit으로 되돌아간 후 되돌아간 commit 이후 commit들이 삭제됨

그런데 삭제되는 commit들의 기록을 어떤 영역에 남겨둘 것인지 옵션을 활용해 조정할 수 있음

**— soft : 삭제된 commit의 기록을 staging area에 남김**

**—mixed : 삭제된 commit의 기록을 working directory에 남김 (기본 옵션 값)**

**— hard : 삭제된 commit의 기록을 남기지 않음** 

![image.png](attachment:1cb6f5da-daaf-49c7-a0b5-f1394f04a46e:image.png)

이미 삭제한 commit으로 다시 돌아가고 싶다면?

**git reflog**

- HEAD가 이전에 가리켰던 모든 commit을 보여줌
- reset의 —hard 옵션을 통해 지워진 commit도 reflog로 조회하여 복구 가능

**파일 내용을 수정 전으로 되돌리기** 

**git restore** : Modified 상태의 파일 되돌리기

- working Directory에서 파일을 수정한 뒤, 파일의 수정 사항을 취소하고, 원래 모습대로 되돌리는 작업

 **restore 주의사항**

원래 파일로 덮어쓰는 원리이기 때문에 수정한 내용은 전부 사라짐

git restore를 통해 수정 취소 후에는 해당 내용을 복원할 수 없음 

**Staging area에 올라간 파일을 Unstage하기**

Unstage 하는 명령어 

1. **git rm —cached**
2. **git restore —staged**

**명령어 간 차이 : Commit 존재 여부에 대한 차이** 

**git rm —cached** : Staging Area에서 Working Directory로 되돌리기 

⇒ **git 저장소에 “commit”이 없는 경우**

to unstage and remove paths only from the staging area

**git rm —staged** : Staging Area에서 Working Directory로 되돌리기 

⇒ **git 저장소에 “commit”이 존재하는 경우** 

the contents are restored from HEAD