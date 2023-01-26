registers เป็นหน่วยความจำภายใน cpu

ซึ่ง RISC-V มี Register ให้ใช้ทั้งหมด 32 ตัว (x0 ถึง x31) ซึ่ง Register แต่ละตัวนั้นจะมีหน้าที่เฉพาะแตกต่างกันไป

โดยในที่นี้

x1 เรากำหนดให้เป็น Adress เริ่มต้น ที่เราใส่ข้อมูลไว้เพื่อให้ได้ output ออกมาเป็นตัวอักษรที่ต้องการ
x2 เราใช้ในการกำหนดให้ output ออกมาเป็นตัวอักษร แล้วแสดงผลที่ c0000000 ตรง Text/IO
x3 เราใช้รับค่าที่เรากำหนดไว้ใน Adress 20-24 เพื่อให้ output ออกไปที่ Text/IO

และเข้าลูปเพื่อจบโปรแกรมได้ด้วยเมื่อปริ้นถึง Adress 25 ซึ่งกำหนดไว้เป็น 00 ทำให้ x3 กลายเป็น 0
จึงถูกจั๊มไป 16 ด้วย beq x3, x0, +16
และติดลูปด้วย jal x0, 0
