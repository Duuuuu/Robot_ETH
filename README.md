# Robot_BTC

Github操作影片:https://youtu.be/xAkl5X1v-Lc

幣安交易所:https://www.binance.com/tw

幣安API Restful:https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md

R package e1071:https://cran.r-project.org/web/packages/e1071/index.html

R package C50:https://cran.r-project.org/web/packages/C50/index.html

    預期工作階段：先完成第一階段，如果有時間再做第二階段和第三階段。
    以敏捷式開發協同方式完成。

    第一階段：
    1. 幣安交易所Restful API取得比特幣相關資料並且輸出成csv或rds 。
    2. 建立市場模型：尋找分批進出場時機，停利停損可以先設定成10%和-5%。

    第二階段：
    1. Twitter Restful API取得交易所對比特幣的文本資料並且輸出成csv或rds 。
    2. 優化市場模型，結合Twitter Restful API：尋找分批進出場時機，停利停損可以先設定成10%和-5%。

    第三階段：
    1. 建立市場模型：尋找適合停利停損的%數。

一、介紹：區塊鏈(Blockchain)：
1. 沒有區塊鏈之前，全球性交易必須要有中央機構、交易所在「中心」做媒合。
2. 區塊鏈1.0，比特幣(Bitcoin;BTC)開創分散式帳本，「去中心化」，讓個人對個人、銀行對銀行，能直接交易。
3. 區塊鏈2.0，以太坊(Ethereum;ETH)以比特幣為基礎，多了智慧合約(Smart Contract)的區塊，可以讓交易合約內容直接寫入。
4. 區塊鏈3.0，則是希望把加密貨幣結合物聯網，並且就區塊鏈原有問題進行改善。
5. 區塊鏈優點：去中心化、交易內容不易被竄改。區塊鏈缺點：礦工有限、交易時資料傳送緩慢。
6. 資料來源: https://www.cw.com.tw/article/article.action?id=5090842

二、加密貨幣：通常以BTC和ETH兩大加密貨幣為主。並且以USDT為計價單位，USDT與美金交易，接近1:1。高風險、高波動、24小時、歷史資訊短(2009年開始)：
1. 基本面：加密貨幣技術特質(乙太幣、萊特幣等)、區塊鏈技術、交易頻率、交易規模、掛牌的交易所、挖礦速度等。
2. 技術面：交易系統（含進出場邏輯、停利停損、加碼減倉、價量、型態、支撐壓力位等）。 
3. 籌碼面：大戶持股比率、虛擬貨幣期貨OI、造市商籌碼。
4. 消息面：ICO加密貨幣發行、加密貨幣交易所成立、法律制定、避險(新興市場爆發貨幣危機)、交易所本身資訊安全度。第一手訊息Twitter、Telegram、Wechat。第二手訊息Google Trend、Google News。

三、研究目的：對已經掛牌在交易所的加密貨幣，制定交易策略：
1. 因為其高風險、高波動的特性，必須嚴格進行風控。
2. 建構虛擬貨幣投資組合(Portfolio)，分散風險。
3. 資金控管。
4. 建立有效的交易系統，提升交易績效。
5. 系統性策略思考（含消息面、技術面），建構介入市場與否SOP。

四、取得即時資料的方式：大致上有兩種：https://github.com/Duuuuu/Robot_BTC/blob/master/reqres.png
1. 透過Restful API(API)，直接取得資訊，通常資料格式會是JSON，不須再額外處理。通常不需要API KEY。但是做交易，就會有API KEY，作為身分驗證；就像，刷信用卡，要有本人簽名。這個就是很典型的Restful API，有發現到網址有我們要求的東西24hr以及交易是BTC對USDT：https://api.binance.com/api/v1/ticker/24hr?symbol=BTCUSDT
2. 透過scrapy，取得網頁原始碼資訊，通常資料格式會是HTML，必須再額外處理。

五、架構圖：幣安交易所、單一加密貨幣(比特幣)、尋找分批進出場時機。做好資金控管，並設定停利停損：https://github.com/Duuuuu/Robot_BTC/blob/master/structure.png
1. 幣安交易所：Restful API：https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md
2. Twitter:Restful API：http://www.dataguru.cn/article-10964-1.html

六、市場模型：
1. 對過去一段時間前面的資料進行迴歸分析或進行訓練，並且把訓練好的模型，拿去測試過去一段時間後面的資料，看最後結果績效是否不錯。https://github.com/Duuuuu/Robot_BTC/blob/master/seg_of_train_test.png
2. Twitter文本分析，這邊可能要對一些關鍵字，給予分數[-1,1]之間，然後對前面幾篇文章進行加權，越接近現在加權越高。W1至W4就是SVM架構。分數越高代表市場越好，分數越低代表市場越不好。https://github.com/Duuuuu/Robot_BTC/blob/master/content_analysis.png






