# 演習 3 - インポートによるAPIの作成

この演習では、yamlファイルのインポートによりAPIを作成します。

# 演習 3 - 目的

この演習では、以下の内容を理解できます。

+ インポートによるAPI作成の方法
+ API設計における **パス** 、および、 **定義** の設定方法

---

<div style="page-break-before:always"></div>

# 3.1	- yamlファイルのダウンロード

1.	インポートするyamlファイルをダウンロードします。以下のURLのテキストをローカルのファイルにコピーして、 **findbranch.yaml** という名前で保存します。

	+ https://www.ibm.com/support/knowledgecenter/ja/SSMNED_2018/com.ibm.apic.apionprem.doc/findbranch_v6.txt

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/masterhttps://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/copy-yaml.png)

# 3.2	- APIの作成

1.	API Managerにログインしていない場合には、ログインします。

1.	左のメニューから **開発** を選択し、開発メニューに進みます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab2/move-to-develop.png)

1.	**開発** 画面で、 **追加** メニューから **API** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab1/developmenu-add-api.png)

1.	**既存のOpenAPI** にチェックを入れて、 **次へ** を選択します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/check-import-api.png)

1.	**参照** ボタンをクリックして、ローカルに保存した **findbranch.yaml** ファイルを指定し、 **次へ** をクリックします。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/import-from-file.png)

1.	**APIのアクティブ化** にチェックを入れて、 **次へ** をクリックします。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/check-activate-api.png)

1.	API定義がインポートされ、要約情報が表示されます。 **APIの編集** をクリックします。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/import-api-summary.png)

1.	定義されているAPIの情報を確認してみましょう。 **タイトル** は **FindBranch** です。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-title.png)

1.	下にスクロールして、 **基本パス** を確認します。 **/findbranch** となっています。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-basepath.png)

1.	左のメニューから **セキュリティー定義** と **セキュリティー** を確認します。 **セキュリティー定義** に **clientID** が設定されており、 **セキュリティー** メニューで、 **clientID** にチェックが入っています。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-security-def.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-security.png)

1.	左のメニューから **パス** を確認します。パスは **/details** のみが設定されています。 **/details** をクリックしてパスの詳細を確認します。
	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-path.png)

	> ![][info]
	>
	> APIのURLは、 **<カタログごとのAPIエンドポイント><基本パス><パス>** となります。

1.	**/details** パスでは、操作として、 **GET** 操作のみが設定されています。このパスではGET要求のみ受け付けられます。操作 **GET** をクリックして詳細を表示します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-path-detail.png)

1.	この **GET** 操作に必要なパラメーターなど、追加のオプションを設定できます。ここではパラメーターは設定されていません。応答の **スキーマ** に **branch** と設定されています。 **branch** のデータ構造は、 **定義** で設定されているので後続の手順で確認します。ここでは、特に変更を加えずにこのまま利用します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-get-detail.png)

1.	左上の![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/return-button.png)を2回クリックして、API設計画面に戻ります。

1.	API設計画面の左のメニューから **定義** を選択します。 **定義** では、APIの要求や応答のペイロードのデータ構造を定義できます。 **address** をクリックして詳細表示します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-def1.png)

1.	定義 **address** には、5つの項目がstring形式で定義されていることが分かります。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-def-address.png)

1.	左上の![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/return-button.png)をクリックして、 **定義** の画面に戻ります。次に **branch** をクリックして詳細表示します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-def-def2.png)

1.	**ソース・ビューにナビゲート** をクリックして、ソースを表示し、 **definitions** に定義されているbranchオブジェクトの構造を確認します。
	 **branch** オブジェクトには、 **address** 、 **type** 、 **id** という3つのプロパティー(項目)があります。 **address** プロパティーは、先ほど確認した **address** 定義を参照しています。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-branch-navigate-to-source.png)

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/definitions-branch.png)

1.	上部の **設計** をクリックして、設計画面に戻ります。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/move-to-design.png)

1.	左のメニューから **プロパティー** 選択して確認します。プロパティーには、演習1と同様に **target-url** が設定されています。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-property.png)

1.	ここまでで、APIのインターフェースの設計メニューの確認が終わりました。次に、上部の **アセンブル** をクリックして **アセンブル** 画面に移動し、APIの処理内容を確認します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/move-to-assemble3.png)

1.	**アセンブル** 画面では、 **invoke** ポリシーが配置されており、 **invoke** ポリシーのプロパティーには、URLに **$(target-url)** が設定されています。呼び出すURLとしては、APIの **設計** 画面で確認したプロパティー **target-url** に設定されている値が利用されます。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/assemble-invoke.png)

# 3.3	- APIのテスト

1.	演習1、演習2と同様の手順でAPIのテストを行ってみましょう。画面上のボタン![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/start-test-button.png)をクリックしてテストツールを表示します。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/assemble-start-test-tool.png)

1.	**製品を再公開** し、呼び出す操作を選択して、 **呼び出し** をクリックしてAPIをテストしてみましょう。応答が正しく返ることを確認してください。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab3/api-test-response.png)

1.	右上の **保存** ボタン![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/save-bottun.png)をクリックして、API定義を保存し、ホームメニューをクリックして、ホームに戻ります。

	![](https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/lab1/move-to-home3.png)

以上で、演習3は終了です。

---

続いて、 [演習 4 - 製品化と公開](../Lab%204)に進んでください。

[important]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/important.png "Important!"
[info]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/info.png "Information"
[troubleshooting]: https://github.com/naomit703/ibm-apiconnect-v2018-pot-docs-jp/raw/master/lab-guide/img/common/troubleshooting.png "Troubleshooting"
