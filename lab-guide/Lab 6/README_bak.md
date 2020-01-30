# 演習 6 - OAuthセキュリティーの実装

この演習では、OAuthセキュリティーを実装してテストする方法を確認します。

# 演習 6 - 目的

この演習では、以下の内容を理解できます。

+ ネイティブOAuthプロバイダーの定義方法
+ OAuthで保護されるAPIのセキュリティー定義方法
+ OAuthセキュリティーの定義方法

---

# 6.1	- ネイティブOAuthプロバイダーの作成



1. API Managerにログインしていない場合には、ログインします。

1. まず、Native OAuthプロバイダーでの認証を行うURLを`認証ユーザー・レジストリー`として設定します。左のメニューから`リソース`を選択します。
	![](/lab-guide/img/lab6/select-resource.png)

1. `ユーザー・レジストリー`の画面で、`作成`をクリックします。

	![](/lab-guide/img/lab6/user-registry-create.png)

1. `認証 URL ユーザー・レジストリー`をクリックします。
	![](/lab-guide/img/lab6/select-auth-url-registry.png)

1. 以下を入力して`保存`をクリックして保存します。

	|項目|入力値|備考|
	|-----------------|-----------|-----------------|
	|タイトル|AuthURL|認証URL名前|
	|Display Name|AuthURL|表示名|
	|URL|https://httpbin.org/basic-auth/user/pass|認証サービスのURL|
	|TLSクライアント・プロファイル|TLSプロファイルなし||

	![](/lab-guide/img/lab6/auth-url-define.png)

1. 次に、`OAuthプロバイダー`を設定します。`OAuth プロバイダー`を選択し、`追加`をクリックして `ネイティブ OAuth プロバイダー`を選択します。

	![](/lab-guide/img/lab6/select-native-oauth-provider.png)

1. `タイトル`に`oauthprovider`と入力して`次へ`をクリックします。

	![](/lab-guide/img/lab6/oauth-provider-title.png)


1. `サポートされている権限付与タイプ`フィールドで、`リソース所有者 - パスワード`にチェックを入れ、`次へ`をクリックします。

	![](/lab-guide/img/lab6/oauth-provider-configuration.png)

1. `スコープ`セクションで、上部の`名前`フィールドに `details`と入力し、`説明`フィールドに`Branch details`と入力し、`次へ`をクリックします。

	![](/lab-guide/img/lab6/oauth-provider-scope.png)

1. `ID抽出`に`基本認証`が選択され、`認証`に`AuthURL`が選択され、`許可`設定が`認証済み`に設定されていることを確認して、`次へ`をクリックします。

	![](/lab-guide/img/lab6/oauth-provider-authorize1.png)
	![](/lab-guide/img/lab6/oauth-provider-authorize2.png)

	> ![][info]
	>
	> 前の手順で作成した、`認証URLユーザー・レジストリー`をOAuthプロバイダーの認証に利用するように設定しています。

1. サマリーページが表示されるので、下までスクロールして、`終了`をクリックします。
	![](/lab-guide/img/lab6/oauth-provider-summary.png)

1. `デバッグ応答ヘッダーの有効化`にチェックを入れて、`保存`をクリックします。

	![](/lab-guide/img/lab6/oauth-provider-save.png)

1. このOAuthプロバイダーを利用するに、カタログで有効化します。API Managerの左のメニューから`管理`を選択します。

	![](/lab-guide/img/common/move-from-home-to-manage.png)

1.	`Sandbox`を選択します。

	![](/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから`設定`を選択します。

	![](/lab-guide/img/lab2/sandbox-manage.png)

1. `OAuthプロバイダー`を選択し、`編集`をクリックします。

	![](/lab-guide/img/lab6/sandbox-oauth-edit.png)

1. 利用可能なOAuthプロバイダーが表示されるので、チェックを入れて`保存`をクリックします。

	![](/lab-guide/img/lab6/add-oauth-provider.png

1. 左のメニューの`APIエンドポイント`をクリックして`ゲートウェイURL`をコピーしておきます。後続の手順で利用します。

	![](/lab-guide/img/lab6/api-endpoint.png)

	左上の![](/lab-guide/img/common/return-button.png)をクリックして、管理画面に戻ります。

# 6.2	- APIへのOAuthセキュリティーの追加

次に既存のAPIにOAuthセキュリティーを追加します。

1. これまでの演習で作成した、FindBranchにセキュリティー定義を追加します。左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)

1.	`FindBranch`を選択します。

	![](/lab-guide/img/lab6/select-findbranch-api.png)

1.	`セキュリティー定義`をクリックして、`追加`をクリックします。

	![](/lab-guide/img/lab6/api-security-def-add.png)

1.	以下のように入力し、`保存`をクリックします。

	|項目|入力値|備考|
	|-----------------|-----------|-----------------|
	|名前|oauth||
	|タイプ|OAuth2||
	|OAuth プロバイダー|oauthprovider||
	|フロー|Resource Owner||

	![](/lab-guide/img/lab6/api-security-def-oauth-detail.png)

1.	次に`セキュリティー`をクリックし、定義した`oauth`にチェックを入れ、スコープ`details`にチェックを入れて、`保存`をクリックします。

	![](/lab-guide/img/lab6/api-add-oauth-security.png)

	以上でAPIへのOAuthセキュリティー定義の追加が完了しました。



# 6.3	- 製品の再公開

1.	APIのテストを行ってみましょう。左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)

1.	`FindBranch`APIを選択します。

	![](/lab-guide/img/lab6/select-findbranch-api.png)

1.	上部から`アセンブル`をクリックして、アセンブル画面に移動します。

	![](/lab-guide/img/lab6/lab6-move-to-assemble.png)

1. 画面上のボタン![](/lab-guide/img/common/start-test-button.png)をクリックしてテストツールを表示します。

	![](/lab-guide/img/lab3/assemble-start-test-tool.png)

1.	`製品の再公開`をクリックします。

	![](/lab-guide/img/lab6/api-test-republish-product.png)

# 6.4 - テスト用のアプリケーション作成と利用登録

1.	テスト用のアプリケーションをAPI Manager画面から作成します。左のメニューから、`管理`メニューを右クリックし、新しいタブでリンクを開きます。

	![](/lab-guide/img/lab6/open-manage-menu-in-new-tab.png)


1.	ログイン画面が表示されたら、再度ログインします。左のメニューから`管理`メニューを選択します。

		![](/lab-guide/img/common/move-from-home-to-manage.png)

1.	`Sandbox`を選択します。

	![](/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから`アプリケーション`を選択します。

	![](/lab-guide/img/lab6/sandbox-application.png)

1.	アプリケーションを新規に作成します。`追加`ボタンをクリックし、`作成`を選択します。

	![](/lab-guide/img/lab6/application-add-create.png)

1.	以下のように入力して、`作成`をクリックします。

	|項目|入力値|備考|
	|-----------------|-----------|-----------------|
	|タイトル|oauthapp||
	|OAuth リダイレクト URL (オプション)|https://example.com||
	|コンシューマー組織|`Sandbox Test Organization`にチェック||

	![](/lab-guide/img/lab6/create-app-input.png)
	![](/lab-guide/img/lab6/create-app-create.png)

1.	アプリケーションの資格情報が表示されるので、`クライアント ID`、`クライアント・シークレット`をそれぞれコピーして、保存しておきます。後続の演習で利用します。`OK`をクリックします。

	![](/lab-guide/img/lab6/app-credential-info.png)

1.	作成したテスト用アプリケーションで、製品プランにサブスクライブします。`oauthapp`の右のメニューをクリックして、`サブスクリプションの作成`を選択します。

	![](/lab-guide/img/lab6/sampleapp-create-subscription2.png)

1.	`FindBranch auto product:2.0.0/Default Plan`にチェックを入れて`作成`をクリックします。

	![](/lab-guide/img/lab6/subscribe-to-findbranch-auto2.png)


1.	演習5で登録したアプリケーションをテストする製品に利用登録(サブスクライブ)する必要があります。左のメニューから、`管理`メニューを右クリックし、新しいタブでリンクを開きます。

	![](/lab-guide/img/lab6/open-manage-menu-in-new-tab.png)


1.	ログイン画面が表示されたら、再度ログインします。左のメニューから`管理`メニューを選択します。

		![](/lab-guide/img/common/move-from-home-to-manage.png)

1.	`Sandbox`を選択します。

		![](/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから`アプリケーション`を選択します。

		![](/lab-guide/img/lab6/sandbox-application.png)

1.	このカタログで利用可能なアプリケーションの一覧が表示されます。`SampleApp`の右のメニューをクリックして、`サブスクリプションの作成`を選択します。

	![](/lab-guide/img/lab6/sampleapp-create-subscription.png)

1.	`FindBranch auto product:2.0.0/Default Plan`にチェックを入れて`作成`をクリックします。

	![](/lab-guide/img/lab6/subscribe-to-findbranch-auto.png)

1.	ここで、先ほどのAPIのテスト画面のタブに戻ります。操作フィールドで`get /details`を選択し、`clientId`、`clientSecret`フィールドに、演習5でコピーしておいた`APIキー`と`秘密鍵(シークレット)`を入力します。`ユーザー名`フィールドに user と入力し、`パスワード`フィールドに pass と入力します。

	|項目|入力値|備考|
	|-----------------|-----------|-----------------|
	|操作|get /details||
	|clientId|前の演習でコピーした`APIキー`||
	|clientSecret|前の演習でコピーした`秘密鍵(シークレット)`||
	|ユーザー名|user||
	|パスワード|pass||

	![](/lab-guide/img/lab6/api-test-detail1.png)

1.	OAuth トークンを取得します。ここでは、cURL で以下のコマンドを使用してトークンを取得します。

<APIエンドポイント>/oauthprovider/oauth2/token

curl -k <APIエンドポイント>/oauthprovider/oauth2/token -d "grant_type=password&scope=details&username=user&password=pass&client_id=<APIキー>&client_secret=<秘密鍵(シークレット)>"

curl -k https://apicgw.mycluster-843612-98d9bd8ec23489ff9abfa33c8924325c-0001.jp-tok.containers.appdomain.cloud/potorg-101/sandbox/oauthprovider/oauth2/token -d "grant_type=password&scope=details&username=user&password=pass&client_id=dc3b629792c46f2737f905292ced177a&client_secret=8eb16496599d38e8eb51b15ad282d562"

	![](/lab-guide/img/lab6/.png)

1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)
1.	a
	![](/lab-guide/img/lab6/.png)





ここで、再公開された API のテストに戻る必要があります。現在開いているブラウザー・タブを閉じて、再公開した API のテストに戻ります。

「操作」フィールドで、「get /details」を選択します。

「clientId」フィールドに、以前に作成したクライアント ID を入力します。
「clientSecret」フィールドに、以前に作成したクライアント・シークレットを入力します。

「ユーザー名」フィールドに user と入力します。「パスワード」フィールドに pass と入力します。

OAuth トークンを取得します。ここでは、cURL で以下のコマンドを使用してトークンを取得します。

curl -k https://gateway_url/org_name/sandbox/mainprovideroa/oauth2/token -d "grant_type=password&scope=details&username=user&password=pass&client_id=app_client_id&client_secret=app_client_secret"

「explorer_access_token」フィールドにアクセス・トークンを入力するか貼り付けます。以下にトークンの例を示します。

AAIgMzU4MjRmMjY0NmY3OTllZjRjM2Y3OWU1ZDQwZGYwYWOxkwNYTnIxWaHu8Htf1OUAQUEGl3TLJVHayXjPJE5Rxd7clNdBEYRAEkuHIWX8hR2KF4AA9_SuOCNxJsETDaiJ

「呼び出し」をクリックします。URL が組み込まれている黄色いエラー・ボックスが表示される場合があります。この URL をクリックして、ブラウザー証明書エラーをオーバーライドします。

呼び出し」を再度クリックします。応答にはブランチ・データが含まれています。


以上で、演習6は終了です。

---

続いて、 [演習 7 - ](../Lab%207)に進んでください。

[important]: /lab-guide/img/common/important.png "Important!"
[info]: /lab-guide/img/common/info.png "Information"
[troubleshooting]: /lab-guide/img/common/troubleshooting.png "Troubleshooting"
