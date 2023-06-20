# Docker-React
コマンドは、docker-compose.ymlが存在するディレクトリで実行する必要があります。

cdコマンドでディレクトリを移動しておいてください。

## イメージの構築
VERSIONの値には[dockerhubに公開されているタグ](https://hub.docker.com/_/node/tags)を記入してください。

最新バージョンの node.js を使用する場合は、`--build-arg` は不要です
```
docker-compose build --build-arg VERSION="node_version"
```

## create-react-appでプロジェクトを作成
```
docker-compose run --rm react sh -c 'yarn create react-app react-app'
```
また、typescriptで構築したい場合は以下のコマンドで実行してください。
```
yarn create react-app react-app --template typescript
```

## Viteでプロジェクトを作成
```
docker-compose run --rm react sh -c 'yarn create vite'
```
プロジェクト名や使用するテンプレートは、追加のコマンドラインオプションによって直接指定することもできます。
```
# npm 6.x
npm create vite@latest react-app --template react-ts

# npm 7+ は追加で 2 つのダッシュが必要:
npm create vite@latest react-app -- --template react-ts

# yarn
yarn create vite react-app --template react-ts

# pnpm
pnpm create vite react-app --template react-ts
```
サポートされている各テンプレートの詳細は [create-vite](https://github.com/vitejs/vite/tree/main/packages/create-vite) を参照してください: `vanilla`, `vanilla-ts`, `vue`, `vue-ts`, `react`, `react-ts`, `react-swc`, `react-swc-ts`, `preact`, `preact-ts`, `lit`, `lit-ts`, `svelte`, `svelte-ts.

## コンテナの作成と起動
```
docker-compose up -d
```

## 作成したプロジェクトをGitHubで管理する
```
# 管理したいプロジェクトのディレクトリへ移動
cd ./projects/react-app

# Gitリポジトリを作成
git init

# ファイルをステージングエリアに追加
git add .

# ステージングエリアの変更をコミット
git commit -m "first commit"

# ブランチの名前を変更
git branch -M main

# リモートリポジトリの接続を追加
git remote add origin https://github.com/****/*****.git

# ローカルの変更をリモートリポジトリにプッシュ
git push -u origin main
```
