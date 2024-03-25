---
sidebar_position: 1
---
# 📂 Cấu trúc thư mục
Cấu trúc cho toàn bộ dự án
```
project
├── src
│   ├── api
│   ├── components
│   ├── context
│   ├── helper
│   ├── languages
│   ├── model
│   ├── navigation
│   ├── notifications
│   ├── redux
│   ├── scenario
│   ├── services
│   └── styles
├── assets
│   └── img
├── App.tsx
├── package.json
├── README.md
```
Các file tĩnh tại thư mục `project/assets`.
Các mã nguồn phát triển tại thư mục `project/src`

## api
Tất cả các service thực thi RestfulAPI.

```
api
├── HttpService.ts
├── AssetService.ts
├── AuthenticateService.ts
├── ClientsService.ts
├── CommentService.ts
└── ...

```


## components
Tất cả các thành phần con cho giao diện người dùng.

```
components
├── asset
├── client
├── department
├── global
├── language
└── ...
```
Cấu trúc bên trong thư mục được sắp xếp theo đối tượng page trong ứng dụng. Ví dụ: trang asset, trang client, trang department, ...

## context
Quản lý state của toàn bộ ứng dụng. 

``` typescript
export class GlobalComponentsState {
    openSnackbar!: (content: string, type?: SnackbarType, timeOut?: number) => void;
    showConfirmDialog!: (content: string, callBackOnSuccess?: () => void, callBackOnError?: () => void) => void
    setShowSpinner!: React.Dispatch<React.SetStateAction<boolean>>
    setClientsDialogVisibility!: React.Dispatch<React.SetStateAction<boolean>>
    setProjectsDialogVisibility!: React.Dispatch<React.SetStateAction<boolean>>
    setLanguageDialogVisibility!: React.Dispatch<React.SetStateAction<boolean>>
    setUpdateDialogVisibility!: React.Dispatch<React.SetStateAction<boolean>>
    setStatsDialogVisibility!: React.Dispatch<React.SetStateAction<boolean>>
    openImageViewer!: (urls: string[]) => void;
    selectImage!: (selectedCount: number) => Promise<void>;
    removeImage!: (index: number) => void;
}

```

## helper
Tất cả các phương thức hỗ trợ triển khai ứng dụng. Ví dụ: chỉnh ảnh,...

## languages
Đa ngôn ngữ.
```
languages
├── vi.json
├── en.json
└── ...
```
## model
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
## navigation
Quản lý điều hướng trong ứng dụng.
```
navigation
├── GlobalNavigationContainer.ts
├── GlobalStackNavigator.ts
├── HomeBottomTabsNavigator.ts
├── HomeCustomTabBar.ts
└── ...
```
## notifications
Quản lý thông báo từ firbase cloud messaging.
```
notifications
├── FirebaseNotification.ts
├── NotifeeNotification.ts
└── ...
```
## redux
Quản lý dữ liệu, vòng đời dữ liệu.
```
redux
├── actions
├── reducers
└── store
```
## scenario
Thực thi hành động theo ngữ cảnh cho trước.

## services
Tất cả dịch vụ khác không thuộc RestfulAPI (ví dụ: rxjs, signalR)

## styles
Style chung cho toàn bộ ứng dụng

