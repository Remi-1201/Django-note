## npmを使ったインストール

- npm installにはグローバルインストールとローカルインストールがあります。

```
npm install {パッケージ名}
npm i {パッケージ名}
npm add {パッケージ名}
```

### グローバルインストール

- グローバルインストールすると、PCのどのディレクトリからも使用できるようになります。
  - root配下にあるnode_modulesというディレクトリにパッケージがインストールされます。

```
npm install --global {パッケージ名}
npm install -g {パッケージ名}
```

### ローカルインストール

- ローカルインストールでインストールをすると、カレントディレクトリの中の`node_modules`にインストールされ、<br>
`package.json`の`dependencies`に記述されます。

```
npm install --save {パッケージ名}
npm install -S {パッケージ名}
```
>npm 5.0.0 以降からは、--saveオプションをつけなくてもデフォルトでカレントディレクトリにインストールするようになっています

### package.jsonのすべてのパッケージをインストール

```
npm install
```

## package.jsonとバージョン

- package.jsonは、パッケージの情報が記載されたファイルです。

- package.jsonが存在することによって、npmが管理できるパッケージ になります。

- package.jsonはnpm initコマンドで作成できます。

```
mkdir test-project //ディレクトリを作成
        
cd test-project  //ディレクトリに移動
 
npm init  //package.json の生成
```


- バージョン指定のパッケージインストール

```
npm install {パッケージ名}@バージョン

//例
npm install react-chartjs-2@3.3.0
```
