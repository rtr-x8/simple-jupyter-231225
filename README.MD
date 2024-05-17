Update!!

## install

```bash
gh repo clone rtr-x8/simple-jupyter-231225
cp .env.example .env
docker compose up -d --build
```

portを変更していなければ[localhost:8888](http://localhost:8888)で立ち上がる  
初回起動はおよそ1分ほど.

## add package

パッケージを新たに追加する際は以下のようにパッケージ管理ファイルを更新する。

```bash
docker compose exec simple_jupyter pip3 install xxx
docker compose exec simple_jupyter python3 -m pip freeze > ./.docker/python/requirements.txt
```

## update package

パッケージ管理ファイルを元にパッケージを更新する

```bash
docker compose exec simple-jupyter pip install -r ./.docker/python/requirements.txt
```

あるいはdockerをビルドし直しても良い。
```bash
docker compose up -d --build
```

## DEVS

localhostで立ち上がるのでブラウザからアクセスするのが楽。

Jetbrain intelijeで実行させる場合はPythonパッケージとJupyterパッケージを追加し、    
interpreterをdocker-composeにして接続する。

※jupter labのパスワードを求められた場合は入力せずにログインを数回クリックすればエラーが出るがアクセス可能。  
　パスワード無しで設定しているが入力を促されてしまう。

※ファイルの読み込みパスはdockerコンテナ内で実行するため「/app/」がルートとなる。