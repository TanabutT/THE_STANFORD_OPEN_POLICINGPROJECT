# THE_STANFORD_OPEN_POLICINGPROJECT

Do police bias with black and Hispanic drivers and searched more often than whites?


THE STANFORDOPEN POLICINGPROJECT part 1

https://medium.com/botnoi-classroom/the-stanfordopen-policingproject-66cfc2e3a2af?source=friends_link&sk=d2c169f546a7e49f63e2a8c402d18bae

THE STANFORDOPEN POLICINGPROJECT part 2
https://tanabutt.medium.com/the-stanfordopen-policingproject-part-2-198ac6251858


Do police bias with black and Hispanic drivers and searched more often than whites?
จริงหรือที่ว่า เมื่อตำรวจทำการเรียกรถให้หยุดในการปฏิบัติหน้าที่ มีโอกาสที่ต้องการจะค้นตัว หรือค้นรถต่อเพื่อหาสิ่งผิดปกติ bias เกิดกับ คนผิวสี และคนที่พูดสเปนหรือคนทางเม็กซิโกนั่นเอง โดยใช้ข้อมูลจาก https://openpolicing.stanford.edu/ โดยจะทำกันโดยเลือก จาก Rhode Island State ครับผม
https://openpolicing.stanford.edu/img/mp.jpg
ใครอยากตามไปดูตัวเต็มตามไปได้ ที่ GitHub หรือ Google colab ตามนี้เลยครับผม ลุย!
GitHub ช่วง prepare: https://gist.github.com/TanabutT/83452915139c2e0069811cd745d1f431#file-policedataprepare-ipynb และ https://gist.github.com/TanabutT/0a2e334ab8ad27bbfae56abea23c2f1c
Google collab ช่วง prepare: https://drive.google.com/file/d/1VwSjFmoqzpWG_X-F8W8lYSrT2dd9I7wS/view?usp=sharing
Google collab ช่วง analysis : https://drive.google.com/file/d/1VwSjFmoqzpWG_X-F8W8lYSrT2dd9I7wS/view?usp=sharing

THE STANFORDOPEN POLICINGPROJECT part 3 (final)
medium article link:  
https://medium.com/tanabut-taksinavongskukl/the-stanfordopen-policingproject-final-400a03eb346e  
github gist link:  
https://gist.github.com/TanabutT/4106063c035f0928d999044a561ae09d  
google colab link:  
https://colab.research.google.com/drive/1cCj4qGWQqVeYZnWflCPV0fOcc-N5pdAo?usp=sharing  
github link:  
https://github.com/TanabutT/THE_STANFORD_OPEN_POLICINGPROJECT  
https://github.com/TanabutT/THE_STANFORD_OPEN_POLICINGPROJECT/blob/main/RIpolice_part3_final_submit.ipynb  


### Summary in part final นี้จะมีหลักสำคัญดังนี้
- จัดการ imbalance Data
- ใช้ feature selection เข้ามาช่วยซึ่งมีทั้งแบบ supervise และ unsupervise
- เลือก evaluation matric ที่เหมาะสมกับ application เพื่อที่จะทำการ Tune Hyperparameter และเปรียบเทียบผล

### application ของ ML model ที่จะทำนี้ objective หลักคือ
ต้องการทำนายการผ่านการเรียกของตำรวจไปโดยไม่โดนตรวจค้นภายในรถ โดยต้องการให้ค่าผิดพลาดในการทำนายพลาดน้อยที่สุด นั่นคือ สามารถรู้ได้ว่ารถที่จะใช้ทำงานขนของอะไรก็ตาม เมื่อโดนตำรวจเรียกแล้วจะไม่โดนตรวจค้นภายในรถ ผิดพลาดน้อยกว่า 5%

### จุดมุ่งหมายของการปรับปรุง Machine Learning model
- จัดการ imbalace data ในที่นี้เลือกใช้แบบไหนต้องลองดูกันว่าแบบไหนดีที่สุดจาก Random undersampling, Ensemble resampling, Class re-weight แต่ขอข้ามตัวที่เพิ่มข้อมูลที่เป็นการใช้ perfomance ของคอมพิวเตอร์สูงไปก่อนคือตัว Random oversampling และ SMOT (Synthetic Minority Oversampling Technique)
- ทดลองกับ machine learning โดยใช้หลักการ Multi-Fidelity Search ทั้ง grid serch และ random search
- ใช้ hyperband ช่วยในการ allocate resource เป็นการช่วยให้สามารถทำงานบนเครื่องคอมพิวเตอร์ที่ไม่ได้มี resource สูงมาก และประหยัดเวลากว่า gridsearch และ randomsearch
- เลือกดูค่าการวัดผลที่สอดคล้องกับการใช้งานจริงจาก coufusion matrix ในที่นี้ต้องดูค่า recall จาก Precision-Recal Curve แล้วดูค่า Area under Precision-Recall Curve (AUC of PR-curve) and Average Precision (AP) ประกอบกัน
- สุดท้ายจะใช้ค่า recall หลังจากทำการ fit เพื่อ train model เพื่อพิจารณานำไปใช้งานกับ application ที่ต้องการ

---
