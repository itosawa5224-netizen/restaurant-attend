# 飲食店アテンド業務（現状分析／As-Is）

業務分析により作成した業務フロー図を以下に示す。

```mermaid

flowchart TD
    
    subgraph Customer [利用客]
        Start([受付<br>]) --> WriteBoard[受付情報を記入する]
        WriteBoard --> Wait[待機スペースで待つ] 
        Wait --> Respond[呼び出しに応答する] & WaitCancel[キャンセル]
        MoveToSeat[席へ移動する]
        MoveToSeat --> End([着席])
    end



    subgraph Board [ウェイティングボード（紙）]
        BoardData[(待機リスト<br>名前・人数〔大人/子ども〕)]
        BoadDelete[(【消去】<br>待機情報を消去)]
        BoardUpdated[(【更新】<br>案内済み消し込み)]
    end

    Customer ~~~ Board ~~~ Leader ~~~ Hall 
    WriteBoard --> BoardData
    BoardData -.-> CheckBoard
    WaitCancel --> BoadDelete
    CrossOut -.-> BoardUpdated




    subgraph Leader [フロアリーダー]
        CheckBoard[待機客の<br>受付順・人数構成を確認する]
         --> CheckCleanSeat[片付け済みの空席状況を確認する]
         --> Node(( ))
         --> HasEmptySeat{案内可能な<br>空席があるか？}

        HasEmptySeat -- Yes（空席あり） --> SelectSeat[空席から<br>案内する席を選択する] 
        HasEmptySeat -- No (空席なし) --> OderSeat[片付け最優先の席を指示出し]
        
        SelectSeat --> DecideSeat
        DecideSeat[案内席の決定] 
         --> CallCustomer[店頭で名前・人数を呼び出す]

        OderSeat --> DecideSeat
        CallCustomer ~~~ CrossOut[該当行に案内済みの線を引く]
        CallCustomer --> CrossOut
        GuideSeat[席へ先導する]

    end

    CrossOut ~~~ BoardUpdated ~~~ Respond
    CheckBoard ~~~ Wait
    CallCustomer --> Respond
    Respond --> GuideSeat
    
    GuideSeat --> MoveToSeat




    subgraph Hall [ホールスタッフ]
        Bussing[【バッシング】<br>退店後の片付け・<br>テーブルリセットを行う]
        %%-->
        SeatReady[完了]
    end

    Bussing -.-> State
    State -.-> SeatReady

    SeatReady -.口頭共有.-> CheckCleanSeat
    CheckCleanSeat -.目視確認.- State
    


    subgraph State [座席状況]
        direction TD
        SeatMax[(満席<br>【空席】:なし<br>【片づけ可能席】:なし <br>【案内可能席】:なし)]
         -->
        SeatStandby[(空席なし<br>【空席】:なし<br>【片づけ可能席】:あり <br>【案内可能席】:なし)]
         -.OR.-
        SeatEmpty[(空席あり<br>【空席】:あり<br>【片づけ可能席】:あり/なし <br>【案内可能席】:なし)]
         -.OR.-
        SeatAvailable[(案内可能<br>【空席】:あり<br>【片づけ可能席】:あり/なし <br>【案内可能席】:あり)]
        
    end 
    
    
    
    

```

## 発生条件（トリガー）：

満席後、来店客が店頭のウェイティングボードに記入した時点

## 始点・終点：

• 始点：受付（来店〜ボード記入完了）\
• 終点：着席（最終的な案内先テーブルへの着席完了）

## ウェイティングボードの記入項目：

名前(カナ)、人数、大人/子供の区別、備考

## 例外処理（フロー図無反映）：

1. 先頭人数と席が不一致の場合\
（待機順を前後させて案内可能な組を優先）
2. 呼び出し時に不在の場合\
（ボードに不在印をつけ、次の待機組へ進む）
3. 席へ先導後に別の席を希望された場合\
（空席再確認・テーブルリセットのうえ再誘導）
