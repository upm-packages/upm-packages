---
layout: default
title: Use packages
nav_order: 1
parent: English
permalink: /en/usage
---

# Use packages

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Install packages

### 1. Search packages

Search for the package you want to use in [Unofficial Unity Package Manager Registry](https://upm-packages.dev).

### 2. Add ScopedRegistry settings to `Packages/manifest.json`

Access Unofficial Unity Package Manager Registry using the `scopedRegistry` scheme that Unity Package Manager supports independently.

And, specify the domain part of the package name you want to use in the `scopedRegistries.scopes` field.

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

To specify more than one, separate them with `,`.

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

### 3. Specify the packages in the `dependencies` field

Add the package name and the version you want to use in the form `"$package_name": "$version"`.

Be careful not to forget to add commas or add unnecessary commas to the end.

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

For preview packages, specify a suffix such as `-preview.1`.

## Update packages

If there is an update in the package, you can update from the Unity Package Manager UI.
