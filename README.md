# JupyterLab利用プロジェクトをGitで管理する:nbstripout編

[記事](https://zenn.dev/articles/e8fcb7aa4736f3) で試す内容のためのリポジトリ。

Pythonファイルやノートブックの内容は適当なサンプルとしてirisデータセットを読み込んでプロットするもの。
`src/` 配下には読み込みやプロット用の関数などが置かれており、ノートブックからはそれらを読み込んで利用する形。

## 環境ごとのセットアップ方法

注意: このリポジトリにpushしないようにしてください

### VSCode

1. このリポジトリをzipでダウンロードあるいはフォークしてクローンする
2. リポジトリのフォルダでVSCodeを開く
3. Reopen Folder in ...
4. ryeによって必要なライブラリがインストールされる

### Binder

Jupyter環境を試せるWebサービス、Binderを使って試す方法。

1. 次のリンク先を開く

### JupyterLabをDockerで起動

1. このリポジトリをzipでダウンロードあるいはフォークしてクローンする
2. `docker run -d -p 8888:8888 -v $(pwd):/work jupyter/minimal-notebook:2023-10-20` などでJupyterLabのサーバーを起動する
3. コンテナのログからトークンをコピーする
4. `localhost:8888` を開き、先程コピーしたトークンを入力してJupyter環境に入る
5. ランチャーからターミナルを開く
6. `conda env create --file environment.yml` を実行する
7. コンテナを再起動

データ分析によく使われるとされるので `conda` を利用する前提で進める。

## 試し方

`notebooks/` 配下のノートブックファイルを実行した後に保存し、コミットしようとしてみる、など。

## フォルダ構成

フォルダ・ファイルの利用方法想定は以下の通り。

- `.devcontainer`: VSCodeで開くときに利用するdevcontainer設定
- `notebooks/`: Jupyter Notebookファイルを格納
- `src/`: 再利用可能なPythonスクリプトを格納
- `data/`: 生データと前処理済みデータを格納
- `models/`: 訓練済みモデルを格納
- `reports/`: 分析レポートと生成されたグラフィックを格納
- `requirements-dev.lock`: rye用の依存関係を記述したファイル
- `requirements.lock`: rye用の依存関係を記述したファイル
- `environment.yml`: condaの依存関係を共有するためのファイル
- `pyproject.toml`: ryeの設定管理用
- `LICENSE`: ライセンス情報を記述したファイル
- `README.md`: プロジェクトの概要と使用方法を説明するドキュメント

実際モデルをGitにいれることがあるのかは知らない。
Git LFS使えば入れても良さそう。
