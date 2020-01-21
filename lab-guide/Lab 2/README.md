# 演習 2 - セキュリティー定義の付加されたAPIの作成

この演習では、セキュリティー定義が付加されたAPIを作成します。

# 演習 2 - 目的

この演習では、以下の内容を理解できます。

+ APIへのセキュリティー定義の付加方法
+ セキュリティー定義の付加されたAPIのテスト方法
+ 公開されたAPIのURLの確認方法

---


# 2.1	- APIの作成

1.	API Managerにログインしていない場合には、ログインします。

1.	左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)


1.	演習1と同じ手順で、異なる名前のAPIを作成します。`開発`画面で、`追加`メニューから`API`を選択します。

	![](/lab-guide/img/lab1/developmenu-add-api.png)

1.	`ターゲット・サービスから`を選択し、`次へ`をクリックします。

	![](/lab-guide/img/lab1/addapi-from-target-service.png)
	![](/lab-guide/img/lab1/addapi-from-target-service-next.png)

1.	作成するAPIの情報を以下のように入力し、`次へ`をクリックします。指定するターゲット・サービスURLは、`branch`APIと同じです。

	|項目|入力値|備考|
	|-----------------|-----------|-----------------|
	|タイトル|branch-key|APIの名前|
	|バージョン|1.0.0|デフォルトで`1.0.0`が入力されます|
	|基本パス|/branch-key|デフォルトでAPIのタイトルと同じ名前が入力されます|
	|ターゲット・サービスURL|https://apictutorials.mybluemix.net/branches |このAPIが呼び出すターゲットサービスを入力します|

	![](/lab-guide/img/lab1/create-api-from-target-service-wizard1.png)


	> ![][info]
	>
	> `ターゲット・サービスURL` に入力するURLは、店舗情報をGET要求で取得するAPIです。ブラウザーの別のタブを開き、`ターゲット・サービスURL`に入力したURLをコピー&ペーストして、APIのレスポンスが返ることを確認してください。

1.	`キー単位でAPI呼び出しを制限する`にチェックを入れ、`5 / 1 分`の設定に変更して`次へ`をクリックします。

	![](/lab-guide/img/lab2/api-wizard-add-limit.png)

1.	APIが作成されるので、`APIの編集`をクリックします。

	![](/lab-guide/img/lab2/api-wizard-edit-api.png)


1.	左のメニューから`セキュリティー定義`を選択します。デフォルトで`clientID`が定義されています。`clientID`をクリックして詳細を表示します。

	![](/lab-guide/img/lab2/security-def-client-id.png)


1.	`clientID`セキュリティー定義の詳細が確認できます。この定義では、クライアント・アプリケーションごとに発行する`APIキー`を、HTTPヘッダーに、`X-IBM-Client-Id`という名前で受け付けることが定義されています。ヘッダー名は変更することが可能です。
ここでは、このセキュリティー定義をそのまま利用します。

	![](/lab-guide/img/lab2/security-def-client-id-detail.png)


	左上の![](/lab-guide/img/common/return-button.png)をクリックして戻ります。

1.	左のメニューから`セキュリティー`を選択します。`clientID`にチェックが入っているため、このキュリティー定義が有効化されています。

	![](/lab-guide/img/lab2/security-def.png)

	> ![][important]
	>
	> セキュリティー定義に定義しただけでは、その定義が有効にならないことに注意してください。必ず`セキュリティー`メニューで、有効にしたい定義にチェックが入っていることを確認してください。


1.	右上の`保存`ボタン![](/lab-guide/img/common/save-bottun.png)をクリックして、API定義を保存します。

以上でセキュリティー定義が追加できました。

# 2.2	- APIのテスト

1.	演習1で行ったのと同じ手順でAPIのテストを行います。API開発画面上部から`アセンブル`をクリックして、アセンブル画面に移動します。

	![](/lab-guide/img/lab2/move-to-assemble2.png)

1.	アセンブル画面でAPIのテストツールを利用します。画面上のボタン![](/lab-guide/img/common/start-test-button.png)をクリックしてテストツールを表示します。

	![](/lab-guide/img/lab2/start-test-tool2.png)

1.	`APIのアクティブ化`をクリックし、APIをカタログ上にデプロイします。

	![](/lab-guide/img/lab2/activate-api2.png)

1.	操作・メニューで呼び出す操作として`get /`を選択し、`呼び出し`をクリックしてAPIを呼び出します。

	![](/lab-guide/img/lab2/test-tool-invoke-api2.png)

	> ![][info]
	>
	> テストツールに、`clientID`が表示されていることに注目してください。このAPIの呼び出しにはAPIキーが必要となったため、テストツールが自動的にテスト用のAPIキーを発行し、このAPIの呼び出しができるように利用登録までが完了しています。利用登録については、後続の演習で説明があります。


1.	API応答が表示されます。状況コードが`200 OK`と表示されており、応答本文にJSON形式の応答が表示されていることを確認します。

	![](/lab-guide/img/lab2/test-tool-api-response2.png)

1.	ここまでで、セキュリティー定義を付加したAPIAPIの定義とテストが完了しました。右上の`保存`ボタン![](/lab-guide/img/common/save-bottun.png)をクリックして、API定義を保存し、ホームメニューをクリックして、ホームに戻ります。

	![](/lab-guide/img/lab1/move-to-home.png)


# 2.3	- APIの外部ツールからのテスト

1.	演習1、演習2で作成したAPIが、どのようなURLで公開されるのかを確認します。公開されるAPIのエンドポイントは、ゲートウェイ、プロバイダー組織、カタログによって決められます。エンドポイントのURLはカタログの設定で確認できます。API Managerの左のメニューから`管理`を選択します。

	![](/lab-guide/img/common/move-from-home-to-manage.png)

1.	`Sandbox`を選択します。

	![](/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから`設定`を選択します。

	![](/lab-guide/img/lab2/sandbox-manage.png)

1. `APIエンドポイント`を選択すると、このカタログのエンドポイントが確認できます。外部から呼び出しをテストするために、このURLをコピーしておきます。

	![](/lab-guide/img/lab2/sandbox-api-endpoint.png)

	> ![][info]
	>
	> `APIエンドポイント`のルールは以下のようになります。
	> <ゲートウェイのURL>/<プロバイダー組織の名前>/<カタログの名前>


1. まず、演習1で作成した、`branch`APIをテストしてみましょう。APIのURLは以下の形式となります。

	|APIのURL|
	|-----------------|
	|<ゲートウェイのURL>/<プロバイダー組織の名前>/<カタログの名前>/<APIの基本パス>/<呼び出すパス>|

	演習1で作成した`branch`APIは、基本パスが`/branch`、パスは`/`となっています。したがって、前の手順でコピーしたAPIエンドポイントの後ろに、`/branch/`を追加したものが、`branch`APIのURLとなります。

	ブラウザなどの外部ツールを起動し、このURLに対してGET要求でAPIを呼び出してみましょう。パラメーター等は不要です。

	|`branch`APIのURL|
	|-----------------|
	|<APIエンドポイント>/branch/|

	`branch`APIはセキュリティー定義を付加していないため、呼び出しが成功するはずです。

1. 同様に、セキュリティー定義を付加した`branch-key`APIを同様の手順で呼び出してみましょう。

	|`branch-key`APIのURL|
	|-----------------|
	|<APIエンドポイント>/branch-key/|

	今度はエラーとなるはずです。`branch-key`APIには、セキュリティー定義で`APIキー`が必要なため、`401 Unauthorized`エラーが応答として戻ります。
	これは、Chromeブラウザで実行した応答の例です。

	![](/lab-guide/img/lab2/response-401.png)

以上で、演習2は終了です。

---

続いて、 [演習 3 - スクラッチからのAPIの作成](../Lab%203)に進んでください。

[important]: /lab-guide/img/common/important.png "Important!"
[info]: /lab-guide/img/common/info.png "Information"
[troubleshooting]: /lab-guide/img/common/troubleshooting.png "Troubleshooting"
