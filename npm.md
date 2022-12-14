この間はフロント開発を通してnpmを扱う機会が多くなりましたので、この記事ではnpmの基本概念とよく使うコマンドをまとめておきます。

---

- npm(Node Package Manager)とは、Node.jsのパッケージを管理するツール（パッケージマネージャ）です。
>Node.js とはサーバサイドで動く JavaScript のことです。

```
# Node.js のバージョン確認
node -v       
```
- npmのようなパッケージマネージャを使用することでパッケージのインストールや管理を行うことができます。
```
# npm のバージョン確認
npm -v     

# npm のアップデート
npm update -g npm
```
- package.jsonは、パッケージの情報が記載されたファイルであり、プロジェクト・フォルダーの配下にあります。

>  - package.jsonが存在することによって、npmが管理できるパッケージ になります。
>
>  - package.jsonは`npm init`コマンドで作成できます。

```
mkdir test-project //ディレクトリを作成
        
cd test-project  //ディレクトリに移動
 
npm init  //package.json の生成
```

- package.jsonの例

```package.json
{
  // 省略
  "dependencies": {
    "moment": "^2.29.1"
  },
  "devDependencies": {
    "eslint": "^7.23.0"
  }
}
```

## 1. npmを使ったインストール

- npm installにはグローバルインストールとローカルインストールがあります。

```
npm install {パッケージ名}

npm i {パッケージ名}

npm add {パッケージ名}
```

### 1.1 グローバルインストール

- グローバルインストールすると、PCのどのディレクトリからも使用できるようになります。
  - root配下にあるnode_modulesというディレクトリにパッケージがインストールされます。

```
npm install --global {パッケージ名}

npm install -g {パッケージ名}
```

### 1.2 ローカルインストール

- ローカルインストールでインストールをすると、カレントディレクトリの中の`node_modules`にインストールされ、`package.json`の<mark>dependencies</mark>に記述されます。

```
npm install --save {パッケージ名}

npm install -S {パッケージ名}
```
>npm 5.0.0 以降からは、--saveオプションをつけなくてもデフォルトでカレントディレクトリにインストールするようになっています

- `package.json` の <mark>devDependencies</mark> に追加するとき `--save-dev` (= `-D`)

```
npm install --save-dev <package>

npm install -D <package>
```

### 1.3 package.jsonのすべてのパッケージをインストール

```
npm install
```

### 1.4 パッケージ・インストールとバージョン指定

- バージョン指定のパッケージインストール

```
npm install {パッケージ名}@バージョン

//例
npm install react-chartjs-2@3.3.0
```

-  最新版を指定する場合
> @latest とつけなくても指定しなければ最新版がインストールされる

```
npm install {パッケージ名}@latest
```

## 2.npmとアップデート
- npm自体をアップデートする

```
npm update npm
```
- npmを使用してパッケージをアップデートする

```
npm update パッケージ名
npm up パッケージ名
npm update パッケージ名@バージョン
npm upgrade パッケージ名
```
- npmでグローバルのパッケージを更新する
```
npm update -g パッケージ名
```
- npmで複数パッケージを一括でアップデートする
```
npm update  パッケージ名 パッケージ名
```

---

## 3. 参考資料

- [DIVE INTO CODE - Webエンジニア ステップアップコース（Python）テキスト 【npmの機能と仕組み】](https://diver.diveintocode.jp/curriculums/2627)
- [Qiita - そろそろ適当に npm install するのを卒業する](https://qiita.com/sugurutakahashi12345/items/3cc49926faeaf25d3051)
- [TechAcademy - アップデートの方法！npm updateの使い方【初心者向け】](https://techacademy.jp/magazine/16146#ta-toc-5)
