# 演習 2 - シンプルなAPIの作成

この演習では、既存のAPIを呼び出すAPIをAPI Connectに登録してテストを行います。

# 演習 2 - 目的

この演習では、以下の内容を理解できます。

+ API Managerへのログイン方法
+ 既存APIを呼び出すAPIの定義方法
+ API ManagerでのAPIの開発、単体テストの基本的な操作方法

---


# 2.1	- APIへのセキュリティー定義の追加

1.	API Managerにログインしていない場合には、ログインします。


1.	左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)


1.	演習1で作成した、API`branch`を選択します。

	![](/lab-guide/img/lab2/select-branch-api.png)

1.	左のメニューから`セキュリティー定義`を選択します。デフォルトで`clientIdHeader`が定義されています。`clientIdHeader`をクリックして詳細を表示します。

	![](/lab-guide/img/lab2/security-def-client-id-header.png)


1.	`clientIdHeader`セキュリティー定義の詳細が確認できます。この定義では、クライアント・アプリケーションごとに発行する`APIキー`を、HTTPヘッダーに、`X-IBM-Client-Id`という名前で受け付けることが定義されています。
ここでは、このセキュリティー定義をそのまま利用します。

	![](/lab-guide/img/lab2/security-def-client-id-header-detail.png)



	左上の![](/lab-guide/img/common/return-button.png)をクリックして戻ります。

1.	左のメニューから`セキュリティー`を選択して、`追加`ボタンをクリックします。

	![](/lab-guide/img/lab2/security-add.png)


1.	セキュリティー定義で定義した、`clientIdHeader`が表示されるので、チェックを入れます。

	![](/lab-guide/img/lab2/security-ad-2.png)

以上でセキュリティー定義が追加できました。



以上で、演習1は終了です。

---

続いて、 [演習 3 - APIへの定義の追加](../Lab%202)に進んでください。

[important]: /lab-guide/img/common/important.png "Important!"
[info]: /lab-guide/img/common/info.png "Information"
[troubleshooting]: /lab-guide/img/common/troubleshooting.png "Troubleshooting"
