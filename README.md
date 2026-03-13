# Task Board - N-Tier Architecture with Docker

## 📋 ภาพรวมโครงการ

เว็บแอปจัดการงาน (Task Board) ที่ใช้ **N-Tier Architecture** และ **Docker** สำหรับวิชา ENGCE301 สัปดาห์ที่ 6

### 🏗️ โครงสร้าง 4 ชั้น

1. **Database Layer** - PostgreSQL เก็บข้อมูลงาน
2. **API Layer** - Node.js/Express จัดการข้อมูล (แบ่ง 3 ชั้นย่อย)
3. **Web Server Layer** - Nginx ทำ reverse proxy + SSL
4. **Frontend Layer** - HTML/CSS/JavaScript หน้าเว็บ

## ✨ ฟีเจอร์หลัก

- ✅ สร้าง/แก้ไข/ลบ งาน
- 📊 ติดตามสถานะ (TODO, IN_PROGRESS, DONE)
- 🎯 จัดลำดับความสำคัญ (LOW, MEDIUM, HIGH)
- 📈 ดูสถิติการใช้งาน
- 🐳 ใช้งานผ่าน Docker ทั้งระบบ

## 🛠️ เทคโนโลยี

- **Backend**: Node.js + Express + PostgreSQL
- **Frontend**: HTML + CSS + JavaScript
- **Infrastructure**: Docker + Docker Compose + Nginx

## 🚀 การใช้งาน

### เริ่มต้นใช้งาน

```bash
# เริ่มระบบ
docker compose up -d

# ตรวจสอบสถานะ
docker compose ps

# เปิดใช้งาน
https://localhost
```

### คำสั่งที่ใช้บ่อย

```bash
# ดู log
docker compose logs -f

# หยุดระบบ
docker compose down

# รีสตาร์ท
docker compose restart
```

## 📁 โครงสร้างโฟลเดอร์

```
term-project-week6/
├── api/                    # Backend API
│   ├── src/
│   │   ├── controllers/    # จัดการ HTTP requests
│   │   ├── services/       # Business logic
│   │   └── repositories/   # Database operations
│   └── Dockerfile
├── database/               # PostgreSQL
│   └── init.sql           # สร้างตารางและข้อมูลตัวอย่าง
├── nginx/                 # Web server
│   ├── nginx.conf         # ตั้งค่าหลัก
│   └── conf.d/            # ตั้งค่าเว็บไซต์
├── frontend/              # Frontend
│   ├── index.html         # หน้าเว็บหลัก
│   ├── css/               # ไฟล์ CSS
│   └── js/                # ไฟล์ JavaScript
├── scripts/               # สคริปต์ช่วยงาน
└── docker-compose.yml     # จัดการ containers
```

## 🔧 การตั้งค่า

### สิ่งที่ต้องมี

- Docker
- Docker Compose

### การตั้งค่าเริ่มต้น

ระบบใช้ค่าเริ่มต้นที่พร้อมใช้งานได้ทันที:

- **Database**: PostgreSQL (port 5432)
- **API**: Node.js (port 3000)
- **Web**: Nginx (port 443)

## 📊 API Endpoints

- `GET /api/tasks` - ดูทุกงาน
- `POST /api/tasks` - สร้างงานใหม่
- `PUT /api/tasks/:id` - แก้ไขงาน
- `DELETE /api/tasks/:id` - ลบงาน
- `GET /api/tasks/stats` - ดูสถิติ

## 🐳 Docker Services

| Service | Container | Port | หน้าที่ |
|---------|-----------|------|---------|
| db | taskboard-db | 5432 | ฐานข้อมูล |
| api | taskboard-api | 3000 | Backend API |
| nginx | taskboard-nginx | 443 | Web server |

## 📝 สถานะงาน

- **TODO** (📝) - ยังไม่ได้ทำ
- **IN_PROGRESS** (🔄) - กำลังทำ
- **DONE** (✅) - เสร็จสิ้น

## 🎯 ลำดับความสำคัญ

- **LOW** (🟢) - สำคัญน้อย
- **MEDIUM** (🟡) - สำคัญปานกลาง
- **HIGH** (🔴) - สำคัญมาก

## 🛡️ ความปลอดภัย

- ใช้ HTTPS โดยอัตโนมัติ
- Non-root containers
- CORS configuration
- SSL/TLS encryption

## 📈 การพัฒนา

### แก้ไข Backend

1. แก้ไขไฟล์ใน `api/src/`
2. รีสตาร์ท container: `docker compose restart api`

### แก้ไข Frontend

1. แก้ไขไฟล์ใน `frontend/`
2. รีสตาร์ท container: `docker compose restart nginx`

## 🐛 การแก้ปัญหา

### ปัญหาทั่วไป

1. **Port ถูกใช้งานแล้ว**
   ```bash
   docker compose down
   # ตรวจสอบ port ที่ใช้งาน
   lsof -i :443
   ```

2. **Database connection failed**
   ```bash
   docker compose logs db
   ```

3. **API ไม่ตอบสนอง**
   ```bash
   docker compose logs api
   ```
