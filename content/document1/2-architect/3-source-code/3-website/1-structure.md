---
sidebar_position: 1
---

# 📂 Cấu trúc thư mục

Cấu trúc cho toàn bộ dự án

```
project
├── src
│   ├── app
|   |   ├── adapter
|   |   ├── components
|   |   ├── directive
|   |   ├── extensions
|   |   ├── models
|   |   ├── modules
|   |   ├── services
|   |   ├── theme
|   |   ├── app-routing.module.ts
|   |   ├── app.component.html
|   |   ├── app.component.scss
|   |   ├── app.component.ts
|   |   └── app.module.ts
│   ├── assets
|   |   ├── config
|   |   ├── i18n
|   |   ├── images
|   |   ├── js
|   |   └── styles
│   |── evironments
|   |   ├── environment.ts
|   |   └── environment.prod.ts
│   |── index.html
│   └── styles.scss
├── angular.json
├── package.json
├── README.md
```

Các file tĩnh tại thư mục `project/src/assets`.
Các mã nguồn phát triển tại thư mục `project/src/app`

## Service

Tất cả các service trong dự án.

```
services
├── admin
├── asset
├── auth
├── base
├── bim-model
└── ...

```

## Components

Tất cả các thành phần con cho giao diện người dùng.

```
components
├── asset
├── bim-model
├── client
├── department
├── document
└── ...
```

Cấu trúc bên trong thư mục được sắp xếp theo đối tượng trong ứng dụng. Ví dụ: asset, client, department, ...

## Model

Tất cả cấu trúc mô hình.

```
models
├── asset
├── client
├── department
├── global
├── language
└── ...
```

## Modules

Các module nhỏ được chia theo đối tượng

```
modules
├── asset
├── bim-model
├── calendar
├── client
├── iot
└── ...
```
