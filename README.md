# Pneumonia Detection using CNN 💻🩺


## 📁Dataset
<p align="center">
    <img src="https://i.imgur.com/jZqpV51.png" alt= "Examples of Chest X-Rays" height="150">
</p>

ข้อมูลนี้เกี่ยวกับ**ภาพเอกซเรย์ปอด (Chest X-ray)** มาจาก [Chest X-Ray Images (Pneumonia) ใน kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/) ซึ่งประกอบไปด้วย 2 label คือ ภาพเอกซเรย์ปอดปกติ (Normal) และภาพเอกซเรย์ปอดอักเสบ (Pneumonia)

## ความท้าทาย:
❗❗ ข้อมูลชุดนี้ Imbalanced มาก ทั้ง train และ test set 
    
- train set: มีทั้งหมด 4710 ภาพ ประกอบด้วย ภาพ xray normal มี 1341 ภาพ (28.47 %) ส่วน pneumonia มี 3369 ภาพ (71.53 %) ซึ่งภาพ xray normal น้อยกว่า pneumonia อยู่ที่ 2028 ภาพ

- test set: มีทั้งหมด 624 ภาพ ประกอบด้วย ภาพ xray normal มี 234 ภาพ (37.50 %) ส่วน pneumonia มี 390 ภาพ (62.50 %) ซึ่งภาพ xray normal น้อยกว่า pneumonia อยู่ที่ 156 ภาพ



## การจัดการกับ Imbalanced data:
การจัดการกับ Imbalanced data มีหลายวิธี เช่น Oversampling (การเพิ่มจำนวนข้อมูลของคลาสน้อย) Under-sampling (การลดจำนวนข้อมูลของคลาสหลัก) Cost-sensitive methods (พิจารณาจากค่าความผิดพลาดจากการแบ่งกลุ่ม (Misclassifiying examles)) การกำหนดค่าน้ำหนักให้กับคลาส (class weights) เป็นต้น

ที่มา: https://medium.com/espressofx-notebook/จัดการข้อมูล-imbalanced-ใน-scikit-learn-c22f4c18ebb5

## To do:

[✅] 1.ทำ Augmentation เฉพาะ train set และใช้ข้อมูลที่เท่ากัน โดยใช้วิธี Under-sampling

[✅] 2. ใช้ Class Weights มาปรับ

[.....] 3. ใช้ transfer learning  



## result
<details>
<summary> 1. ทำ Augmentation เฉพาะ train set และใช้ข้อมูลที่เท่ากัน โดยใช้วิธี Under-sampling (Click เพื่อดูเพิ่มเติม)</summary>

- จำนวนข้อมูล
    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/no_train_model1.png?raw=true" alt= "no_train_model1" height="400">
    </p>
        
    ใน training set ทั้งสอง class มีจำนวนรูปภาพเท่ากัน 

    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/no_test_model1.png?raw=true" alt= "no_test_model1" height="400">
    </p>
    ส่วนใน test set pneumonia จะมีจำนวนมากกว่า normal เล็กน้อย
        
 - model ที่ใช้
    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/model1.png?raw=true" alt= "model1" height="400">
    </p>

- ผลที่ได้
    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/history_model1.png?raw=true" alt= "history_model1" height="300">
    </p>

    จากการ Train Model พบว่า ในช่วงแรกของการ training และ validation ค่า loss และ accuracy ยังไม่ดีเท่าไรนัก เนื่องจากเป็นช่วงแรกที่ model เริ่มเรียนรู้ เมื่อผ่านไปหลาย epoch จะเห็นว่า model ก็ได้มีการเรียนรู้ไปในทางที่ดีขึ้นกว่าเดิม ค่า loss ก็ลดลงเรื่อย ๆ ส่วนค่า accuracy เองก็เพิ่มขึ้นด้วย
        
    นอกจากนี้ค่า accuracy ของทั้ง training และ validation อยู่ในค่าที่ใกล้เคียงกัน โดยในครั้งล่าสุดมี train accuracy: 0.9149 และ validation accuracy: 0.8977 ซึ่งนั่นแปลว่า model ที่ 1 นี้ ไม่เกิดการ overfitting หรือ underfitting ขึ้น 

    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/acc_model1.png?raw=true" alt= "acc_model1" height="100">
        </p>

    จากการ Evaluate Model ได้**ค่า accuracy อยู่ที่ 0.898** ซึ่งถือว่าค่อนข้างดีเลย แต่ส่วนตัวคิดว่าในงานที่เกี่ยวกับทางการแพทย์ อย่างงานนี้ควรจะมีค่า accuracy ที่สูงกว่านี้ เพื่อการวินิจฉัยโรคจะได้มีประสิทธิภาพมากขึ้น
    
- ลองทำนายกับภาพอื่น 
        
     ภาพที่จะลองมีทั้งหมด 16 ภาพ ประกอบด้วย normal มี 8 ภาพ และ pneumonia มี 8 ภาพ (มาจาก folder val ของชุดข้อมูลนี้)

    *ตัวอย่างการแปลผลในภาพ: p--> pneumonia [0.859] คือ ทำนายว่าเป็น pneumonia โดยมีความน่าจะเป็นอยู่ที่ 0.859 โดยที่ถ้าค่าความน่าจะเป็นมากกว่า 0.5 จะเป็น pneumonia ถ้าน้อยกว่า 0.5 จะเป็น normal*



    <p align="center">
    <img src="https://github.com/mill-ornrakorn/Pneumonia-Detection-using-CNN/blob/main/pic%20for%20readme/result_model1.png?raw=true" alt= "result_model1" >
    </p>

    เมื่อลองทำนายกับภาพอื่นดู พบว่าทั้ง 16 ภาพนี้ model ทำนายได้ถูกต้องทุกภาพเลย 
    
</details>


<!-- <details>
<summary> 2. ใช้ CNN model (ใน 1.) + ใช้ข้อมูลทั้งหมดเลย (Imbalanced) + ทำ Augmentation เฉพาะ train set + class weight (Click เพื่อดูเพิ่มเติม)</summary>


</details> -->


.

.

(ยังมีต่ออีกค่ะ..)

## ตารางสรุป

| No. |      Model         |         Dataset            |    Train set | Test set    | Description | Accuracy | ลองทำนายกับ 16 รูป (normal 8 ภาพ และ pneumonia 8 ภาพ) |
|-----|:------------------:|---------------------------:|---------:|-----:|------:|------:|------:| 
| 1.   |    CNN แบบแรก      | ใช้ข้อมูลที่เท่ากัน โดยใช้วิธี Under-sampling | class ละ 1340 ภาพ |  class ละประมาณ 234 ภาพ | ทำ Augmentation เฉพาะ train set | 89.8% | ถูกต้องทุกภาพ
| 2.   |    CNN แบบแรก + class weight     | ใช้ข้อมูลทั้งหมดเลย (Imbalanced) | normal มี 1341 ภาพ (28.47 %) ส่วน pneumonia มี 3369 ภาพ (71.53 %) | normal มี 234 ภาพ (37.50 %) ส่วน pneumonia มี 390 ภาพ (62.50 %) | ทำ Augmentation เฉพาะ train set และใช้ class weight มากำหนดค่าน้ำหนักให้กับคลาส | 90.9% | ทำนาย pneumonia ถูกต้องทุกภาพ แต่ทำนาย normal ผิดไป 3 ภาพ จาก 8 ภาพ



