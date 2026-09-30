# JAI Prize Wheel

วงล้อสุ่มของรางวัลแบบ static ล้วน (HTML + JSON) บน GitHub Pages — ไม่มี backend, ไม่บันทึกประวัติ

| ไฟล์ | หน้าที่ |
|---|---|
| `index.html` | หน้าวงล้อสำหรับผู้เล่น — หมุนได้ 1 ครั้งต่อการเข้าหน้า (รีเฟรชเพื่อหมุนใหม่) |
| `admin.html` | หน้าหลังบ้าน — แก้ชื่อ/สี/โอกาสออกของรางวัล แล้วกดบันทึกขึ้นเว็บ |
| `prizes.json` | รายการของรางวัลและน้ำหนัก (หน้าวงล้ออ่านไฟล์นี้) |

## การสุ่ม

- โอกาสออก = น้ำหนักของรางวัล ÷ น้ำหนักรวม (เช่น 70 / 27.5 / 2.5 → 70% / 27.5% / 2.5%)
- น้ำหนัก `0` = แสดงบนวงล้อแต่ไม่มีทางออก
- สุ่มในเครื่องผู้เล่นด้วย `crypto.getRandomValues` — ไม่ต้องรอเน็ต

## แก้โอกาสออกผ่านหน้า admin (แนะนำ)

1. สร้าง token ครั้งแรกครั้งเดียว: GitHub → Settings → Developer settings → **Fine-grained tokens** → Generate new token
   - Repository access: **Only select repositories** → `jai-prize-wheel`
   - Permissions → Repository permissions → **Contents: Read and write**
2. เปิด `admin.html` → วาง token → แก้รางวัล → **บันทึกขึ้นเว็บ**
3. รอประมาณ 1 นาที ให้ GitHub Pages อัปเดต แล้วหน้าวงล้อจะใช้ค่าใหม่

Token เก็บไว้เฉพาะในเบราว์เซอร์ของเครื่องที่ติ๊ก “จำไว้ในเครื่องนี้” — ห้ามใส่ token ลงในโค้ด

## แก้โดยไม่ใช้ token

แก้ `prizes.json` บน GitHub โดยตรง (กดรูปดินสอ) หรือในหน้า admin กด **ดาวน์โหลด prizes.json** แล้วอัปโหลดทับไฟล์เดิม
