## npmを使ったインストール

- npm installにはグローバルインストールとローカルインストールがあります。

```
npm install {パッケージ名}
npm i {パッケージ名}
npm add {パッケージ名}
```
#### グローバルインストール

- グローバルインストールすると、PCのどのディレクトリからも使用できるようになります。
  - root配下にあるnode_modulesというディレクトリにパッケージがインストールされます。

```
npm install --global {パッケージ名}
npm install -g {パッケージ名}
```

#### ローカルインストール

- ローカルインストールでインストールをすると、カレントディレクトリの中の`node_modules`にインストールされ、<br>
`package.json`の`dependencies`に記述されます。

```
npm install --save {パッケージ名}
npm install -S {パッケージ名}
```
>npm 5.0.0 以降からは、--saveオプションをつけなくてもデフォルトでカレントディレクトリにインストールするようになっています

#### package.jsonのすべてのパッケージをインストール

```
npm install
```

