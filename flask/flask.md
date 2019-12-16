##### 191212(목)

### FLASK

> 파이썬 Flask로 웹서버 구동하기

 https://www.palletsprojects.com/p/flask/ 

- 자바 스프링 같은 프레임워크
- Django 프레임워크보다 가볍고 스케일이 작은 것부터 큰 것까지 만들 수 있음



```
1개의 REPOSITORY는 1개의 PROJECT로 나누는게 좋다
```



**git 초기화**

``git init``

**ignore 파일 생성**

``touch .gitignore``

**gitignore.io/ 에서 조회 후 .gitignore 파일에 추가**




```python
from flask import Flask, escape, request

app = Flask(__name__)

@app.route('/')
def hello():
    name = request.args.get("name", "World")
    return f'Hello, {escape(name)}!'
```

**git log --oneline** 커밋된 내용 확인

git diff 현재까지와의 차이점 확인



``templates`` 디렉토리 아래에 htmle 파일을 flask가 찾아서 동작할 예정



|                  구분                   | 리눅스 | 윈도우 |
| :-------------------------------------: | ------ | ------ |
| 현재의 디렉토리 파일 목록을 간단히 출력 | ls     | dir    |
|              환경변수 설정              | env    | set    |

```
http

| 요청 | 응답 | |

| 주문 | 커피 | get |

| 제출 | 계좌 | post |

get(가져오는 것) ex) 나 naver페이지 보여줄래? / 그래 html페이지 보여드림

post(처리하는 것) ex) 이것 좀 처리해줘  / 그래
```



  \# request.args => GET 형식으로 데이터가 들어온다면 사용

  \# request.form => POST 형식으로 데이터가 들어온다면 사용



___

BeautifulSoup 자바스크립트 이전부터

selenium은 자바스크립트 이후 수정 최종본부터

___

변수에 숫자가 포함되면 제대로 작동X  잘못

변수가 시작할 때 숫자면 안된다. // 끝날 때는 상관없다.

**return 값이 많아지면 dictionary에 담아서 그 dictionary만 return하면 편하다**

___

# Flask

> visual studio code로 flask 파일 열고 hello.py 파일을 만들어준다

```python
# 요청이 들어오면 return해준다
# 플라스크 모듈 안에서 import 4개 불러오기
from flask import Flask, escape, request, render_template
import random
from bs4 import BeautifulSoup
import requests
# 플라스크를 app이라는 변수에 저장
app = Flask(__name__)
# 밑에 있는 함수가 시작되기 전에 시작되는 부분
# /라는 요청이 들어오면 밑에있는 hello함수를 실행시키겠다
```

 https://www.palletsprojects.com/p/flask/  사이트에서 복사



```python
@app.route('/')
# /라는 것은 127.0.0.1:5000이 숨겨져 있다
```



### 예제1 'hi'

```python
@app.route('/hi')
# 127.0.0.1:5000/hi
def hi():
    return 'hi'
```

hi()는 hi라는 return 값을 가진 함수를 정의한다



### 예제2 'oh'

```python
@app.route('/oh')
# 127.0.0.1:5000/oh
def oh():
    return 'ohminjae'
```

oh()는 ohminjae라는 return 값을 가진 함수를 정의한다



### 예제3 '/html_file'

```python
@app.route('/html_file')
@app.route('/html_file')
def html_file():
    return render_template('index.html')
# render 만들다/되게 하다/세우다
```

html_file()는 index.html이라는 return 값을 가진 함수를 정의한다

**templates**라는 폴더를 생성하고 그 안에 index.html을 생성

**flask**가 **templates**내의 **html**파일을 찾아서 동작시킨다

```html
<body>
    <!-- li*4 tap 누르면 4개의 li tag가 생긴다. -->
    <li>소풍</li>
    <li>양자강</li>
    <li>시레기</li>
    <li>순두부</li>
    <!-- ol > li*4 tap 누르면 ol tag안에 li tag가 4개 생긴다 -->
    <!-- ol.abc > 1i*4 tap 누르면 abc 클래스 ol안에 li tag가 4개 생긴다 -->
</body>
```



### 예제4 '/variable'

```python
@app.route('/variable')
def variable():
    name = '오민재'
    return render_template('variable.html', html_name = name)
```

variable()는 variable.html이라는 값과 name값을 html_name으로 return한다

```html
<body>
    <!-- 파이썬 문법의 변수를 표시하는 방법 = 중괄호 두개 -->
    <!-- 플라스크에서 사용하는 jinja라는 문법 -->
    <h1>{{html_name}}님 안녕하세요</h1>
</body>
```

python으로부터 넘겨받는 값은 html 내에서 {{변수}} (중괄호 내에 작성) 사용한다



### 예제5 '/cube1'

```python
@app.route('/cube1/<int:num>/')
def cube1(num):
    num = num
    cube_num = num ** 3
    return render_template('cube1.html', num = num, cube_num = cube_num)
```

/cube/3

3의 3제곱은 27입니다.

**cube1.html을 리턴해주는게 render_template의 역할**

``** 지수를 표현 // 3의 4제곱 = 3 ** 4``

```html
<body>
    <h1>{{num}}의 세제곱은</h1>
    <h1>{{cube_num}}입니다.</h1>
</body>
```

python에서 완성된 변수를 받아와서 출력



### 예제6 '/movies'

```python
@app.route('/movies')
def movies():
    movies = ['겨울왕국2','쥬만지','해리포터']
    return render_template('movies.html', movies = movies)
```

movies 리스트를 만든다

```html
<body>
    <h1>현재 상영 영화 리스트</h1>
    <!-- 중괄호 안에 % 사이에 작성한다 -->
    <!-- jinja template는 중괄호# 부터 주석으로 인식 -->
    {#
        <!-- {% for문을 작성 %} -->
    #}
    {% for movie in movies %}
        {% if movie == '겨울왕국2' %}
            <li style = "color: blue">{{movie}}</li>
        {% else %}
            <li>{{movie}}</li>
        {% endif %}
    {% endfor %}
</body>
```

html 내에서 python의 for문 작성방법

``{% 여기서 작성 %}``

movie가 겨울왕국2와 같다면 style을 이용해 글자색을 파란색으로 바꾼다

html내에서 for문과 if문을 종료할 때는 **endfor**, **endif**를 써준다



### 에제7 '/ping', '/pong'

```python
@app.route('/ping')
def ping():
    return render_template('ping.html')

@app.route('/pong', methods = ['GET','POST'])
def pong():
    # request.args => GET 형식으로 데이터가 들어온다면 사용
    # request.form => POST 형식으로 데이터가 들어온다면 사용
    # print(request.form.get('keyword'))
    keyword = request.form.get('keyword')
    return render_template('pong.html', keyword = keyword)
```

ping.html에서 input받은 keyword **request.form.get('keyword')**

이것을 다시 keyword라는 변수에 저장 => pong.html에 return

```html
<body>
    <form action="/pong" method = "post">
        <input type="text" name="keyword">
        <input type="submit">
    </form>
</body>

<body>
    <h1>여기는 pong입니다.</h1>
    <h3>{{keyword}}를 입력했습니다.</h3>
</body>
```



### 에제8 '/naver'

> 네이버 대리검색

```python
@app.route('/naver')
def naver():
    return render_template('naver.html')
```

/naver 가 나오면 naver.html을 return해준다

```html
<body>
    <h1>네이버 대리검색</h1>
    <form action="https://search.naver.com/search.naver">
        <input type = "text" name = 'query'>
        <input type = "submit">
    </form>
</body>
```

form action에서 https://search.naver.com/search.naver 여기로

input 받은 query 이름의 text값을 보내준다

**ex) text type의 input값을 '도비'라고 한 후 submit 했을 경우**

**search.naver.com/search.naver?query=도비**



### 에제8 '/summoner', '/opgg'

> lol게임 소환사의 등급, 승 구하기

```python
@app.route('/summoner')
def summoner():
    return render_template('summoner.html')

@app.route('/opgg')
def opgg():
    # args.get('asdf') = keyerror 에러를 반영
    # args.get['asdf'] = None 값을 반영
    # args.get('asdf', '잘못된 접근입니다.') = 잘못된 정보면 잘못된 접근이라는 디폴트값 반영가능
    username = request.args.get('username')
    opgg_url = f"https://www.op.gg/summoner/userName={username}"

    response = requests.get(opgg_url).text
    soup = BeautifulSoup(response, 'html.parser')
    tier = soup.select_one('#SummonerLayoutContent > div.tabItem.Content.SummonerLayoutContent.summonerLayout-summary > div.SideContent > div.TierBox.Box > div > div.TierRankInfo > div.TierRank').text
    win = soup.select_one('#SummonerLayoutContent > div.tabItem.Content.SummonerLayoutContent.summonerLayout-summary > div.SideContent > div.TierBox.Box > div > div.TierRankInfo > div.TierInfo > span.WinLose > span.wins')
    return render_template('opgg.html', username = username, opgg_url = opgg_url, tier = tier, win = win.text.replace('W',''))
```

**/summoner 역할**

1. /summoner가 있으면 summoner.html을 return한다
2. summoner.html에서는 text 형태의 username 이름을 input 받아서 submit 했을 때 /opgg로 action한다

**/opgg 역할**

1. 

```html
<body>
    <h1>전적 검색</h1>
    <form action = '/opgg'>
        <input type = 'text' name = 'username'>
        <input type = 'submit'>
    </form>
</body>

<body>
    <h1>{{username}}님을 검색했습니다.</h1>
    {{opgg_url}}<br>
    티어는 {{tier}}이고, 승은 {{win}}승입니다.
</body>
```

