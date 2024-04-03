# Murmurcat funding rate rank
![image](https://github.com/NorthBei/funding-rate-rank/assets/15665709/31c032ba-1354-488e-9eb2-fa6609ee950a)


## Project Intro

### Introduction

Funding Rate Rank(資金費率排名)是呢喃貓的小組專案，小組專案的目標主要是透過做幣圈的小工具，讓參與的成員由淺入深的一起學習寫程式，提高呢喃貓的社群的技術夥伴比例，未來如果有任何幣圈的套利機會，技術夥伴就可以在社群和大家起同協作，創造出更高的價值！

這個專案由呢喃貓的成員們一同發想、一起動手開發，資金費率機器人會定時自動收集各個交易所的幣價、資金費率資料，從各大交易所中找出最適合透過資金費率套利的幣別&交易對，讓大家套利順利、賺大錢😆😆


### 資金費率的規則

- 當做多的人多於做空的人時，多軍要向空軍支付資金費率，此時資金費率為正數。

正數的資金費率代表市場中多頭（做多）的交易者支付給空頭（做空）交易者的費用。這可能意味著市場多頭氣氛較強，多頭交易者願意支付一定的費用以保持其倉位，而空頭交易者則可以受益於這種情況。

- 當做空的人多於做多的人時，空軍要向多軍支付資金費率，此時資金費率為負數。

負數的資金費率則代表相反的情況，即空頭交易者支付給多頭交易者的費用。這可能意味著市場空頭氣氛較強，空頭交易者願意支付費用以保持其倉位，而多頭交易者可能會從這種情況中獲益。



這樣規定的邏輯是讓市場上強勢一方的持倉成本增加，有助於合約價格與現貨價格保持較小的價差，避免其中一方過於強勢甚至操縱市場。

![image](https://github.com/NorthBei/funding-rate-rank/assets/15665709/13a660e7-a3b4-4da0-9bc1-58624279caaf)

以幣安的交易頁面為例，資金費率和下一次收取資金費率時間的倒計時會如上圖一樣顯示在頁面上。資金費率的計算公式為：

資金費率 = 持有的倉位總價值 x 資金費率比例

例如此時你持有 10000 USDT 的 ETH 永續合約倉位，在下次收取資金費率的時候，你將支付10000 x 0.0027% = 0.27 USDT 的資金費率。


### Screenshots/Film

![image](https://github.com/NorthBei/funding-rate-rank/assets/15665709/aab4e557-7b2c-4794-95ed-f5518d392936)


## Development Instruction

### Environment

|Service|Version|
|-|-|
|Node.js|v18.18.2|
|yarn| v9.8.1|

### Environment Variables

Rename the `.env.local.example` to `.env.local`, and get the env var from Firebase service

|Service|Env var|
|-|-|
|Firebase|VUE_APP_FIREBASE_API_KEY|
|Firebase|VUE_APP_FIREBASE_AUTH_DOMAIN|
|Firebase|VUE_APP_FIREBASE_PROJECT_ID|
|Firebase|VUE_APP_FIREBASE_STORAGE_BUCKET|
|Firebase|VUE_APP_FIREBASE_MESSAGING_SENDER_ID|
|Firebase|VUE_APP_FIREBASE_APP_ID|

### Getting Started


Install packages & Run the development server:

```zsh
npm run install
npm run dev
```

### Project setup

Install all packages
```zsh
npm run install
```

### Start Development

Run development web server at http://localhost:8080 for development

```zsh
npm run serve
```

### Build Production

Run below command to build this project.

```zsh
npm run build
```

## Reference
- [資金費率是什麼？負資金費率代表什麼？如何通過資金費率套利？](https://coindada.com/article/what-is-funding-rate/)
