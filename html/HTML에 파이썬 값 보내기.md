# HTML에 파이썬 값 보내기



- html과 파이썬 값 보내기

```python
from flask import Flask, render_template
import random

app = Flask(__name__)

@app.route("/")
def hello():
    return "<h1>서버가 heml도 보내주나?</h1>"
    
@app.route("/html_tag")
def html_tag():
    return """
    <h1>첫번째 줄!!</h1>
    <h2>두번째 줄</h2>
    """
    
@app.route("/html_file")
def html_file():
    return render_template("html_file.html")
    
@app.route("/welcome/<string:name>")
def welcome(name):
    return render_template("welcome.html", people=name)
    
@app.route("/cube/<int:num>")
def cube(num):
    triple = num*num*num
    return render_template("cube.html", triple=triple, num = num)
    
@app.route('/lunch')
def lunch():
    #요 부분에 점심메뉴를 추천해주는 코드를 작성!
    abc = ['참치찌개', '바나나', '삼겹살', '족발', '초밥']
    menu = random.choice(abc)
    return render_template("lunch.html", menu=menu)
    
@app.route('/lotto')
def lotto():
    #로또 난수
    pick = random.sample(range(1, 46), 6)
    sort_pick = sorted(pick)
    return render_template("lotto.html", sort_pick=sort_pick)
    
@app.route('/naver')
def naver():
    return render_template("naver.html")
    
@app.route('/google')
def gogoole():
    return render_template("google.html")
    
```

```html
<h1>{{num}}의 세제곱값은 {{triple}}입니다.</h1>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <form  action="https://www.google.com/search">
        <input type="text" name="q"/>
        <input type="submit" value="Submit"/>
    </form>
</body>
</html>
```

