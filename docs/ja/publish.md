---
layout: default
title: パッケージを登録する
nav_order: 2
parent: Japanese
permalink: /ja/publish
---

# パッケージを登録する

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 事前準備

### 1. GitHub Organizations の Member になる

レジストリの認証に [upm-packages](https://github.com/upm-packages) という GitHub Organizations の OAuth Application を用いているので、Organizations への Member 登録が必要になります。

[こちらのフォーム](https://forms.gle/2PKmKjcxeGpiZcYB8) より登録申請を行ってください。可能な限り早めに Member 登録を処理します。

### 2. Unofficial Unity Package Manager Registry にログインする

[Unofficial Unity Package Manager Registry](https://upm-packages.dev) の右上にある **ログイン** ボタンを押下し、 GitHub OAuth App の認証を行ってください。

### 3. 認証情報を `~/.npmrc` に保存する

![認証情報](/images/screenshots/auth_info.png)

画面上部に表示される認証情報をコピーし、 `~/.npmrc` の末尾に追記します。

## パッケージ登録

### 1. 通常の Unity プロジェクトとしてパッケージを開発する

原則的に Unity 2019.1.0f2 以降のバージョンでの開発を推奨しています。

開発するパッケージが Unofficial Unity Package Manager Registry で管理されている他のパッケージに依存していても問題ありません。

### 2. `.npmrc` を配置する

以下の内容を記した `.npmrc` をプロジェクトのルートディレクトリに配置します。

```rc
registry=https://upm-packages.dev
```

### 3. `package.json` を配置する

次に例示するような `package.json` を **`Assets/` 直下** に配置します。

```json
{
    "name": "dev.monry.upm.sample-package",
    "displayName": "Sample Package",
    "version": "1.0.0",
    "unity": "2019.1",
    "description": "Sample Package for Unofficial Unity Package Manager Registry",
    "author": {
        "name": "Tetsuya Mori",
        "url": "https://github.com/monry"
    },
    "license": {
        "type": "MIT",
        "url": "https://monry.mit-license.org"
    },
    "keywords": ["sample"],
    "category": "",
    "dependencies": {
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/monry/Sample-Package"
    }
}
```

次のフィールドは必須項目です。

* name
* displayName
* version

原則的に [package.json がサポートするフィールド](https://docs.npmjs.com/files/package.json) が利用可能です。

Unity Package Manager でインストールされた際のエラーを回避するために `package.json.meta` も生成されるように `package.json` を Unity Editor 上でインポートしておきましょう。

### 4. publish する

`npm` コマンドや `yarn` コマンドを用いてパッケージを Unofficial Unity Package Manager Registry に publish します。

```bash
npm publish Assets
```

```bash
yarn publish Assets
```

なお、パッケージの更新を行う際には、 `package.json` の `"version"` フィールドの値が変更されている必要があります。
