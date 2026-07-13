# 🎹 Piano Gamified Practice App

An interactive web application designed to gamify piano practice, featuring real-time AI audio scoring, automated quota controls, and engaging social rewards.

---

## 🚀 Project Overview (ภาพรวมโปรเจกต์)
เว็บแอปพลิเคชันสำหรับฝึกซ้อมเปียโนที่ผสมผสานระบบเกม (Gamification) เข้ามาเพื่อกระตุ้นให้นักเรียนฝึกซ้อมอย่างสม่ำเสมอ โดยมีหัวใจหลักคือระบบตรวจเสียงและให้คะแนนด้วย AI พร้อมระบบจำกัดโควตาการซ้อมสำหรับผู้ใช้สายฟรี

### 🌟 Core Features (ฟีเจอร์เด่น)
- **AI Practice Scoring:** ตรวจจับและประมวลผลคะแนนการซ้อม ($0-100\%$) พร้อมแจ้งเตือนหากมีเสียงรบกวน (Audio Quality Feedback)
- **Freemium & Quota System:** สิทธิ์ทดลองใช้ Premium 7 วัน และระบบล็อกโควตาซ้อมฟรี 3 ครั้งต่อรอบ (รีเซ็ตอัตโนมัติเวลา 12:00 PM และ 12:00 AM)
- **Gamification & Inventory Shop:** ระบบสะสมคะแนน Streak ภารกิจประจำวัน และร้านค้าซื้อของแต่งอวาตาร์

---

## 🗺️ System Architecture (สถาปัตยกรรมระบบ)

### Use Case Modules
ระบบถูกแบ่งออกเป็น 4 โมดูลหลักตามแผนภาพสถาปัตยกรรมระบบ:
1. **Module 1: Onboarding & Profile** - จัดการโปรไฟล์, อวาตาร์ และรายงานสถิติตัวเลขรายสัปดาห์
2. **Module 2: Core Practice System** - ระบบเลือกเพลง, ซาวด์เช็คก่อนอัดเสียง, เมโทรนอม และการประมวลผลของ AI
3. **Module 3: Gamification & Social** - ภารกิจประจำวัน, ตารางอันดับ (Leaderboard) และการแชร์การ์ดความคืบหน้า
4. **Module 4: Monetization & Subscription** - ระบบร้านค้า และการควบคุมเช็คสิทธิ์โควตาบัญชี

---

## 🗄️ Database Structure (โครงสร้างฐานข้อมูล MongoDB)

โปรเจกต์นี้ใช้ **MongoDB (NoSQL)** ในการจัดเก็บข้อมูล โดยเน้นสถาปัตยกรรมแบบ **Embedding** เพื่อประสิทธิภาพความเร็วสูงสุดในการเรียกอ่านข้อมูล (ลดการทำ Database Joins)

### Collections Mapping
ฐานข้อมูลถูกจัดระเบียบออกเป็น 4 Collections หลัก:
1. `users` : เก็บข้อมูลบัญชี, ฝังข้อมูลของแต่งตัวละคร (`profile`) และฝังข้อมูลสิทธิ์การใช้งาน (`subscription_quota`) ไว้ในก้อนเดียวกัน
2. `songs_library` : คลังจัดเก็บข้อมูลโน้ตเพลงและเมทาดาตาทั้งหมดของแอป
3. `practice_logs` : บันทึกประวัติการซ้อมเปียโนแต่ละรอบ ผลคะแนนจาก AI และความเห็นเรื่องคุณภาพเสียง
4. `daily_tasks` : จัดเก็บภารกิจประจำวันและฝังแทร็กความคืบหน้าของนักเรียนแต่ละคน (`student_progress`)

*(สำหรับตัวอย่าง Mock Data ในรูปแบบ JSON ของแต่ละ Collection สามารถเข้าไปดูและอ้างอิงได้จากไฟล์พิมพ์เขียวฉบับเต็มในโฟลเดอร์ `/docs/db-blueprint.json`)*

---

## 💻 Tech Stack (เทคโนโลยีที่ใช้)
- **Frontend:** HTML5, CSS3, JavaScript / React (หรือเฟรมเวิร์กที่คุณเลือกใช้)
- **Backend:** Node.js, Express
- **Database:** MongoDB (via Mongoose)
- **AI Engine:** Web Audio API & Audio Analysis Model

---

## 🛠️ Installation & Setup (ขั้นตอนการติดตั้งเพื่อเริ่มงาน)

### Prerequisites
- [Node.js](https://nodejs.org/) (เวอร์ชัน 18 ขึ้นไป)
- [MongoDB](https://www.mongodb.com/) (ติดตั้งในเครื่อง หรือใช้ MongoDB Atlas)

### Steps to Run Locally
1. **Clone the repository:**
\`\`\`bash
git clone https://github.com/your-username/piano-gamified-app.git
cd piano-gamified-app
\`\`\`