---
layout: default
title: パッケージを利用する
nav_order: 1
parent: Japanese
permalink: /ja/usage
---

# パッケージを利用する

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## パッケージをインストールする

### 1. 利用したいパッケージを検索する

[Unofficial Unity Package Manager Registry](https://upm-packages.dev) にて利用したいパッケージを検索します。

### 2. `Packages/manifest.json` に ScopedRegistry の設定を追加する

Unity Package Manager が独自にサポートしている `scopedRegistry` の仕組みを利用して Unofficial Unity Package Manager Registry へアクセスします。

このとき、利用したいパッケージ名のドメイン部分を `scopedRegistries.scopes` フィールドに指定します。

```json
{
  "scopedRegistries": [
    {
      "name": "Unofficial Unity Package Manager Registry",
      "url": "https://upm-packages.dev",
      "scopes": [
        "dev.monry.upm"
      ]
    }
  ],
  "dependencies": {
    ...
  }
}
```

複数指定する場合は `,` で区切ります。

```json
{
  "scopedRegistries": [
    {
      "name": "Unofficial Unity Package Manager Registry",
      "url": "https://upm-packages.dev",
      "scopes": [
        "dev.monry.upm",
        "com.example.upm"
      ]
    }
  ],
  "dependencies": {
    ...
  }
}
```

### 3. `dependencies` フィールドにインストールしたいパッケージを指定する

利用したいパッケージ名と、バージョンを `"$package_name": "$version"` の形式で追加します。

このとき、カンマの付け忘れや、末尾への不要なカンマ追加をしないように気をつけましょう。

```json
{
  "scopedRegistries": [
    {
      "name": "Unofficial Unity Package Manager Registry",
      "url": "https://upm-packages.dev",
      "scopes": [
        "dev.monry.upm"
      ]
    }
  ],
  "dependencies": {
    ...
    "dev.monry.upm.sample-package": "1.0.0",
    ...
  }
}
```

プレビューパッケージの場合は、 `-preview.1` などのサフィックスまで指定しましょう。

## パッケージを更新する

パッケージに更新がある場合、Unity Package Manager の UI から更新が行えます。
