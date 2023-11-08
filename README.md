# Pneumonia Detection using CNN 💻🩺


## 📁Dataset
ข้อมูลที่ใช้ในมาจาก [Chest X-Ray Images (Pneumonia) ใน kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/)

## ความท้าทาย:
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
    - จำนวนข้อมูล
        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/no_train_model1.png?raw=true" alt= "no_train_model1" height="200">
        </p>
        
        ใน training set ทั้งสอง class มีจำนวนรูปภาพเท่ากัน 

        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/no_test_model1.png?raw=true" alt= "no_test_model1" height="200">
        </p>
        ส่วนใน test set pneumonia จะมีจำนวนมากกว่า normal เล็กน้อย
        
    - model ที่ใช้
        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/model1.png?raw=true" alt= "model1" height="200">
        </p>

    - ผลที่ได้
        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/history_model1.png?raw=true" alt= "history_model1" height="300">
        </p>

        จากการ Train Model พบว่า ค่า accuracy ของทั้ง training และ validation อยู่ในค่าที่ใกล้เคียงกัน โดยในครั้งล่าสุดมี train accuracy: 0.9149 และ validation accuracy: 0.8977 ซึ่งนั่นแปลว่า model ที่ 1 นี้ ไม่เกิดการ overfitting หรือ underfitting ขึ้น 

        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/acc_model1.png?raw=true" alt= "acc_model1" height="100">
        </p>

        จากการ Evaluate Model ได้ค่า accuracy อยู่ที่ 0.898 ซึ่งถือว่าค่อนข้างดีเลย แต่ส่วนตัวคิดว่าในงานที่เกี่ยวกับทางการแพทย์ อย่างงานนี้ควรจะมีค่า accuracy ที่สูงกว่านี้ เพื่อการวินิจฉัยโรคจะได้มีประสิทธิภาพมากขึ้น
    
    - ลองทำนายกับภาพอื่น 

        *ตัวอย่างการแปลผลในภาพ: p--> pneumonia [0.859] คือ ทำนายว่าเป็น pneumonia โดยมีความน่าจะเป็นอยู่ที่ 0.859 โดยที่ถ้าค่าความน่าจะเป็นมากกว่า 0.5 จะเป็น pneumonia ถ้าน้อยกว่า 0.5 จะเป็น normal*



        <p align="center">
        <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/result_model1.png?raw=true" alt= "result_model1" height="100">
        </p>

        เมื่อลองทำนายกับภาพอื่นดู พบว่าทั้ง 26 ภาพนี้ model ทำนายได้ถูกต้องทุกภาพเลย 
    