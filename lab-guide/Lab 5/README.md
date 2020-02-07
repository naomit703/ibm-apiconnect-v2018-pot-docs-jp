# 演習 5 - 開発者ポータルの利用

この演習では、API利用者として、開発者ポータルがどのように利用できるのかを確認します。

# 演習 5 - 目的

この演習では、以下の内容を理解できます。

+ 開発者ポータルの有効化方法
+ アプリケーションの登録方法
+ プランへのサブスクライブの方法
+ 開発者ポータルからのAPIのテスト方法

---

<div style="page-break-before:always"></div>

# 5.1	- 開発者ポータルの有効化

> ![][info]
>
> 開発者ポータルをすでに有効化している場合には、5.2もしくは、5.3に進んでください。

1.	開発者ポータルを有効化していない場合には、有効化します。開発者ポータルはカタログ単位で作成されます。新しいカタログを作成した場合には、開発者ポータルは有効化されていないため、有効化する必要があります。
API Managerにログインしていない場合には、ログインします。

1. API Managerの左のメニューから **管理** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/move-from-home-to-manage.png)

1.	**Sandbox** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから **設定** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab2/sandbox-manage.png)

1.	**管理** メニューから **ポータル** を選択し、右側の **作成** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-menu-click-create.png)

1.	**ポータル・サービス** をプルダウンから選択し、 **作成** をクリックしてポータルサイトを作成します。 **ポータル・サービス** には、その環境で構成されている **ポータル・サービス** が表示されます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-create.png)

1.	開発者ポータルのプロビジョニングが開始され、メッセージが表示されます。数分で開発者ポータルのプロビジョニングが完了すると、プロバイダー組織所有者にメールが送信されます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-after-create.png)

1.	メールに表示されているリンクをクリックして、adminユーザーのパスワード等を設定します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/.png)

	> ![][info]
	>
	>  **admin** ユーザーは、開発者ポータルの画面のデザインを変更したり設定を変更する開発者ポータルの管理ユーザーです。開発者ポータルをAPI利用者として利用するには、後続の手順で開発者組織の作成とユーザー登録をしなければなりません。

# 5.2 開発者組織とユーザー登録

> ![][info]
>
> 開発者組織作成、ユーザー登録をすでに実施している場合には、5.3に進んでください。

1.	API Managerから開発者組織とユーザーを作成します。開発者組織はカタログごとに作成します。API Managerの左のメニューから **管理** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/move-from-home-to-manage.png)

1.	**Sandbox** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/manage-select-sandbox.png)

1. 左側のカタログの管理メニューから **コンシューマー組織** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/sandbox-consumer-org.png)

1. 右の **追加** ボタンから **組織の作成** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/add-create-devorg.png)

1.	組織名やユーザー名、メールアドレス等を入力して、 **作成** をクリックします。ユーザー名や組織名は任意の名前を指定してください。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/add-consumer-org1.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/add-consumer-org2.png)

1.	コンシューマー組織が作成されました。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/added-consumer-org.png)

1.	作成したユーザーで開発者ポータルにログインしてみましょう。開発者ポータルのURLは、開発者ポータルを有効化したメニューで確認できます。API Manager左のメニューから、 **管理** > **Sandbox** > **設定** > **ポータル** と進み、確認します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-url.png)

1.	ポータルのトップページで **サインイン** をクリックし、登録したユーザー名、パスワードでログインします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-top-sign-in.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-login.png)

# 5.3 開発者ポータルへのログイン

1.	開発者ポータルにログインしていない場合には、ログインします。ポータルトップページにアクセスし、右上の **サインイン** をクリックして、ユーザー名、パスワードを入力してログインします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-top-sign-in.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-login.png)

1.	**API製品** をクリックして、公開されている製品を確認してみましょう。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-api-products.png)

1.	公開した製品 **FindBranch** をクリックして確認してみましょう。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/all-products-select-FindBranch.png)

1.	**FindBranch** 製品には、2つのAPIが含まれており、2つのプランが設定した通りに表示されています。プランの詳細を確認するために、 **詳細の表示** をクリックしてみましょう。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/plan-show-detail.png)

1.	プランのレート制限が表示されます。レート制限の表示にマウスのカーソルを合わせると、レート制限の詳細が表示されます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/plan-detail.png)

# 5.4 アプリケーション登録

1.	プランへの利用登録を行うためにアプリケーション登録を行います。アプリケーションを登録すると、APIキーとシークレットがポータル上で発行されます。
上部のメニューから **アプリケーション** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/select-application-tab.png)

1.	**新規アプリケーションの作成** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/create-new-application.png)

1.	タイトルに **SampleApp** と入力し、 **送信** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/input-sampleapp.png)

1.	アプリケーションが登録されると、 **APIキー** と **秘密鍵(シークレット)** が表示されます。シークレットはここで一度しか表示されません。この演習では利用しませんが、必要な場合にはここで今後のためにコピーして保存しておきます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/api-key-and-secret.png)

# 5.5 プランの利用登録

1.	APIを利用するには、プランの利用登録を行う必要があります。 **API製品** タブをクリックし、 **FindBranch** 製品を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/move-to-api-products.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/all-products-select-FindBranch.png)

1.	**Silver** プランに **サブスクライブ(利用登録)** してみましょう。 **Silver** プランの **サブスクライブ** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/click-subscribe.png)

1.	作成した **SampleApp** が表示されるので、 **アプリケーションの選択** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/select-application.png)

1.	内容を確認して **次へ** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/confirm-subscription.png)

1.	**完了** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/subscribe-done.png)

# 5.6 APIのテスト実行

1.	APIをテスト実行してみましょう。 **FindBranch** 製品の画面から **FindBranch** APIを選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/select-find-branch-api.png)

1.	APIの詳細が表示されます。パスの詳細を表示するために、左のメニューから **GET /details** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/select-get-details.png)

1.	APIのURLや要求や応答の例がこの画面から確認ができます。 **試してみる** をクリックして、APIのテストをを行ってみましょう。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/try-it.png)

1.	**クライアントID** に **SampleApp** が表示されていることを確認し、 **送信** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/api-test-request.png)

1.	応答が返ることを確認します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-api-test-response.png)

	> ![][info]
	>
	> 要求のヘッダーに **クライアントID** が挿入されていることを確認してください。指定したアプリケーション名に紐づくクライアントIDをツールが挿入しています。

1.	プランの設定でレート制限を1時間5回までと設定していたので、制限がかかるのかを確認してみましょう。 **送信** ボタンをあと5回クリックしてAPIを呼び出してみてください。
合計6回目に呼び出した際に、以下のようにエラーとなり、レート制限を超えたことにより、APIの呼び出しができなかったことが分かります。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab5/portal-too-many-requests.png)


以上で、演習5は終了です。

---

続いて、 [演習 6 - OAuthセキュリティーの実装](../Lab%206)に進んでください。

[important]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/important.png "Important!"
[info]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/info.png "Information"
[troubleshooting]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/troubleshooting.png "Troubleshooting"
