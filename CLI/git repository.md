### 191210

> **5OH-HO5.github.io reposittory**

git에서 (블로그 같은 역할) 알아서 인식하고 주소창에 치면 새 웹페이지에서 출력

1. **bootstrap template** 다운

2. 다운받은 파일 **resume** 으로 폴더이름 변경

3. gitignore.io에서 windows, visual studio code 등 추가


4. visual studio code로 열어서 gitignore 내용을 추가 저장

   (git bash에서 ``code .``하면 뜨긴 함)

5. 추가 후 visual studio code에서 아래내용 실행

```
 ctrl + shift + p 

 select default 

 git bash 선택

 ctrl + ` (백틱)

 ctrl + ` = git bash 켜짐 

 git bash 전에 화면은 휴지통 클릭으로 종료 가능

```

___

> FONT AWESOME

페이스북, 깃허브, 링크 아이콘

skills 창에 있는 아이콘도 수정 등

___

> 반응형 웹페이지

Bootstrap - layout - grid _ 12칸으로 나눈다

화면의 비율대로 조절할 수 있다.

___

bootstrap main page에서 css, js copy 적용

___

> 기능

bootstrap - components에서 'navbar'

bootstrap - components에서 'card'

___

> 색상

bootstrap - Utilities에서 'Colors'

#384fbd

> GITHUB

A/ github에서 new repository 'END TO END' create repository

settings - 왼쪽 Collaborators - 초대

B/ 등록된 이메일에서 수락



___

PC에서 해야할 일

CTRL + `(백틱)

GIT INIT

GITIGNORE 설정된 가정하

GIT ADD .

GIT STATUS

GIT COMMIT -M '끝말잇기 시작'

GIT ADD REMOTE



원격저장소에서 연결할 때 하는 일

GIT REMOTE ADD ORIGIN 원격저장소 주소

GIT PUSH ORIGIN MASTER

___

남의 원격저장소에 있는 정보 가져오기

CLONE ALL DOWNLOAD 주소 복사

GIT BASH 열기

CD DESKTOP/

GIT CLONE 그 주소

___

자료 수정 후 남의 원격저장소에 PUSH

push할 때 remote 안써도되는 이유

clone 해와서 필요없다 // 어디로 돌아갈지 지가 안다 똑똑



cd .. 뒤로가기

mkdir 폴더 만들기

___

데이터를 가져올 때는 PULL

origin 공간에서 master 가져와

git pull origin master 엄청나

___

> 두 개의 컴퓨터에서 서로 다른 commit 남겼을 때 충돌발생

pull할 때 잘 커밋하면 됨ㅋ

push할 때는



git log --oneline 커밋내역이 주르륵

___

깃허브 오픈소스에 기여하는 방법

콜라보레이터에 추가 안되어있으면 접근도 못함 찐따

반영하고 싶을 떄는 pull  requests해야됨



issues: ex) 토론 게시판 / 제안

pull requests: 이 코드 이렇게 수정했으면 좋겠다고 요청

___

오픈소스에 어필하기

오른쪽 상단 - Fork

포크된 정보 나한테 가져오기

= cd Desktop/

= git clone 가져올 주소


```
`남 repository

PR, Pull Requests

`yourAccount

PUSH

`Local
```

다시 git init하고 나의 repository에  push해준다

pull requests 누르면 어디서 어디로 보내줄지 확인하고 create requests해준다

