---
layout: default
title: Publish packages
nav_order: 2
parent: English
permalink: /en/publish
---

# Publish packages

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prepare

### 1. Become a Member of GitHub Organizations

We use [GitHub Organizations](https://github.com/upm-packages) OAuth Application for registry authentication
So, you need to register a member to Organizations.

Please apply for registration from [this form](https://forms.gle/2PKmKjcxeGpiZcYB8). Process Member registration as soon as possible.

### 2. Login to Unofficial Unity Package Manager Registry

Click the **Login** button at the top right of [Unofficial Unity Package Manager Registry](https://upm-packages.dev) to authenticate GitHub OAuth App.

### 3. Save authentication informations into `~/.npmrc`

![Authentication Informations](/images/screenshots/auth_info.png)

Copy the authentication information displayed at the top of the screen and append it to the end of `~/.npmrc`.

## Publish packages

### 1. Develop the package as a regular Unity project

In principle, development with Unity 2019.1.0f2 or later is recommended.

There is no problem if the package you develop depends on other packages managed by Unofficial Unity Package Manager Registry.

### 2. Put `.npmrc`

Put `.npmrc` with the following contents in the root directory of the project.

```rc
registry=https://upm-packages.dev
```

### 3. Put `package.json`

Put `package.json` likes following content under the `Assets/` directory.

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

The following fields are required.

* name
* displayName
* version

In principle [fields supported by package.json](https://docs.npmjs.com/files/package.json) are available.

Import `package.json` on Unity Editor so that `package.json.meta` is also generated to avoid errors when installed by Unity Package Manager.

### 4. Publish package

Publish package to Unofficial Unity Package Manager Registry using `npm` or `yarn` commands

#### `npm`

```bash
npm publish Assets
```

#### `yarn`

```bash
yarn publish Assets
```

Note: When updating a package, the value of the `"version"` field of `package.json` needs to be changed.
