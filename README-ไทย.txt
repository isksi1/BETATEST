วิธีสร้างไฟล์ APK และเผยแพร่เว็บจาก repository เดียวกัน

โครงสร้าง
- docs/index.html   ไฟล์หน้าเว็บหลัก (ใช้ทั้งเว็บและแอป)
- .github/workflows/build-apk.yml   สูตรสร้าง APK อัตโนมัติ
- signing/debug.keystore   กุญแจเซ็นแอป (ห้ามลบ ถ้าลบแล้วอัปเดตทับแอปเก่าไม่ได้)
- package.json, capacitor.config.json   ตั้งค่าตัวสร้างแอป

ขั้นตอน
1. ไปที่ repository tun-calculate บน GitHub กด Add file > Upload files
2. ลากไฟล์และโฟลเดอร์ทั้งหมดในซิปนี้ไปวาง (ต้องมี .github, docs, signing)
   Windows: เปิด File Explorer > View > Show > Hidden items เพื่อให้เห็นโฟลเดอร์ที่ขึ้นต้นด้วยจุด
3. ถ้าก่อนหน้านี้มีไฟล์ index.html ที่หน้าแรกของ repository ให้ลบทิ้ง แล้วกด Commit changes
4. ไปที่แท็บ Actions รอ 3-6 นาทีให้ "Build APK" ขึ้นเครื่องหมายถูกสีเขียว
   (ถ้าไม่ทำงานเอง กดเลือก Build APK แล้วกด Run workflow)
5. กดเข้างานนั้น เลื่อนลงส่วน Artifacts ดาวน์โหลด absence-calculator-apk
   แตกซิปได้ app-debug.apk ส่งเข้ามือถือ Android แล้วติดตั้ง

ถ้าอยากเปิดเป็นเว็บด้วย
- Settings > Pages > Source: Deploy from a branch > Branch: main โฟลเดอร์ /docs > Save
- ต้องตั้ง repository เป็น Public จึงจะเปิด Pages ได้ แต่ถ้าต้องการแค่ APK ตั้งเป็น Private ได้

การอัปเดตแอป
- แก้ไฟล์ docs/index.html บน GitHub แล้ว Commit ระบบจะสร้าง APK ใหม่ให้เอง
- ติดตั้งไฟล์ใหม่ทับแอปเดิมได้เลย ข้อมูลที่บันทึกไว้จะยังอยู่ (ห้ามถอนการติดตั้งก่อน)

เรื่องข้อมูล
- แอปบันทึกข้อมูลอัตโนมัติในเครื่อง ถอนการติดตั้งหรือล้างข้อมูลแอปแล้วข้อมูลจะหาย
- กดปุ่ม "สำรองข้อมูล" เป็นระยะ แล้วใช้ "นำข้อมูลกลับมา" เมื่อย้ายเครื่อง
