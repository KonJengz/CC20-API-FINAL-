![ERD](./pic//prisma-erd.svg)

# 🏥 Health Tracker API Documentation

## 📑 API Endpoints Summary

| Method             | Endpoint                     | Description                       | Access | Score |
| ------------------ | ---------------------------- | --------------------------------- | ------ | ----- |
| **Authentication** |                              |                                   |        |       |
| [x] POST           | `/auth/register/doctor`      | ลงทะเบียนแพทย์                    | Public | 10    |
| [] POST            | `/auth/register/user`        | ลงทะเบียนผู้ป่วย                  | Public | 10    |
| [] POST            | `/auth/login`                | เข้าสู่ระบบ                       | Public | 10    |
| **Users**          |                              |                                   |        |
| [] GET             | `/users/me`                  | ดูข้อมูลตัวเอง                    | User   | 5+5   |
| [] PATCH           | `/users/me`                  | แก้ไขข้อมูลตัวเอง                 | User   | 5+5   |
| **Doctor**         |                              |                                   |        |
| [] GET             | `/doctors/me`                | ดูข้อมูลตัวเอง                    | Doctor | 5+5   |
| [] PATCH           | `/doctors/me`                | แก้ไขข้อมูลตัวเอง                 | Doctor | 5+5   |
| **Health Records** |                              |                                   |        |
| [] POST            | `/health-records`            | สร้างบันทึกสุขภาพ                 | User   | 5+5   |
| [] GET             | `/health-records`            | ดูบันทึกสุขภาพทั้งหมด             | User   | 5+5   |
| [] GET             | `/health-records/:id`        | ดูบันทึกสุขภาพเฉพาะ               | User   | 5+5   |
| [] PATCH           | `/health-records/:id`        | แก้ไขบันทึกสุขภาพ                 | User   | 5+5   |
| [] DELETE          | `/health-records/:id`        | ลบบันทึกสุขภาพ                    | User   | 5+5   |
| **Doctor Notes**   |                              |                                   |        |
| [] POST            | `/doctor-notes`              | สร้างบันทึกให้ผู้ป่วย             | Doctor | 5+5   |
| [] GET             | `/doctor-notes/my-notes`     | ดูบันทึกที่เขียนทั้งหมด           | Doctor | 5+5   |
| [] GET             | `/doctor-notes/user/:userId` | ดูบันทึกที่เขียนให้ผู้ป่วยคนหนึ่ง | Doctor | 5+5   |
| [] GET             | `/doctor-notes/received`     | ดูบันทึกที่ได้รับจากหมอ           | User   | 5+5   |
| [] PATCH           | `/doctor-notes/:id`          | แก้ไขบันทึก                       | Doctor | 5+5   |
| [] DELETE          | `/doctor-notes/:id`          | ลบบันทึก                          | Doctor | 5+5   |

## Other Marks

Error Middleware 5 Marks

NotFound Middleware 5 Marks

Prisma Schema 10 Marks

## 📝 Notes

1. ทุก protected route ต้องส่ง token ใน header:
   ```
   Authorization: Bearer <token>
   ```
2. Error responses จะมี HTTP status code ที่เหมาะสม
