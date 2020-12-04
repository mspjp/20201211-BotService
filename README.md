# MS Tech camp #3 \~Azure Bot Service で LINE Bot を作成する\~

ハンズオン担当: 石井峻 (Twitter: [@ShunIshii2](https://twitter.com/shunishii2))


## もくじ

1. Azure Bot Service の作成
2. LINE Messaging API の設定
3. Azure Bot Service と Messaging API を繋げる

## 1. Azure Bot Service の作成

1. Azure で [Bot Service] を開く。
![](https://user-images.githubusercontent.com/39784917/101144048-1bb98900-365b-11eb-9ce7-9a244c11b7e8.png)

2. [追加] から [Web App Bot] を作成
![](https://user-images.githubusercontent.com/39784917/101144859-4b1cc580-365c-11eb-846b-357318796dc0.png)

3. 以下の項目を入力して [作成]
- ボット ハンドル：任意 (mstechcamp3)
- サブスクリプション：任意 (Azure for Students)
- リソースグループ：新規で任意 (mstechcamp3)
- 場所：Japan East
- 価格レベル：F0
- アプリ名：任意 (mstechcamp3)
- ボット テンプレート：Echo Bot (C#)
- App Service プラン/更新：(新規) mstechcamp3/Japan East
- Application Insights：オフ
- Microsoft アプリ ID とパスワード：アプリ ID とパスワードの自動生成

4. 作成された [App Service プラン] へ移動し、[スケールアップ] を選択
![](https://user-images.githubusercontent.com/39784917/101148311-d304ce80-3660-11eb-911b-ba0dff792a26.png)

5. [開発 / テスト] の中の [F1] を選択し、[適用]
![](https://user-images.githubusercontent.com/39784917/101148558-1cedb480-3661-11eb-8031-c8d8c4069c79.png)

## 2. LINE Developers コンソールでチャネルを作成する

LINE Developers の [オフィシャルガイド](https://developers.line.biz/ja/docs/messaging-api/getting-started/#using-console) に従って作成

## 3. Azure Bot Service と Messaging API を繋げる

1. LINE Developers で作成したチャネルの [チャネル基本設定] から、[チャネルシークレット] を取得

2. LINE Developers で作成したチャネルの [Messaging API 設定] から、[チャネルアクセストークン（長期）] を発行

3. Azure で作成したリソースに移動し [チャネル] に接続
![](https://user-images.githubusercontent.com/39784917/101150136-2bd56680-3663-11eb-8287-2ca916dcb87f.png)

4. [その他のチャンネル] から [LINE] を選択
![](https://user-images.githubusercontent.com/39784917/101146424-540e9680-365e-11eb-9b3d-9b4ba2529cfa.png)

5. LINE Developers で取得した [チャネルシークレット] と [チャネルアクセストークン（長期）] を、それぞれ Azure の [チャンネルシークレット] と [チャンネル アクセス トークン] に入力し、[webhook の URL] をコピーして [保存] する
![](https://user-images.githubusercontent.com/39784917/101149508-65f23880-3662-11eb-87c6-f0f43c0b36ff.png)

6. LINE Developers で作成したチャネルの [Messaging API 設定] 内、[Webhook URL] を [編集] し、先ほど Azure でコピーした [webhook の URL] を入力（先頭に https:// を追記）して [更新] し、[Webhook の利用] をオンにする
![](https://user-images.githubusercontent.com/39784917/101151058-786d7180-3664-11eb-83c8-cec100ac59e5.png)

7. [LINE 公式アカウント機能] の [応答メッセージ] を [編集] し、[応答メッセージ] を [オフ] にする
![](https://user-images.githubusercontent.com/39784917/101150625-db123d80-3663-11eb-9bcd-95ac14a9b645.png)
![](https://user-images.githubusercontent.com/39784917/101150884-304e4f00-3664-11eb-8901-1337eb7534a3.png)

完成です！

LINE Developers で作成したチャネルの [Messaging API 設定] に、友達追加用の QR コードがあります。
