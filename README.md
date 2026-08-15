# 🎓 TUNorth-Hub: แพลตฟอร์มการเรียนรู้ออนไลน์สำหรับโรงเรียนมัธยมศึกษา (LMS EdTech)

ยินดีต้อนรับสู่ **TUNorth-Hub** แพลตฟอร์มจัดการเรียนรู้ออนไลน์ (Learning Management System) เต็มรูปแบบ ที่ออกแบบมาเพื่อโรงเรียนมัธยมศึกษา รองรับการจัดการเรียนการสอนแบบ On-Demand, วิดีโอ/เอกสารประกอบ, Interactive Code Playground (Python), การส่งการบ้าน, แบบทดสอบออนไลน์จับเวลา และระบบออกเกียรติบัตรอัตโนมัติพร้อมหน้าตรวจสอบรหัสสาธารณะ

---

## 📑 สารบัญ (Table of Contents)

1. [✨ ฟีเจอร์หลักของระบบ (Key Features)](#-ฟีเจอร์หลักของระบบ-key-features)
2. [🛠️ เทคโนโลยีที่ใช้ (Tech Stack)](#️-เทคโนโลยีที่ใช้-tech-stack)
3. [📋 สิ่งที่ต้องเตรียมก่อนเริ่มติดตั้ง (Prerequisites)](#-สิ่งที่ต้องเตรียมก่อนเริ่มติดตั้ง-prerequisites)
4. [🚀 วิธีการติดตั้งและรันระบบ (Quick Start Guide)](#-วิธีการติดตั้งและรันระบบ-quick-start-guide)
   - [แบบที่ 1: รันผ่าน Docker (แนะนำสำหรับทุกคน / ง่ายที่สุด)](#แบบที่-1-รันผ่าน-docker-แนะนำสำหรับทุกคน--ง่ายที่สุด)
   - [แบบที่ 2: รันแยกเครื่องสำหรับ Development (Local Dev Mode)](#แบบที่-2-รันแยกเครื่องสำหรับ-development-local-dev-mode)
5. [🔑 บัญชีผู้ใช้เริ่มต้นสำหรับทดสอบ (Default Accounts & Seed Data)](#-บัญชีผู้ใช้เริ่มต้นสำหรับทดสอบ-default-accounts--seed-data)
6. [⚙️ การตั้งค่า Environment Variables (.env)](#️-การตั้งค่า-environment-variables-env)
7. [🌐 พอร์ตและ URL ต่างๆ ในระบบ (Port Mappings & URLs)](#-พอร์ตและ-url-ต่างๆ-ในระบบ-port-mappings--urls)
8. [📁 โครงสร้างโปรเจกต์ (Project Structure)](#-โครงสร้างโปรเจกต์-project-structure)
9. [🔧 คำสั่งที่ใช้บ่อย (Useful Commands)](#-คำสั่งที่ใช้บ่อย-useful-commands)
10. [❓ ปัญหาที่พบบ่อยและการแก้ไข (Troubleshooting & FAQs)](#-ปัญหาที่พบบ่อยและการแก้ไข-troubleshooting--faqs)

---

## ✨ ฟีเจอร์หลักของระบบ (Key Features)

* **🔐 ระบบจัดการสิทธิ์ผู้ใช้งาน (Strict Role Isolation 100%):**
  * 👨‍💼 **Admin (ผู้ดูแลระบบ):** จัดการผู้ใช้, จัดการคอร์สทั้งหมด, ปรับแต่งหน้าเว็บ/แบรนด์ดิ้ง, ควบคุมโหมดปิดปรับปรุงระบบ (Maintenance Mode) และดู Health Dashboard (สถานะ Server, DB, Redis, Storage)
  * 👩‍🏫 **Teacher (คุณครูผู้สอน):** สร้างและแก้ไขคอร์สเรียน, อัปโหลดวิดีโอ/สไลด์ PDF, สร้างแบบทดสอบ, ตรวจการบ้านและให้คะแนน, พรีวิวคอร์สเสมือนนักเรียน
  * 🧑‍🎓 **Student (นักเรียน):** ลงทะเบียนเรียน, ดูเนื้อหาวิดีโอ, ทำแบบทดสอบแบบจับเวลา, ส่งการบ้าน, เขียนโค้ด Python ผ่านเบราว์เซอร์ และรับเกียรติบัตรเมื่อเรียนจบ
* **🐍 Interactive Code Playground:**
  * ฝึกเขียนโค้ด Python 3 ในเบราว์เซอร์ได้ทันที ไม่ต้องลงโปรแกรมเพิ่ม (ขับเคลื่อนด้วย Pyodide WebAssembly + Monaco Editor)
  * รองรับทั้ง Console Output, Interactive `input()`, Error handling
* **📝 Assessment & Quiz Engine:**
  * แบบทดสอบออนไลน์จับเวลาถอยหลัง (Timer)
  * ตรวจและคิดคะแนนอัตโนมัติ พร้อมกำหนดจำนวนครั้งสูงสุดในการทำข้อสอบได้
* **📜 Certificate & Verification Engine:**
  * ออกใบเกียรติบัตรอัตโนมัติเมื่อเรียนครบ 100% พร้อมรหัสมาตรฐาน `TUN-YYYY-XXXX-XXXX`
  * ออกแบบมาสำหรับพิมพ์กระดาษ A4 แนวนอน (1-Page Print Landscape)
  * หน้าระบบตรวจสอบความถูกต้องของเกียรติบัตรสาธารณะ (`/verify/[code]`)
* **🎨 Modern UI & Responsive Design:**
  * รองรับ Light & Dark Mode ปรับเปลี่ยนได้ลื่นไหล
  * รองรับการแสดงผลทุกหน้าจอตลอดจนมือถือและแท็บเล็ต

---

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack)

| ส่วนของระบบ | เทคโนโลยีหลัก | รายละเอียดเพิ่มเติม |
| :--- | :--- | :--- |
| **Frontend** | Next.js 16 (App Router), React 19, TypeScript | ใช้ Tailwind CSS v4, Lucide Icons, Sonner Toasts |
| **Frontend Tooling** | Bun | จัดการ Dependencies และ Build Process ได้รวดเร็ว |
| **Backend API** | Go 1.25+, Fiber v2, GORM | ประสิทธิภาพสูง โหลดเร็ว และรองรับ Concurrent Users |
| **Database** | PostgreSQL 17 | จัดเก็บข้อมูลระบบหลัก และ Auto-Migration อัตโนมัติ |
| **In-Memory Cache** | Redis 7 | แคชข้อมูลและจัดการ Session/Rate Limiter |
| **Code Sandbox** | Pyodide (WebAssembly), Monaco Editor | รัน Python ภายใน Client Browser |
| **DevOps / Proxy** | Docker, Docker Compose, Nginx | รองรับการ Deploy บน Server และ Local Dev สะดวก |

---

## 📋 สิ่งที่ต้องเตรียมก่อนเริ่มติดตั้ง (Prerequisites)

ก่อนเริ่มต้น ให้ตรวจสอบว่าในเครื่องคอมพิวเตอร์ของคุณติดตั้งโปรแกรมต่อไปนี้เรียบร้อยแล้ว:

1. **Git:** สำหรับ Clone โค้ดโปรเจกต์ ([ดาวน์โหลด Git](https://git-scm.com/))
2. **Docker Desktop:** สำหรับรัน Database, Redis, หรือรันทั้งระบบแบบ Container ([ดาวน์โหลด Docker Desktop](https://www.docker.com/products/docker-desktop/))
   * *หมายเหตุ: หากใช้ Windows แนะนำให้เปิดใช้งาน WSL 2 (Windows Subsystem for Linux)*
3. **กรณีต้องการรันโค้ดแบบ Manual (Local Dev):**
   * **Bun:** ([ติดตั้ง Bun](https://bun.sh/)) หรือ Node.js v20+
   * **Go:** เวอร์ชั่น 1.23+ ([ติดตั้ง Go](https://go.dev/))

---

## 🚀 วิธีการติดตั้งและรันระบบ (Quick Start Guide)

### แบบที่ 1: รันผ่าน Docker (แนะนำสำหรับทุกคน / ง่ายที่สุด)

วิธีนี้เหมาะสำหรับผู้ที่ต้องการรันทั้งระบบ (Frontend + Backend + PostgreSQL + Redis + Nginx) พร้อมใช้งานทันทีด้วยคำสั่งเดียว:

#### ขั้นตอนที่ 1: คัดลอกไฟล์ Environment

เปิด Terminal / PowerShell แล้วไปที่โฟลเดอร์ของโปรเจกต์:

```bash
# คัดลอกไฟล์ตั้งค่าจากตัวอย่าง
cp .env.example .env
```
*(บน Windows PowerShell ใช้ `copy .env.example .env`)*

#### ขั้นตอนที่ 2: สั่งรันโปรเจกต์ด้วย Docker Compose

```bash
docker compose -f docker-compose.prod.yml up --build -d
```

*คำสั่งนี้จะทำการ:*
- Build และ Start เซิร์ฟเวอร์ Backend (Go), Frontend (Next.js), Nginx, PostgreSQL และ Redis ให้อัตโนมัติ
- ทำ Auto-Migration ฐานข้อมูล และสร้างข้อมูลทดสอบเริ่มต้น (Seed Data) ให้อัตโนมัติ

#### ขั้นตอนที่ 3: เปิดใช้งานบนเว็บเบราว์เซอร์

เปิดเบราว์เซอร์แล้วเข้าไปที่:
* 🌐 **Web Application:** [http://localhost](http://localhost) (ผ่าน Nginx พอร์ต 80) หรือ [http://localhost:3000](http://localhost:3000)
* 🔌 **Backend API:** [http://localhost:8080/api/v1](http://localhost:8080/api/v1)

> 💡 **การปิดการทำงาน:** เมื่อต้องการหยุดการทำงาน ให้ใช้คำสั่ง:
> ```bash
> docker compose -f docker-compose.prod.yml down
> ```

---

### แบบที่ 2: รันแยกเครื่องสำหรับ Development (Local Dev Mode)

วิธีนี้เหมาะสำหรับนักพัฒนาที่ต้องการแก้ไขโค้ดและดูผลลัพธ์แบบ Real-time (Hot Reload):

#### ขั้นตอนที่ 1: รันเฉพาะ Database & Redis ผ่าน Docker

เริ่ม Database และ Redis ขึ้นมาก่อน:

```bash
docker compose up -d
```
*(จะรัน PostgreSQL ที่พอร์ต `5432` และ Redis ที่พอร์ต `6379`)*

#### ขั้นตอนที่ 2: สร้างไฟล์ `.env` ที่ Root

```bash
cp .env.example .env
```

#### ขั้นตอนที่ 3: รัน Backend (Go)

เปิด Terminal ที่ 1:

```bash
cd backend

# ติดตั้ง Go dependencies
go mod download

# รัน Backend Server (พร้อม Seed ข้อมูลทดสอบ)
go run cmd/server/main.go --seed
```
*เซิร์ฟเวอร์ Backend จะทำงานที่ `http://localhost:8080`*

#### ขั้นตอนที่ 4: รัน Frontend (Next.js)

เปิด Terminal ที่ 2:

```bash
cd frontend

# ติดตั้ง Dependencies ด้วย Bun (หรือ npm)
bun install

# รัน Dev Server
bun run dev
```
*เว็บ Frontend จะทำงานที่ `http://localhost:3000`*

---

## 🔑 บัญชีผู้ใช้เริ่มต้นสำหรับทดสอบ (Default Accounts & Seed Data)

ระบบได้เตรียมบัญชีผู้ใช้เริ่มต้นในทุกระดับสิทธิ์ (Role) พร้อมรหัสผ่านเดียวกันเพื่อให้ทดสอบได้ทันที:

| บทบาท (Role) | อีเมล (Email) | รหัสผ่าน (Password) | สิทธิ์และการเข้าถึง |
| :--- | :--- | :--- | :--- |
| 👨‍💼 **Admin (ผู้ดูแลระบบ)** | `admin@tunorth.ac.th` | `Password123!` | เข้าใช้งานหน้า `/admin` (จัดการระบบ, ผู้ใช้, ธีม, สถิติ) |
| 👩‍🏫 **Teacher (คุณครู)** | `teacher@tunorth.ac.th` | `Password123!` | เข้าใช้งานหน้า `/teacher` (จัดการรายวิชา, สื่อการสอน, ข้อสอบ) |
| 🧑‍🎓 **Student (นักเรียน 1)** | `student1@tunorth.ac.th` | `Password123!` | เข้าใช้งานหน้า `/student` (เรียนหนังสือ, ทำแบบทดสอบ, การบ้าน) |
| 🧑‍🎓 **Student (นักเรียน 2)** | `student2@tunorth.ac.th` | `Password123!` | เข้าใช้งานหน้า `/student` (เรียนหนังสือ, ทำแบบทดสอบ, การบ้าน) |

> 📌 **หมายเหตุ:** นักเรียนทั่วไปสามารถกด **"สมัครสมาชิก" (Register)** ผ่านหน้าเว็บเพื่อสร้างบัญชีใหม่ได้ด้วยตนเอง

---

## ⚙️ การตั้งค่า Environment Variables (.env)

ไฟล์ `.env` ที่ Root ของโปรเจกต์ประกอบด้วยการตั้งค่าสำคัญดังนี้:

```ini
# โหมดของ Application (development / production)
APP_ENV=development
PORT=8080

# การตั้งค่าฐานข้อมูล PostgreSQL 17
POSTGRES_DB=tunorth_hub
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DATABASE_URL=postgres://postgres:postgres@localhost:5432/tunorth_hub?sslmode=disable&TimeZone=Asia/Bangkok

# การตั้งค่า Redis Cache
REDIS_URL=localhost:6379

# กุญแจความปลอดภัยสำหรับ JWT Authentication
JWT_SECRET=tunorth-hub-super-secure-jwt-secret-key-2026

# โฟลเดอร์สำหรับจัดเก็บไฟล์อัปโหลด (วิดีโอ, PDF, ภาพหน้าปก)
UPLOAD_DIR=./uploads

# กำหนด Origin ที่อนุญาตให้เชื่อมต่อ API (CORS)
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:80,http://localhost
```

---

## 🌐 พอร์ตและ URL ต่างๆ ในระบบ (Port Mappings & URLs)

| บริการ (Service) | URL / Connection String | คำอธิบาย |
| :--- | :--- | :--- |
| **Frontend Web App** | `http://localhost:3000` หรือ `http://localhost` | หน้าเว็บไซต์หลักสำหรับผู้ใช้ทุกคน |
| **Backend REST API** | `http://localhost:8080/api/v1` | API Gateway สำหรับรับ-ส่งข้อมูล |
| **PostgreSQL Database** | `localhost:5432` | ฐานข้อมูลหลัก (User: `postgres`, Pass: `postgres`) |
| **Redis Cache** | `localhost:6379` | In-Memory Data Store & Cache |
| **Certificate Verification** | `http://localhost:3000/verify/[code]` | หน้าตรวจสอบความถูกต้องของเกียรติบัตร |

---

## 📁 โครงสร้างโปรเจกต์ (Project Structure)

```text
TUNorth-Hub/
├── backend/                  # ซอร์สโค้ดฝั่งเซิร์ฟเวอร์ (Go + Fiber)
│   ├── cmd/
│   │   ├── server/           # Entry point หลักของ Backend API Server
│   │   └── seed/             # สคริปต์รัน Seed ข้อมูล
│   ├── internal/
│   │   ├── config/           # ตัวจัดการ Configuration & Environment
│   │   ├── database/         # การเชื่อมต่อ PostgreSQL & Redis
│   │   ├── handlers/         # Controller ฟังก์ชันจัดการ Request/Response
│   │   ├── middleware/       # JWT Auth, Role Guard, Rate Limit, CORS
│   │   ├── models/           # GORM Database Models & Structs
│   │   ├── routes/           # การกำหนด API Endpoints
│   │   └── seed/             # ข้อมูลเริ่มต้น (Default Mock Users/Courses)
│   ├── Dockerfile            # Dockerfile สำหรับ Production Backend
│   └── go.mod                # Go Modules & Dependencies
│
├── frontend/                 # ซอร์สโค้ดฝั่งหน้าเว็บ (Next.js 16 + TypeScript)
│   ├── src/
│   │   ├── app/              # Next.js App Router Pages
│   │   │   ├── (auth)/       # หน้า Login / Register
│   │   │   ├── admin/        # หน้าแดชบอร์ดและการจัดการของผู้ดูแลระบบ
│   │   │   ├── teacher/      # หน้าจัดการคอร์สและการสอนของคุณครู
│   │   │   ├── student/      # หน้าเรียน, คอร์ส, และโปรไฟล์นักเรียน
│   │   │   └── verify/       # หน้าระบบตรวจสอบเกียรติบัตรสาธารณะ
│   │   ├── components/       # UI Components (Navbar, Sidebar, Modals, etc.)
│   │   └── lib/              # Utility functions, API Client, Toast Helper
│   ├── Dockerfile            # Dockerfile สำหรับ Production Frontend
│   └── package.json          # Node/Bun Dependencies
│
├── docker/                   # การตั้งค่า Docker & Nginx Reverse Proxy
│   └── nginx/
│       ├── default.conf      # Routing & Proxy Pass Config
│       └── nginx.conf        # Nginx Core Config
│
├── docs/                     # เอกสารสเปกระบบและแบบแปลนฟีเจอร์ (System Spec)
│   └── spec.md               # รายละเอียด System Requirements Specification ฉบับสมบูรณ์
│
├── uploads/                  # โฟลเดอร์เก็บไฟล์ที่อัปโหลด (วิดีโอ, PDF, ภาพ)
├── docker-compose.yml        # Compose สำหรับรันเฉพาะ DB + Redis (Local Dev)
├── docker-compose.prod.yml   # Compose สำหรับรัน Full Stack พร้อม Nginx
├── .env.example              # ตัวอย่างไฟล์ Environment Variables
├── .gitignore                # การกำหนดไฟล์ที่ไม่ส่งขึ้น Git
└── README.md                 # คู่มือการใช้งานโปรเจกต์ฉบับนี้
```

---

## 🔧 คำสั่งที่ใช้บ่อย (Useful Commands)

### การจัดการ Docker Containers
```bash
# ดูสถานะ Container ทั้งหมดที่กำลังรันอยู่
docker compose ps

# ดู Logs การทำงานแบบ Real-time
docker compose -f docker-compose.prod.yml logs -f

# หยุดการทำงานและล้าง Containers ทั้งหมด
docker compose -f docker-compose.prod.yml down

# ล้างข้อมูลใน Volume ทั้งหมด (ระวัง: ข้อมูลใน DB จะหายทั้งหมด)
docker compose -f docker-compose.prod.yml down -v
```

### การทดสอบและ Build ฝั่ง Frontend
```bash
cd frontend

# ตรวจสอบ Linting และ Type Errors
bun run lint

# ทดสอบการ Build สำหรับ Production
bun run build
```

---

## ❓ ปัญหาที่พบบ่อยและการแก้ไข (Troubleshooting & FAQs)

### 1. พอร์ต 5432, 6379, 8080 หรือ 80 ชนกับโปรแกรมอื่นในเครื่อง (Port Conflict)
* **สาเหตุ:** มีโปรแกรมอื่น เช่น PostgreSQL หรือ Web Server อื่นในเครื่องกำลังใช้งานพอร์ตดังกล่าวอยู่
* **วิธีแก้:** สามารถเข้าไปเปลี่ยนพอร์ตด้านหน้าในไฟล์ `docker-compose.yml` หรือ `docker-compose.prod.yml` เช่น เปลี่ยน `"5432:5432"` เป็น `"5433:5432"` แล้วอัปเดต `DATABASE_URL` ใน `.env` ให้ตรงกัน

### 2. เข้าหน้าเว็บแล้วเกิดข้อผิดพลาด Network Error หรือโหลดข้อมูลไม่ขึ้น
* **สาเหตุ:** Backend Server หรือ Database ยังสตาร์ทไม่สมบูรณ์
* **วิธีแก้:** ตรวจสอบว่า Container ของ Backend และ Postgres อยู่ในสถานะ `healthy` ด้วยคำสั่ง `docker compose ps` และตรวจสอบ Logs ด้วย `docker compose logs backend`

### 3. Interactive Code Playground (Python) โหลดช้าในครั้งแรก
* **สาเหตุ:** Pyodide WebAssembly จำเป็นต้องดาวน์โหลด Runtime สำหรับรัน Python (~10-15MB) ผ่านเครือข่ายในการเปิดหน้าครั้งแรก
* **วิธีแก้:** เมื่อโหลดครั้งแรกสำเร็จ เบราว์เซอร์จะทำการแคชไว้ ทำให้การใช้งานครั้งต่อไปรวดเร็วทันที

### 4. อัปโหลดไฟล์วิดีโอหรือสไลด์ PDF ขนาดใหญ่ไม่ผ่าน
* **สาเหตุ:** ขนาดไฟล์เกินที่กำหนดไว้ในค่า Limit
* **วิธีแก้:** Backend ได้รับการตั้งค่ารองรับไฟล์ขนาดสูงสุด **500MB** ต่อการอัปโหลดแล้ว หากต้องการเพิ่มขนาด สามารถปรับแต่งได้ที่ `backend/cmd/server/main.go` ในส่วนของ `BodyLimit` และ `client_max_body_size` ใน `docker/nginx/default.conf`

---

💡 **ทีมพัฒนา:** หากต้องการศึกษาโครงสร้างเชิงลึก สถาปัตยกรรมระบบ หรือ Schema ตารางทั้งหมด สามารถเปิดอ่านได้ที่ [docs/spec.md](docs/spec.md)
