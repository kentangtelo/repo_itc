# pembelajaran_itc
---

1. Install node v16.14.2 https://nodejs.org/en/blog/release/v16.14.2/
2. Jalankan perintah npm install
3. Buat database dengan nama "pembelajaran_itc"
4. Jalankan npx sequelize db:migrate
5. Jalankan npx sequelize-cli db:seed:all
6. Jalankan perintah npm run start


## Table of Contents

- [Pembelajaran_itc](#pembelajaran-itc)
  - [Table of Contents](#table-of-contents)
  - [User](#user)
    - [Register User](#register-user)
    - [Login User](#login-user)
    - [Fetch User](#fetch-user)
  - [Course](#course)
    - [Fetch All Courses](#fetch-all-courses)
    - [Store Course](#store-course)
    - [Modify Course](#modify-course)
    - [Delete Course](#delete-course)
  - [Division](#division)
    - [Fetch All Divisions](#fetch-all-divisions)
  - [Role](#role)
    - [Fetch All Roles](#fetch-all-roles)
---

## User

### Register User

Endpoint

```text
POST /user/register
```

Body

```json
{
    "username": "John",
    "fullName": "John Doe",
    "email": "johndoe@gmail.com",
    "password": "secret123",
    "id_division": 2
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully register user",
    "data": {
        "id": 1,
        "username": "John",
        "fullName": "John Doe",
        "email": "johndoe@gmail.com",
        "generation": null,
        "phoneNumber": null,
        "id_division": 2,
        "id_role": 1
    }
}
```

### Login User

Endpoint

```text
POST /user/login
```

Body

```json
{
    "emailUsername":"johndoe@gmail.com",
    "password": "secret123"
}
```

Response

```json
{
    "status": "success",
    "data": {
        "user": {
            "id": 1,
            "email": "johndoe@gmail.com",
            "username": "John",
            "fullName": "John Doe",
            "id_role": 1,
            "id_division": 2,
            "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MzUsImVtYWlsIjoiam9obmRvZUBnbWFpbC5jb20iLCJ1c2VybmFtZSI6IkpvaG4iLCJyb2xlIjoiVXNlciIsImRpdmlzaW9uIjoiRnJvbnQgRW5kIiwiaWF0IjoxNjY3NTkwOTMxLCJleHAiOjE2Njc1OTIxMzEsInN1YiI6IkpvaG4ifQ.INPm4rFWzXcy95yfoL_pF-HN52d4G2l0IEMppPWPlps"
        }
    }
}
```

### Fetch User

Endpoint

```text
GET /user/:id => /user/1
```

Response

```json
{
    "status": "success",
    "message": "Successfully get user by id",
    "data": {
        "id": 1,
        "username": "John",
        "fullName": "John Doe",
        "email": "johndoe@gmail.com",
        "generation": null,
        "phoneNumber": null,
        "id_division": 2,
        "id_role": 1
    }
}
```



---

## Course

### Fetch All Courses

Endpoint

```text
GET /course
```

Response

```json
{
    "status": "success",
    "message": "Successfully get all courses",
    "data": [
        {
            "id": 3,
            "title": "Lorem ipsum",
            "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
            "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654597/itc-repo/course/sgvgxlblqkis0yh5ikfq.jpg",
            "cloudinary_id": "sgvgxlblqkis0yh5ikfq",
            "createdAt": "2022-11-05T13:23:17.000Z",
            "updatedAt": "2022-11-05T13:23:17.000Z",
            "id_division": 2,
            "id_user": 2
        }
    ]
}
```

### Store Course

Endpoint

```text
POST /course
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1MzkzMCwiZXhwIjoxNjY3NjU1MTMwLCJzdWIiOiJKYW5lIn0.zKZfP9hJua9nYhAshczMTisL0mthOEds0uxMkww7ots",
            }
        ]
    },
    "body": {
        "mode": "formdata",
        "formdata": [
            {
                "key": "title",
                "value": "Lorem ipsum",
                "type": "text"
            },
            {
                "key": "description",
                "value": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
                "type": "text"
            },
            {
                "key": "image",
                "type": "file",
                "src": "/D:/Home/Pictures/test.jpg"
            },
            {
                "key": "id_division",
                "value": "2",
                "type": "text"
            },
            {
                "key": "id_user",
                "value": "2",
                "type": "text"
            },
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully create course",
    "data": {
        "id": 2,
        "title": "Lorem ipsum",
        "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
        "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654432/itc-repo/course/it7ejg37zr9br9advbxz.jpg",
        "cloudinary_id": "it7ejg37zr9br9advbxz",
        "id_division": 2,
        "id_user": 2,
        "updatedAt": "2022-11-05T13:20:33.206Z",
        "createdAt": "2022-11-05T13:20:33.206Z"
    }
}
```

### Modify Course

Endpoint

```text
PUT /course/:id => /course/2
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1NTE3NiwiZXhwIjoxNjY3NjU2Mzc2LCJzdWIiOiJKYW5lIn0.XH4xzH3xgb7yX9mZqobxEeRVr9Os6AxnFgA86EetAHw",
            }
        ]
    },
    "body": {
        "mode": "formdata",
        "formdata": [
            {
                "key": "title",
                "value": "Lorem ipsum edited",
                "type": "text"
            },
            {
                "key": "description",
                "value": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
                "type": "text"
            },
            {
                "key": "image",
                "type": "file",
                "src": "/D:/Home/Pictures/test.jpg"
            },
            {
                "key": "id_division",
                "value": "2",
                "type": "text"
            },
            {
                "key": "id_user",
                "value": "2",
                "type": "text"
            },
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully update course",
    "data": {
        "id": 2,
        "title": "Lorem ipsum edited",
        "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
        "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654432/itc-repo/course/it7ejg37zr9br9advbxz.jpg",
        "cloudinary_id": "it7ejg37zr9br9advbxz",
        "createdAt": "2022-11-05T13:20:33.000Z",
        "updatedAt": "2022-11-05T13:34:11.374Z",
        "id_division": 2,
        "id_user": 2
    }
}
```

### Delete Course

Endpoint

```text
DELETE /course/:id => /course/2
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1NTM3NCwiZXhwIjoxNjY3NjU2NTc0LCJzdWIiOiJKYW5lIn0.bthhCnOrZCgyv0SrC6UwniBou3Wf3K_JrG2Hq_5LSBc",
            }
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully delete course"
}
```

---

## Division

### Fetch All Divisions

Endpoint

```text
GET /division
```

Response

```json
{
    "status": "success",
    "message": "Successfully get division",
    "data": [
        {
            "id": 1,
            "divisionName": "Back End"
        },
        {
            "id": 2,
            "divisionName": "Front End"
        },
        {
            "id": 3,
            "divisionName": "Mobile"
        }
    ]
}
```

---

## Role

### Fetch All Roles

Endpoint

```text
GET /role
```

Response

```json
{
    "status": "success",
    "message": "Successfully get role",
    "data": [
        {
            "id": 1,
            "roleName": "User"
        },
        {
            "id": 2,
            "roleName": "Admin"
        }
    ]
}
```