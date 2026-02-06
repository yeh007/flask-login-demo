# flask-login-demo

Codespace實作，網頁登入，python，顯示 hello world

好的，我來示範如何在 GitHub Codespaces 中，用 Python + Flask 建立一個簡單的「網頁登入 → 顯示 Hello World」範例。
步驟流程
1. 建立 Repository

    在 GitHub 建立一個新倉庫，例如：flask-login-demo。

    啟動 Codespace，進入雲端開發環境。

2. 建立環境需求

在倉庫中新增 requirements.txt：
程式碼

flask

然後在 Codespace Terminal 安裝：
bash

pip install -r requirements.txt

3. 建立 Flask 應用程式

建立 app.py：
python

from flask import Flask, render_template, request, redirect, url_for

app = Flask(__name__)

# 模擬帳號密碼
USERNAME = "admin"
PASSWORD = "1234"

@app.route('/')
def home():
    return redirect(url_for('login'))

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        user = request.form['username']
        pwd = request.form['password']
        if user == USERNAME and pwd == PASSWORD:
            return redirect(url_for('hello'))
        else:
            return "登入失敗，請重試！"
    return '''
        <form method="post">
            使用者名稱: <input type="text" name="username"><br>
            密碼: <input type="password" name="password"><br>
            <input type="submit" value="登入">
        </form>
    '''

@app.route('/hello')
def hello():
    return "Hello World!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8000)

4. 啟動伺服器

在 Codespace Terminal 執行：
bash

python app.py

    預設會在 http://localhost:8000 提供服務。

    在 Codespaces 的 Port 面板中，將 8000 設為 Public，就能在瀏覽器打開。

5. 測試流程

    打開瀏覽器 → 進入 https://<你的-codespace-URL>/login。

    輸入帳號 admin、密碼 1234。

    登入成功後，會跳轉到 /hello，顯示：

程式碼

Hello World!

小結

這樣你就在 Codespaces 中完成了一個最簡單的「登入 → Hello World」網頁應用。
它的特色是：

    快速啟動：不用安裝本地環境。

    一致性：團隊成員都能用同樣的設定。

    可擴充：之後可以加上 Session、資料庫、或 OAuth 登入。

要不要我幫你把這個流程畫成一個 架構圖 (Architecture Diagram)，讓你更直觀地看到「瀏覽器 → Flask → 驗證 → Hello World」的流程？ 



    
