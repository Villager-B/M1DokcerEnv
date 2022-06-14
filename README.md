# M1 Docker env

M1 Dockerの荒波を乗り越えてPythonでの分析環境を簡易的に作成することができるリポジトリ

## 特徴

- M1対応
  - ベースイメージはUbuntu20.04
- Python 3.9.6
- Jupyter lab使用可能状態
  - port 9022
- matplotlib + seabornの日本語対応
  - pandas_profilingもいけます
- ビルド時間は長め
  - M1 macbook airで1900s
  - 1回目の立ち上げは我慢

## 手順

リポジトリをダウンロードしたら`docoker-compose.yml`を一部編集し，`docker-compose up`するだけ．

### docker-compose.ymlの編集

8，9行目の内容を各自のディレクトリ名で修正する．

8行目の`"/Users/shimasan/Documents/:/home/work"`は左側の`/Users/shimasan/Documents/`を自分の作業ディレクトリ名に変える．

9行目は元々jupyter設定を持っている人用なので基本的には削除して良い．

```yaml
    volumes:
      - "/Users/shimasan/Documents/:/home/work"
      - "/Users/shimasan/.jupyter:/root/.jupyter"
```

### コンテナ立ち上げ

ダウンロードしたリポジトリ上で以下のコマンドを実行すればよい．

```bash
docker-compose up
```

以下のURLにアクセスすればJupyter Labが使用できる．

```bash
localhost:9022
```

## Option

### Altairで画像保存したい人

```bash
pip install webdrivermanager
webdrivermanager firefox --linkpath /usr/local/bin
apt -y update
apt -y install firefox firefox-locale-ja
```

### matplotlib+seabornで日本語化

```python
import matplotlib.pyplot as plt
import japanize_matplotlib
import seaborn as sns
sns.set(font="IPAexGothic")
```

pandas_profilingも日本語化されていることが確認できます．