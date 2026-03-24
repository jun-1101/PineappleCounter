# 鳳梨計數程式（Pineapple Counter）- Java 影像處理

## 1. 專案概述（Project Overview）
本專案使用 **Java 影像處理技術（Image Processing）** 來實作一個簡單的鳳梨計數程式。程式會讀取一張圖片，將圖片轉換為灰階，透過水平掃描方式偵測邊緣，並依據偵測到的特徵估算圖片中的鳳梨數量。

本程式 **沒有使用 Deep Learning（深度學習）或人工智慧模型**，而是使用傳統的影像處理方法，演算法簡單且容易解釋，適合作為基礎作業實作。

---

## 2. 專案目標（Objective）
本程式的主要目標如下：

- 讀取一張圖片檔案（JPG）
- 將彩色圖片轉換為灰階圖片
- 使用像素差異進行邊緣偵測
- 計算符合條件的特徵數量
- 估算圖片中鳳梨的數量

---

## 3. 方法說明（Methodology）

### Step 1：讀取圖片（Image Loading）
程式使用 Java 的 `ImageIO` 類別讀取圖片檔案。

```java
BufferedImage image = ImageIO.read(file);
```

---

### Step 2：灰階轉換（Grayscale Conversion）
每個像素的 RGB（紅、綠、藍）值會被平均，轉換成灰階值。

公式如下：

```
Gray = (R + G + B) / 3
```

灰階圖片可以降低顏色影響，讓邊緣偵測更穩定。

---

### Step 3：邊緣偵測（Edge Detection - 水平掃描）
程式會逐列（Row）掃描圖片，計算相鄰像素之間的亮度差異：

```java
diff = Math.abs(gray[y][x] - gray[y][x - 1]);
```

當差異值大於門檻值（threshold，例如 40）時，就視為一個邊緣（edge）。

---

### Step 4：計算特徵數量（Counting Peaks）
如果某一列中偵測到很多邊緣，就代表該列可能包含鳳梨圖案，因此會增加計數：

```java
if (peaks > 50)
    count++;
```

---

### Step 5：估算鳳梨數量（Estimation）
最後將計算結果除以一個常數（例如 20），得到鳳梨數量的估算值：

```java
finalCount = count / 20;
```

這個數值代表平均一顆鳳梨所對應的特徵列數。

---

## 4. 使用技術（Technologies Used）

本專案使用以下技術：

- Java 程式語言
- BufferedImage 類別
- ImageIO 圖片讀取功能
- 基本影像處理（Image Processing）
- 邊緣偵測（Edge Detection）

本程式 **未使用**：

- Deep Learning（深度學習）
- Machine Learning（機器學習）
- 人工智慧模型（AI Model）

---

## 5. 系統需求（Program Requirements）

執行本程式需要：

- Java JDK 8 或以上版本
- 一張圖片檔案（JPG 格式）

例如：

```
0001.jpg
```

圖片需與 `PineappleCounter.java` 放在同一個資料夾內。

---

## 6. 編譯與執行方式（How to Compile and Run）

### 編譯（Compile）

```
javac PineappleCounter.java
```

### 執行（Run）

```
java PineappleCounter
```

---

## 7. 範例輸出（Example Output）

```
Pineapple count: 48
```

實際結果會依圖片內容與門檻值不同而有所差異。

---

## 8. 限制（Limitations）

本程式屬於簡單的規則式方法，存在以下限制：

- 準確度會受到光線與圖片品質影響
- 如果鳳梨重疊，可能會影響計算結果
- 使用固定除數（/20）可能不適用所有圖片
- 無法自動學習新的圖片特徵

---

## 9. 未來改進方向（Future Improvements）

未來可以進一步改進的方向包括：

- 加入垂直掃描（Vertical Scan）提高準確度
- 使用自動門檻值（Adaptive Threshold）
- 在圖片上畫出偵測到的鳳梨位置（畫圈）
- 使用分群（Clustering）方法讓每顆鳳梨只計算一次

---

## 10. 作者資訊（Author）

學生作業（Student Project）

課程名稱：Java 程式設計 / 影像處理（Java Programming / Image Processing）

