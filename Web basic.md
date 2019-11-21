运用Flask框架开发Pythoy最基础web
```python
from flask import Flask
from flask import request

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def home():
    return '<h1>Home</h1>'

@app.route('/signin', methods=['GET'])
def signin_form():
    return '''<form action="/signin" method="post">
              <p><input name="username"></p>
              <p><input name="password" type="password"></p>
              <p><button type="submit">Sign In</button></p>
              </form>'''

@app.route('/signin', methods=['POST'])
def signin():
    # 需要从request对象读取表单内容：
    if request.form['username']=='admin' and request.form['password']=='password':
        return '<h3>Hello, admin!</h3>'
    return '<h3>Bad username or password.</h3>'

if __name__ == '__main__':
    app.run()
```

运行`python app.py`，Flask自带的Server在端口5000上监听：
```
$ python app.py 
 * Running on http://127.0.0.1:5000/
 ```
 
 详细参考廖雪峰老师Python教程：
 https://www.liaoxuefeng.com/wiki/1016959663602400/1017806472608512
