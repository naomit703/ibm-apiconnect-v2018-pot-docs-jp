# 演習 4 - 製品化と公開

この演習では、これまでの演習で作成したAPIを製品化して公開します。

# 演習 4 - 目的

この演習では、以下の内容を理解できます。

+ 製品、プランを定義する方法
+ レート制限を追加する方法
+ 製品の公開方法

---

# 4.1	- 製品、プランの作成

1.	API Managerにログインしていない場合には、ログインします。

1.	左のメニューから`開発`を選択し、開発メニューに進みます。

	![](/lab-guide/img/lab2/move-to-develop.png)

1.	`開発`画面で、`追加`メニューから`製品`を選択します。

	![](/lab-guide/img/lab4/develop-add-product-menu.png)

	> ![][info]
	>
	> `製品`とは、APIをグルーピングして公開する単位です。作成したAPIは製品に含めて公開し、製品単位でライフサイクルを管理します。

1.	`新規製品`を選択し、`次へ`をクリックします。

	![](/lab-guide/img/lab4/new-product-next.png)

1.	`タイトル`に`FindBranch`と入力し、`次へ`をクリックします。

	![](/lab-guide/img/lab4/input-product-title.png)

1.	この製品に追加するAPIを選択します。ここでは、`branch-key`と`FindBranch`を選択して、`次へ`をクリックします。

	![](/lab-guide/img/lab4/select-api-next.png)


1.	`プラン`はあとで編集するので、ここではデフォルトのまま`次へ`をクリックします。

	![](/lab-guide/img/lab4/product-wizard-plan.png)


1.	次の画面もデフォルトのまま`次へ`をクリックします。

	![](/lab-guide/img/lab4/product-wizard-next.png)

1.	製品の枠が作成されます。`製品の編集`をクリックして、設定の確認、編集を行います。

	![](/lab-guide/img/lab4/product-wizard-edit.png)

1.	製品には、どのような設定が含まれるのかを確認してみましょう。まず、`製品のセットアップ`メニューには、製品のタイトルや問い合わせ先など、基本的な情報が含まれています。これらの情報は、製品を公開すると開発者ポータルへ表示されます。

	![](/lab-guide/img/lab4/.png)

1.	左のメニューからプランを選択します。現在ウィザードで作成したデフォルトのプランが1つのみ設定されているので、右の`追加`ボタンをクリックしてプランを追加します。

	![](/lab-guide/img/lab4/menu-plan-add.png)


	> ![][info]
	>
	> `プラン`とは、`製品`の中に定義する、API利用者にAPIの利用登録をさせる単位です。プランごとに、利用可能なAPIやレート制限を変えておくことで、APIの利用可否、呼び出し可能回数を、API利用者(クライアントアプリケーション)ごとに制御できます。

1.	プランのタイトルに`Silver`と入力し、`レート制限`を`5回/1時間`に変更します。`バースト制限`はデフォルトのままにしておきます。下までスクロールして、`保存`をクリックして保存します。

	![](/lab-guide/img/lab4/silver-plan-title.png)
	![](/lab-guide/img/lab4/silver-plan-rate-limit.png)
	![](/lab-guide/img/lab4/plan-edit-save.png)

1.	同様の手順で`Gold`プランを作成します。`レート制限`を`10回/1時間`に変更します。`バースト制限`はデフォルトのままにしておきます。下までスクロールして、`保存`をクリックして保存します。

	![](/lab-guide/img/lab4/gold-plan-title.png)
	![](/lab-guide/img/lab4/gold-plan-rate-limit.png)
	![](/lab-guide/img/lab4/.png)

1.	最初に作成されたデフォルトのプランを削除します。`デフォルトのプラン`の右のメニューをクリックし、`削除`を選択して削除します。

	![](/lab-guide/img/lab4/delete-default-plan.png)

以上で、製品、プランの作成が完了しました。

# 4.2	- 製品の公開

1.	作成したプランを公開します。左のメニューから`開発`を選択して開発メニューに戻ります。

	![](/lab-guide/img/lab4/move-to-develop-from-product.png)

1.	`FindBranch`製品の右のメニューから`公開`を選択します。

	![](/lab-guide/img/lab4/publish-product.png)

	> ![][info]
	>
	> 一覧には、APIと製品の両方がリストされているため、同じ名前のAPIを選択しないように注意してください。

1.	カタログは`Sandbox`が指定されていることを確認し、`公開`をクリックして、製品を公開します。

	![](/lab-guide/img/lab4/publish-select-catalog.png)

# 4.3	- 製品のステータスの確認

1.	公開した製品のステータスを確認してみましょう。カタログの管理画面で確認ができます。左のメニューから`管理`を選択します。

	![](/lab-guide/img/lab4/move-to-manage.png)

1.	公開先のカタログを選択します。ここでは`Sandbox`を選択します。

	![](/lab-guide/img/lab4/select-sandbox.png)

1.	`Sandbox`カタログにデプロイされている製品の一覧が表示されます。先ほど公開した`FindBranch`製品のステータスが`published`になっていることを確認してください。

	![](/lab-guide/img/lab4/all-products.png)

	> ![][info]
	>
	> 一覧には、手動で公開した製品以外にも、テストツールでテストを行った際に、自動的に作成、公開された製品も含まれています。自動で作成された製品には、製品名の最後に`auto-product`という名前がつけられています。

	左上の![](/lab-guide/img/common/return-button.png)をクリックして戻ります。

	以上で、演習4は終了です。

	---

	続いて、 [演習 5 - 開発者ポータルの利用](../Lab%205)に進んでください。

	[important]: /lab-guide/img/common/important.png "Important!"
	[info]: /lab-guide/img/common/info.png "Information"
	[troubleshooting]: /lab-guide/img/common/troubleshooting.png "Troubleshooting"
