
# 🚀 โปรแกรมจัดการเครื่องพิมพ์ Inkjet Keyence

![GitHub repo size](https://img.shields.io/github/repo-size/username/repo-name)
![GitHub contributors](https://img.shields.io/github/contributors/username/repo-name)
![GitHub stars](https://img.shields.io/github/stars/username/repo-name?style=social)
![GitHub forks](https://img.shields.io/github/forks/username/repo-name?style=social)

## 📖 คำอธิบาย
โปรเจคต์นี้เป็นระบบสําหรับควบคุมเครื่องพิมพ์ Inkjet Keyence รุ่น MK-G1000 Series เพื่อไว้จัดการในส่วนต่างๆ เช่น ส่งข้อความ บันทึกประวัติในการพิมพ์ และแสดงสถานะล่าสุดของ Inkjet เป็นต้น 
โดยระบบออกแบบมาให้ผู้ใช้งานสามารถควบคุมผ่านคอมพิวเตอร์หรือโน๊ตบุ้คได้ทุกรุ่น โดยสามารถเชื่อมต่อ Inkjet พร้อมกันได้สูงสุดถึง 4 เครื่อง ผ่านการเชื่อมต่อด้วย IPAddress

---

## 📸 ตัวอย่างหน้าจอ (Screenshots)

ภาพรวมการทำงานของระบบ:

![หน้าจอ Dashboard](./images/dashboard.png)  
*รูปที่ 1: หน้า Dashboard แสดงข้อมูล Inkjet ทั้งหมด*

![หน้าจอฟอร์มเพิ่มสินค้า](./images/add_inkjet.png)  
*รูปที่ 2: ฟอร์มเพิ่ม Inkjet ใหม่*

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
4. ทําการกดคลิกที่ปุ่ม Browse Output Status Path เพื่อเลือกตําแหน่งไฟล์ live_status.csv เพื่อดูสถานะเครื่องพิมพ์แบบ Real Time
5. กดสร้าง INKJET และกรอกข้อมูลดังนี้ให้ครบถ้วน
   - Inkjet Name
   - IPAddress
   - Port
   - Input Directory
   - Output Directory
------ ควรทําให้ Status Inkjet เป็น Printable(สีเขียว) ก่อนทําข้อ 6 ------
6. ทําการลากไฟล์ .txt เข้าไปในโฟลเดอร์ Input Directory ที่กําหนดไว้ข้อ 5 (ไฟล์ .txt ต้องมีข้อความข้างใน เช่น BATCH-ABC)
7. เมื่อลากไฟล์แล้ว ชื่อไฟล์ .txt จะถูกปรากฎในช่อง Queue Data และ ข้อความที่กําหนดข้างในไฟล์ .txt จะปรากฎในช่อง Waiting Print Detail 
8. โปรแกรมจะทําการวนลูปเพื่อเช็คทุกๆ 10 วิ กรณีที่เครื่องอยู่ในสถานะพร้อมพิมพ์(ไม่มี error ใดๆ)  ข้อมูลจะถูกย้ายจาก  Queue Data -> Current Data และ Waiting Print Detail -> Lastest Print Detail แสดงว่าข้อมูลถูกส่งสําเร็จ และไฟล์ใน Input Directory จะถูกลบทันที
9. สามารถดูประวัติข้อความที่ส่งได้ที่ Output Directory ที่กําหนด

## ⚙️ โหมดการทำงาน (Auto / Manual)

1. โหมด Auto
- โปรแกรมจะ ตรวจสอบ Queue และสถานะเครื่อง Inkjet โดยอัตโนมัติ ทุก ๆ 10 วินาที  
- เมื่อเครื่องพร้อมพิมพ์ (ไม่มี Error) ข้อมูลจะถูกส่งไปที่ Inkjet โดยอัตโนมัติ
- ไฟล์ใน Input Directory จะถูกลบทันทีหลังส่งสำเร็จ และบันทึกในประวัติการพิมพ์ว่า Auto
- เหมาะสำหรับการส่งไฟล์หลาย ๆ ชุดต่อเนื่องโดยไม่ต้องควบคุมเอง

2. โหมด Manual
- ผู้ใช้สามารถกดคลิกที่ปุ่ม ดินสอ เพื่อพิมพ์ข้อความลงในช่อง Latest Print Detail และส่งไปที่ Inkjet ด้วยตนเอง  
- เมื่อเครื่องพร้อมพิมพ์ (ไม่มี Error) ข้อมูลจะถูกส่งไปที่ Inkjet  
- ไฟล์ใน Input Directory จะถูกลบทันทีหลังส่งสำเร็จ และบันทึกในประวัติการพิมพ์ว่า Manual 
- เหมาะสำหรับการส่งข้อความเดียว เพื่อส่งให้ Inkjet ทันที

## 🖥️ เครื่องมือที่ใช้ในการพัฒนา

1. ระบบปฏิบัติการ Windows 10
2. Microsoft Visual Studio 2022
 - Guna.UI2.WinForms 2.0.4.7
 - Newtonsoft.Json 13.0.3
 - .NET Framework 4.7.2
