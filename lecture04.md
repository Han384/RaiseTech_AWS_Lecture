# 【 lecture04 課題：IAM･VPC･EC2･RDS 】

## 《 VPC･EC2･RDSの構築 及び 接続確認 》

### **1. VPCの作成**
![VPCの作成①](https://user-images.githubusercontent.com/88935162/234941123-46a062e5-7add-4c04-aab2-421c81bc8f03.png)
![VPCの作成②](https://user-images.githubusercontent.com/88935162/234941317-617cc96a-2d57-4cd0-8089-9c8def1afa4d.png)

### **2. EC2の作成**
![EC2の作成](https://user-images.githubusercontent.com/88935162/234941602-06bf2902-01e8-4200-a7e9-e67da0793b15.png)  
(EC2のセキュリティグループ)  
![EC2のセキュリティグループ①](https://user-images.githubusercontent.com/131488219/235136080-38832849-9d72-4b24-bdd9-d2e7822fceea.png)
![EC2のセキュリティグループ②](https://user-images.githubusercontent.com/131488219/235136189-d1e0cea5-fcef-4aea-9c35-94703c947465.png)

### **3. RDSの作成**
![RDSの作成](https://user-images.githubusercontent.com/88935162/234941918-1e4b51b1-14b7-4cec-9b43-bb50da3d6312.png)  
(RDSのセキュリティグループ)  
![RDSのセキュリティグループ](https://user-images.githubusercontent.com/131488219/235138299-40ca56a5-997c-4e86-bb3d-926450dbea04.png)

### **4. EC2への接続確認**
![EC2への接続確認](https://user-images.githubusercontent.com/88935162/234943603-6a9c862d-966b-492d-ba70-61127a2e5aaf.png)

### **5. EC2からRDSへの接続確認**
![EC2からRDSへの接続確認](https://user-images.githubusercontent.com/88935162/234942559-d0ffdc46-c98b-4bd7-a997-34f2bfb684fd.png)

---
## ■ 今回の課題から学んだこと
VPC･EC2･RDSの構築後、ローカルPCからEC2へSSH接続。その後、EC2よりRDSへ接続を実施。  
接続確認の中で、EC2からRDSへの接続がうまくいきませんでしたが調べて解決。  
(※原因はRDSのインバウンドのセキュリティグループの設定でした。)  
  
今回、エラーの対処を通じ、エラーが出た場合にいかに原因を突きとめられるか。どの部分に設定等の不足があるか想像できるか。  
エラー特定の観点というか、感覚というものが重要か体感しました。これらは主に経験で培っていくものかと思いますが、  
その前提となる知識も重要となるかと思いますので、その両方を今後身に着けていきたいと思います。
