# 🚀 KEYENCE_inkjet_printing_control_DEMO

![GitHub repo size](https://img.shields.io/github/repo-size/username/repo-name)
![GitHub contributors](https://img.shields.io/github/contributors/username/repo-name)
![GitHub stars](https://img.shields.io/github/stars/username/repo-name?style=social)
![GitHub forks](https://img.shields.io/github/forks/username/repo-name?style=social)

## 📖 คำอธิบาย
โปรเจคต์นี้เป็นระบบสําหรับควบคุมเครื่องพิมพ์ Inkjet รุ่น Keyence เพื่อไว้จัดการในส่วนต่างๆ เช่น ส่งข้อความ บันทึกประวัติในการพิมพ์ และแสดงสถานะล่าสุดของอินเจ็ค เป็นต้น 
โดยระบบออกแบบมาให้ผู้ใช้งานสามารถควบคุมผ่านคอมพิวเตอร์หรือโน๊ตบุ้คได้ทุกรุ่น โดยสามารถเชื่อมต่ออินเจ็คพร้อมกันได้สูงสุดถึง 4 เครื่อง ผ่านการเชื่อมต่อด้วย IPAddress

---

## 📸 ตัวอย่างหน้าจอ (Screenshots)

ภาพรวมการทำงานของระบบ:

![หน้าจอ Dashboard](./images/dashboard.png)  
*รูปที่ 1: หน้า Dashboard แสดงข้อมูลอินเจ็คทั้งหมด*

![หน้าจอฟอร์มเพิ่มสินค้า](./images/add_inkjet.png)  
*รูปที่ 2: ฟอร์มเพิ่มอินเจ็คใหม่*

---

## ⚙️ วิธีการติดตั้ง

1. Clone โปรเจกต์นี้ลงเครื่องของคุณ:
   ```bash 
   git clone https://github.com/ecctechs/KEYENCE_inkjet_printing_control_DEMO.git
   cd KEYENCE_inkjet_printing_control_DEMO


## 🖥️ วิธีใช้งาน

1. เชื่อมสาย LAN จากคอมพิวเตอร์หรือโน้ตบุ๊กของคุณเข้ากับเครื่อง Inkjet
   - กรณีต้องการควบคุมหลายเครื่องพร้อมกัน ให้เชื่อมเครื่อง Inkjet แต่ละเครื่องเข้ากับ **Hub/Switch**
2. ทําการทดสอบโดยการ ไปที่ CMD และ PING หา Inkjet แต่ละเครื่อง ถ้า PING เจอแสดงว่าเชื่อมต่อสําเร็จ
3. ทําการเปิดโปรแกรม
4. กดสร้าง INKJET และกรอกข้อมูลดังนี้ให้ครบถ้วน
   - Inkjet Name
   - IPAddress
   - Port
   - Input Directory
   - Output Directory
5. ทําการกดคลิกที่ปุ่ม Browse Output Status Path เพื่อเลือกตําแหน่งไฟล์ live_status.csv เพื่อดูสถานะเครื่องพิมพ์แบบ Real Time
6. กดปุ่ม Add เพื่อเพิ่ม Inkjet
7. ทําการอัพโหลดไฟล์ข้อความที่ต้องการส่ง ในโฟลเดอร์ Input Directory ที่กําหนดไว้
8. เมื่ออัพโหลดไฟล์ เสร็จสิ้นข้อมูล ชื่อไฟล์จะถูกปรากฎในช่อง Queue Data และ ข้อความที่ส่งปรากฎในช่อง Waiting Print Detail 
9. โปรแกรมจะทําการวนลูปเพื่อเช็คทุกๆ 10 วิ กรณีที่เครื่องอยู่ในสถานะพร้อมพิมพ์(ไม่มี error ใดๆ)  ข้อมูลจะถูกย้ายจาก  Queue Data -> Current Data และ Waiting Print Detail -> Lastest Print Detail แสดงว่าข้อมูลถูกส่งสําเร็จ และไฟล์ใน Input Directory จะถูกลบทันที
10. สามารถดูประวัติข้อความที่ส่งได้ที่ Output Directory ที่กําหนด


