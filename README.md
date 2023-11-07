# Pneumonia Detection using CNN 💻🩺

## 📁Dataset
ข้อมูลที่ใช้ในมาจาก [Chest X-Ray Images (Pneumonia) ใน kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/)

## หมายเหตุ:
❗❗ ข้อมูลชุดนี้ Imbalanced มาก ทั้ง train และ test set 
    
- train set: ภาพ xray normal มี 1341 ภาพ ส่วน pneumonia มี 3369 ภาพ ซึ่งภาพ xray normal น้อยกว่า pneumonia อยู่ที่ 2028 ภาพ

- test set: ภาพ xray normal มี 234 ภาพ ส่วน pneumonia มี 390 ภาพ ซึ่งภาพ xray normal น้อยกว่า pneumonia อยู่ที่ 156 ภาพ


To do:

[✅] 1. ทำ augmentation แต่ใช้ข้อมูลที่เท่ากัน (Under-sampling)

[...] 2. ลองทำ Over-sampling

[...] 3. ลองใช้ Class Weights มาปรับ

[...] 4. ลองใช้ transfer learning

// 1-3. model น่าจะเหมือนกันนะ


## result
1. **ทำ augmentation แต่ใช้ข้อมูลที่เท่ากัน (Under-sampling)**



