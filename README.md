# Command Line GIT

init -> add(Stage) -> commit


## คำสั่งเบื้องต้น

`git --version` ตรวจสอบ version

`touch filename` ใช้สร้างไฟล์

`clear` ใช้เคลียร์หน้า cmd

`q` กดออก exit

## Git config

การตั้งค่า Git โดยใส่ชื่อและอีเมล์

```
git config --global user.name "your_name"
git config --global user.email "your@email.com"
```
แสดงสถานะการตั้งค่า
```
git config --list // แสดงเฉพาะ Repository นี้
git config --global --list // แสดงทั้งหมด
```

## คำสั่ง Git ที่ใช้งานบ่อย

### git init

`git init` สำหรับสร้าง Git Repository ให้กับโปรเจ็ค

### git status
`git status` คำสั่งเพื่อดูสถานะการเปลี่ยนแปลงของ Repository(Local)

### git add

คำสั่งเพื่อบันทึกเปลี่ยนสถานะ (Stage) รอการ Commit

```
git add <file_name> // ระบุไฟล์ เช่น git add index.html about.html
git add . // ทุกไฟล์ที่อยู่ภายใต้ Directory ปัจจุบัน
git add --all หรือ git add -A // ทุกไฟล์ใน Project
git add *.html // หลายไฟล์ระบุนามสกุล
```

### git rm

`git rm --cached <file_name>`  ลบออกจาก Stage 

### git checkout
การยกเลิกการแก้ไขไฟล์ เวลาเรา Save ไปแล้วแต่ยังไม่ commit 

`git checkout <file_name>`  ย้อนการแก้ไขไปยัง commit ล่าสุด/ยกเลิกการแก้ไข

### git diff
ใช้สำหรับดูว่า Code มีอะไรเปลี่ยนแปลงและแตกต่างไปบ้างเช่น มี เพิ่ม ลบ แก้ไข อะไรไปบ้าง โดยเทียบกับ Commit ที่ผ่านมา
> แสดงเครื่องหมาย - สีแดง บรรทัดเดิมก่อนถูกแก้ไขและลบ

> แสดงเครื่องหมาย + สัเขียว โค้ดใหม่ที่ถูกแก้ไขและเพิ่มใหม่
```
git diff // เฉพาะ Branch หรือ Commit ID ที่เราใช้อยู่ ณ ขณะนี้
git diff <commit_id> // แบบระบุ Commit ID 
git diff <commit_id> <commit_id> // เปรียบเทียบระหว่างสอง Commit
git diff --cached ดูสิ่งที่แก้ไขล่าสุดก่อน commit
``` 
 

### git commit
คำสั่งเพื่อบันทึกไฟล์ทั้งหมด ขั้นตอนนี้จะ Commit ไปที่ Repository (Local) 
```
git commit -m "ข้อความอธิบายการเปลี่ยนแปลง"
```

### git log
คำสั่งใช้ดูประวัติการ commit ต่างๆ ของRepo โดยจะแสดง เลขcommit, commit message, ชื่อผู้เขียน, email, และเวลาที่ commit นั้นๆ
```
git log
git log --oneline // แสดงแต่ละlog เหลือบรรทัดเดียว
git log --pretty=oneline // แสดงแต่ละlog เหลือบรรทัดเดียว แต่แสดง commit เต็มไม่ซ่อน 
git log --graph // แสดงเป็นเส้น Branch ให้ดูง่ายขึ้น
git log --oneline --graph // ถ้าใช้แบบนี้จะดูง่ายขึ้นมาก
```
`git lg` เป็นคำสั่งใช้ดูประวัติการ commit แบบเป็น branch ต้องเพิ่มการตั้งค่าด้านล่างก่อน

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
```

### git reset
คำสั่งยกเลิกเมื่อเราสั่ง git add ไปแล้ว
```
git reset <file_name>
```

### GIT Branching 

`git branch`  ตรวจสอบ branch ที่มีอยู่ในโปรเจค

`git checkout <branch_name>` ออกจาก Branch ปัจจุบันไปยัง Branch ที่มีอยู่แล้ว

`git checkout -b <branch_name>` ออกจาก Branch ปัจจุบัน สร้าง Branch ใหม่และสลับไป Branch นั้นทันที

`git branch -d <branch_name>` ลบ Branch

`git merge <branch_name>` รวม Branch

### git push
เพื่อส่งไฟล์ขึ้นไปที่ Repository บน Git (Remote)
```
git push โค้ดที่พึ่งเขียนขึ้นไปบน server
git push <remote_name> <branch_name> // ตัวอย่าง git push origin master
```

### git pull
คำสั่งดึงไฟล์ หรืออัพเดท Source Code ภายในเครื่อง (Local) ให้ตรงกับ Repository (Remote) โดยคำสั่ง git pull นั้นจะทำการ git fetch และ git merge ไปด้วย
```
git pull
git pull <remote_name> <branch_name> // ตัวอย่าง git pull origin master
```

### git fetch
เพื่อใช้ดึงความเปลี่ยนแปลงจาก Remote Repository มายัง Local  Repositoryมายัง
```
git fetch
```


