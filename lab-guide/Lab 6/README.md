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


1. `サポートされている権限付与タイプ`フィールドで、`リソース所有者 - パスワード`にチェックを入れ、`アクセス・コード`のチェックを外し、`次へ`をクリックします。

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

1. この認証URLとOAuthプロバイダーを利用するに、カタログで有効化します。API Managerの左のメニューから`管理`を選択します。

	![](/lab-guide/img/common/move-from-home-to-manage.png)

1.	`Sandbox`を選択します。

	![](/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから`設定`を選択します。

	![](/lab-guide/img/lab2/sandbox-manage.png)

1. `APIユーザー・レジストリー`を選択し、`編集`をクリックします。

	![](/lab-guide/img/lab6/sandbox-user-registry-edit.png)

1. 利用可能な`APIユーザー・レジストリー`が表示されるので、`AuthURL`にチェックを入れて`保存`をクリックします。

	![](/lab-guide/img/lab6/add-user-registry.png)

1. 次に、`OAuthプロバイダー`を選択し、`編集`をクリックします。

	![](/lab-guide/img/lab6/sandbox-oauth-edit.png)

1. 利用可能なOAuthプロバイダーが表示されるので、チェックを入れて`保存`をクリックします。

	![](/lab-guide/img/lab6/add-oauth-provider.png)

1. 左のメニューの`APIエンドポイント`をクリックして`ゲートウェイURL`をコピーしておきます。後続の手順で利用します。

	![](/lab-guide/img/lab6/api-endpoint.png)

	左上の![](/lab-guide/img/common/return-button.png)をクリックして、管理画面に戻ります。

# 6.2	- OAuthセキュリティーの付加されたAPIの作成

次に既存のAPIにOAuthセキュリティーを追加します。

1. セキュリティーを付加したAPIを作成するために、新たにAPIを作成します。演習3で利用した`findbranch.yaml`を編集して、インポートによりAPIを作成します。`findbranch.yaml`をコピーして、ファイル名を`oauthapi.yaml`に変更して保存します。

1.	`oauthapi.yaml`を開いて、3箇所の文字列`findbranch`を`oauthapi`に変換してファイルを上書き保存します。

	![](/lab-guide/img/lab2/change-oauthapi.png)

1.	演習3で行ったインポートによるAPIの作成と同じ手順でAPIを作成します。左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)

1.	`開発`画面で、`追加`メニューから`API`を選択します。

	![](/lab-guide/img/lab1/developmenu-add-api.png)

1.	`既存のOpenAPI`にチェックを入れて、`次へ`を選択します。

	![](/lab-guide/img/lab3/check-import-api.png)

1.	`参照`ボタンをクリックして、作成した`oauthapi.yaml`ファイルを指定し、`次へ`をクリックします。

	![](/lab-guide/img/lab3/import-from-file.png)

1.	`APIのアクティブ化`にチェックを入れて、`次へ`をクリックします。
	![](/lab-guide/img/lab3/check-activate-api.png)

1.	API定義がインポートされ、要約情報が表示されます。`APIの編集`をクリックします。
	![](/lab-guide/img/lab3/import-api-summary.png)

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

# 6.3	- 製品プランの作成と公開

1.	新規に製品を作成して作成したAPIを公開します。左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)

1. `開発`画面で、`追加`メニューから`製品`を選択します。

	![](/lab-guide/img/lab4/develop-add-product-menu.png)

1.	`新規製品`を選択し、`次へ`をクリックします。

	![](/lab-guide/img/lab4/new-product-next.png)

1.	`タイトル`に`oauth-test-product`と入力し、`次へ`をクリックします。

	![](/lab-guide/img/lab6/input-product-title-oauth.png)

1.	この製品に追加するAPIを選択します。ここでは、`oauthapi`を選択して、`次へ`をクリックします。

	![](/lab-guide/img/lab6/select-api-next-oauth2.png)

1.	`プラン`はデフォルトのまま`次へ`をクリックします。

	![](/lab-guide/img/lab4/product-wizard-plan.png)

1.	次の画面もデフォルトのまま`次へ`をクリックします。

	![](/lab-guide/img/lab4/product-wizard-next.png)

1.	製品の枠が作成されます。`製品の編集`をクリックして製品の詳細画面を表示し、`右上の保存`ボタン![](/lab-guide/img/common/save-bottun.png)をクリックして保存します。

	![](/lab-guide/img/lab4/product-wizard-edit.png)

1.	製品を公開します。左のメニューから`開発`を選択し、`oauth-test-product`製品の右のメニューから`公開`を選択します。

	![](/lab-guide/img/lab2/move-to-develop.png)

	![](/lab-guide/img/lab6/publish-oauth-test-product2.png)

1. 公開先に`Sandbox`を選択して、`公開`をクリックします。

	![](/lab-guide/img/lab4/publish-select-catalog.png)

# 6.4	- 開発者ポータルからのアプリケーション作成と利用登録

1.	開発者ポータルにログインして、上部のメニューから`アプリケーション`をクリックします。

	![](/lab-guide/img/lab5/select-application-tab.png)

1.	`新規アプリケーションの作成`をクリックします。
	![](/lab-guide/img/lab6/create-new-application2.png)

1.	タイトルに`oauth-test-app`と入力し、`送信`をクリックします。
	![](/lab-guide/img/lab6/input-oauth-test-app.png)

1.	アプリケーションが登録されると、`APIキー`と`秘密鍵(シークレット)`が表示されます。シークレットはここで一度しか表示されないため、今後のためにコピーして保存しておいてください。`継続`をクリックします。

	![](/lab-guide/img/lab6/api-key-and-secret2.png)

1.	プランへのサブスクライブを行います。`API製品`タブをクリックし、`oauth-test-product`製品を選択します。

	![](/lab-guide/img/lab5/move-to-api-products.png)

	![](/lab-guide/img/lab6/all-products-select-oauth2.png)

1.	`デフォルトのプラン`プランにの`サブスクライブ`をクリックします。

	![](/lab-guide/img/lab6/click-subscribe-default.png)

1.	作成した`oauth-test-app`が表示されるので、`アプリケーションの選択`をクリックします。
	![](/lab-guide/img/lab6/select-application2.png)

1.	内容を確認して`次へ`をクリックします。
	![](/lab-guide/img/lab6/confirm-subscription2.png)

1.	`完了`をクリックします。
	![](/lab-guide/img/lab6/subscribe-done2.png)

# 6.5	- 開発者ポータルからのAPIのテスト

1.	APIをテスト実行してみましょう。`oauthapi`APIをクリックします。

	![](/lab-guide/img/lab6/select-find-branch-api2-2.png)

1.	APIの詳細が表示されます。パスの詳細を表示するために、左のメニューから`GET /details`を選択します。

	![](/lab-guide/img/lab5/select-get-details.png)

1.	`試してみる`をクリックしします。

	![](/lab-guide/img/lab6/try-it2-2.png)

1.	`クライアントID`に`oauth-test-app`を選択し、`クライアント秘密鍵`には、コピーしておいた、シークレットを入力します。

	![](/lab-guide/img/lab6/apitest-client-id-secret.png)

1.	ユーザー名に`user`、パスワードに`pass`を入力し、スコープ`details`にチェックを入れて、`トークンの取得`ボタンをクリックします。

	![](/lab-guide/img/lab6/get-token2.png)

1. そのまま下にスクロールして`送信`をクリックします。応答が返ることを確認します。




以上で、演習6は終了です。

---


[important]: /lab-guide/img/common/important.png "Important!"
[info]: /lab-guide/img/common/info.png "Information"
[troubleshooting]: /lab-guide/img/common/troubleshooting.png "Troubleshooting"
