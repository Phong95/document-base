---
sidebar_position: 1
---

# Cấu trúc

## Cấu trúc ứng dụng
Ứng dụng được cấu trúc 3 lớp:

- Frontend
- Backend
- Database

```mermaid
C4Deployment

    Boundary(mob1, "Frontend", ""){
        System(mobile, "Mobile App", "React Native", "aadf", "aaf")

            System(spa, "Single Page Application", "JavaScript and Angular", "")

    }



            Deployment_Node(apache, "Backend", ""){
                System(api, "API Application", ".Net", "")


            }
                        Deployment_Node(database, "Database", ""){
                                System(db2, "Database", "MySql, MongoDb", "")

            }

    Rel(mobile, api, "Makes API calls to", "json/HTTPS")
    Rel(spa, api, "Makes API calls to", "json/HTTPS")
    Rel(api, db2, "Reads from and writes to", "JDBC")

UpdateLayoutConfig($c4ShapeInRow="4", $c4BoundaryInRow="1")
UpdateRelStyle(mobile, api, $offsetX="-70", $offsetY="-30")
UpdateRelStyle(api, db2, $offsetX="-70", $offsetY="-30")
```



## Lưu đồ

Dưới đây là phương thức giao tiếp tổng quan cho toàn bộ ứng dụng **FMEz**

```mermaid
sequenceDiagram
autonumber
    box Ứng dụng phía khách hàng
    participant Ứng dụng
    end
    box Máy chủ
    participant Xác thực
    participant Tài nguyên
    end
    box Cơ sở dữ liệu
    participant MongoDb
    participant MySql
    end

    Ứng dụng->>Xác thực: Yêu cầu xác thực?
    Xác thực->>MySql: Kiểm tra?
    MySql-->>Xác thực: Đúng
    Xác thực-->>Ứng dụng: Token

    Ứng dụng->>Tài nguyên: Yêu cầu tài nguyên
    Note over Ứng dụng,Tài nguyên: Gửi kèm Token

    Tài nguyên->>MongoDb: Kiểm tra?
    MongoDb-->>Tài nguyên: Trả giá trị
    Tài nguyên-->>Ứng dụng: Trả giá trị
```

:::tip Thông tin chung

Tất cả các ứng dụng sẽ đều giao tiếp với máy chủ theo phương thức RestfulAPI, một số trường hợp đặc biệt như đẩy thông báo sẽ dùng giao tiếp khác sẽ được đề cập qua từng ứng dụng cụ thể.

:::
