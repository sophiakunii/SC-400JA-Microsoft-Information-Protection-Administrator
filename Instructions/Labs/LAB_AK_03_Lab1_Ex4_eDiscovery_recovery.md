# ラボ 3 - 演習 4 - 復元に電子情報開示を使用する

この演習では、Contoso Ltd. のコンプライアンス管理者 Joni Sherman のロールを実行します。この組織はテキサスにあり、地元の法律を守るために保持ポリシーを実装する必要があります。「Uniform Preservation of Private Business Records Act」(事業に関する非公開記録の統一保存に関する法律) では、記録を法律の下で違反行為とならずに破棄することができると規定されています。この法律を守るために、組織は、すべてのアイテムを組織内で 3 年間保持するための保持計画を作成しました。

### タスク 1 – 電子情報開示ケースの作成

この演習では、電子情報開示ケースを作成し、Megan Bowen が送信した Mark 8 Project に関する情報が含まれるメールの検索を開始します。法務部は、この情報に対するコンプライアンス レビューを要求しました。

1. Client 1 VM (LON-CL1) には **lon-cl1\admin** アカウントでログインし、Microsoft 365 には **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (ZZZZZZ はラボ ホスティング プロバイダーから支給された固有のテナント ID) としてログインしておく必要があります。  Joni のパスワードは、ラボ ホスティング プロバイダーから支給されます。 

2. **Microsoft Edge** で、**https://compliance.microsoft.com** に移動して、**Joni Sherman** として Microsoft 365 コンプライアンス ポータルにログインします。

3. ポータルでは、左側のナビゲーション ペインで、「**電子情報開示**」を展開し、「**標準**」を選択します。

4. 「**電子情報開示（標準）**」ページで「**+ ケースを作成**」を選択します。

5. **ケース名**フィールドに「*Mark 8 Project Case*」と入力し、「**ケースの説明**」に「*このケースは、Mark 8 Project に関する Megan Bowen のメールを評価するために使用されます。*」と入力して、「**保存**」を選択します。

6. 「**電子情報開示（標準）**」ページで、「**Mark 8 Project Case**」をダブルクリックして、ケースを開きます。

7. 「ケース」ビューで、「**検索**」タブを選択します。

8. 「**+ 新しい検索**」を選択して、新しい検索を開始します。

9. 「**名前と説明**」ページで、「**名前**」欄に「*Mark 8 Project*」と入力し、「**次へ**」を選択します。

10. 「**場所**」ページで、「**Exchange メールボックス**」を「**有効**」にし、「**ユーザー、グループ、チームを選択**」を選択します。

11. 「**Exchange メールボックス**」ダイアログで、「*Megan Bowen*」を検索し、Megan のメールボックスを選択します。  「**完了**」を選択します。

12. 「**場所**」ページで、「**オンプレミス ユーザー用にアプリ コンテンツを追加します。**」チェックボックスをオフにして、「**次へ**」を選択します。

13. 「**検索条件の定義**」ページで、「**キーワード**」欄に 「*Mark 8*」と入力し、「**次へ**」を選択します。

14. 「**検索の確認と作成**」ウィンドウで、「**送信**」を選択します。

15. 検索を作成したら、「**完了**」を選択します。

電子情報開示ケースが正常に作成され、Megan Bowen が送信または受信した、Mark 8 Project に関する情報が含まれるすべてのメールが検索されました。

### タスク 2 - レコード管理と電子情報開示マネージャーのアクセス許可を割り当てる

このタスクでは、タスク 1 で見つけたデータを、法務部に提供する PST ファイルにエクスポートする準備をします。最初に、レコード管理ロールをコンプライアンス管理者に割り当てる必要があります。これを行わないと、検索結果をエクスポートすることができません。

1. Client 1 VM (LON-CL1) に **lon-cl1\admin** アカウントでログインします。

2. **Microsoft Edge** で、**https://compliance.microsoft.com** に移動して、**MOD 管理者**として Microsoft 365 にログインします。  Joni Sherman としてサインアウトする必要がある場合があります。 

3. 左側のナビゲーション ウィンドウで、「**Roles&scopes**」を選択し、「**アクセス許可**」を選択します。「**Microsoft Purview ソリューション**」で、「**役割**」を選択し、 「**Records Management**」を選択します。

4. 「**Records Management**」のポップアップ ウィンドウで、「**編集**」を選択します。

5. 「**役割グループのメンバーの編集**」ページで、「**ユーザーの選択**」を選択します。
 
6. 「**ユーザーの選択**」のポップアップ ウィンドウで「**Joni Sherman**」を検索し、名前の前にあるチェックボックスを選択して、「**選択**」を選択します。

7. メンバーが追加されていることを確認したら、「**次へ**」を選択します。

8. 「**保存**」を選択し、更新を確認した後、「**完了**」を選択します。  

9. Joni が将来のラボで電子情報開示データをエクスポートできるように、**eDiscovery Manager** (電子情報開示マネージャー) のロールに対して手順 3 から 8 を繰り返します。

コンプライアンス管理者に、検索結果をエクスポートしてレコード管理タスクを実行するアクセス許可が正常に付与されました。アクセス許可がユーザーに適用されるまで最大 60 分かかる場合がありますが、次のタスクに進むことができます。

### タスク 3 - 電子情報開示ケースからのデータのエクスポート

このタスクでは、タスク 1 で見つけたデータをエクスポートする準備をして、法務部に提供できるようにします。  アクセス許可がご利用のテナントで使用可能となるまでに、最大 60 分かかる可能性があることを覚えておいてください。

★必ずLON-CL1から操作してください★

1. Client 1 VM (LON-CL1) に **lon-cl1\admin** アカウントでログインしておきます。

2. **Microsoft Edge** で、**https://compliance.microsoft.com** に移動して、**Joni Sherman** として Microsoft 365 コンプライアンス ポータルにログインします。

3. **Microsoft 365 コンプライアンス** ポータルの左側のナビゲーション ペインで、「**電子情報開示**」を展開し、「**標準**」を選択します。

4. **Mark 8 Project case**をクリックして、ケースを開きます。

5. 「**検索**」タブに移動し、「**Mark 8 Project**」を選択します。

**ヒント:** 電子情報開示検索にデータがない場合は、検索のパラメーターを検討してください。  以前のラボでは、Megan に *Mark 8* プロジェクトについてのメールを送信してもらいましたか?  検索のキーワードを、Megan のメールボックスにある既存のメールのいずれかの用語に変更することを検討しない場合。  たとえば、「プランナー」という用語は通常、Megan の既存のメールのいくつかに表示されます。  エクスポートで処理を行うには、検索にデータが含まれている必要があります。

6. 「**Mark 8 Project**」ダイアログで、「**操作**」ボタン ドロップダウンを選択し、「**結果のエクスポート**」を選択します。

7. 「**結果のエクスポート**」ペインの「**出力オプション**」で、オプションを確認します。  「**エクスポート**」を選択します。

★本手順の操作は役割が割り当てられた直後では動作しない場合があります。その場合は後ほど改めて操作を行ってください★

8. 「**Mark 8 Project** 検索」ペインを閉じます。search pane.  

9. ケース画面から「**エクスポート**」タブを選択します。  作成したエクスポートをダブルクリックします。

10.  「エクスポート」ペインの「**エクスポートキー**」で、「**クリップボードにコピー**」を選択し、「**結果のダウンロード**」を選択します。
  
11.  プロンプトが表示されたら、ブラウザーで「**開く**」を選択して、電子情報開示エクスポート ツールをインストールし、「**インストール**」を選択します。

12.  表示されるダイアログ ボックスで、前にクリップボードにコピーしたキーを貼り付けます。  ファイルをダウンロードするのに適した場所を選択します。  「**開始**」を選択します。

見つけたデータを正常にエクスポートしました。

### タスク 4 - メールボックスでの検索と消去の実行

調査によって何人かのユーザーがフィシング メールを受信したことがわかり、あなたは、環境内のすべてのメールボックスでこのようなメールを削除する仕事を任せられました。

★必ずLON-CL1から操作してください★

1. Client 1 VM (LON-CL1) に **lon-cl1\admin** アカウントでログインしておきます。

2. **Microsoft Edge** で、**https://compliance.microsoft.com** に移動して、**Joni Sherman** として Microsoft 365 にログインします。

3. コンプライアンス センターの左側のナビゲーション ペインで、「**コンテンツの検索**」を選択します。

4. 「**+ 新しい検索**」を選択します。

5. 「**名前と説明**」ウィンドウで、「**Phishing mail removal**」と入力し、「**次へ**」を選択します。

6. 「**場所**」セクションで、「**特定の場所**」を選択し、「**Exchange メールボックス**」を選択して「**有効**」に切り替え、「**次へ**」を選択します。

7. 「**検索条件の定義**」ページで、「**キーワード**」フィールドに、「*From:phishingmail@outlook.com AND subject:"Password changed"*」と入力して、「**次へ**」を選択します。
★ここでの検索条件は結果が0件になるため、検索結果が確認できる検索条件として「*subject:"urgent"*」と入れていただくことをお勧めします。★

8. 「**検索の確認と作成**」ウィンドウで、「**送信**」を選択します。「**完了**」をクリックします。

9. 検索を作成後、消去を開始するには、「**セキュリティ & コンプライアンス PowerShell**」を使用する必要があります。スタート メニューで、管理者として **Windows PowerShell** を実行することを選択します。

10. 「**PowerShell**」ウィンドウで、次のコマンドレットを使用して、 **MOD 管理者(admin@...)** としてサインインします。

	`Connect-IPPSSession`

11. **PowerShell** ウィンドウで、次のコマンドを使用します。

	`New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete`

12. PowerShell に「Yes」の「**Y**」を入力し、操作を確定します。

特定のメールを探すための新しいコンテンツ検索を正常に作成し、ユーザーのメールボックスからフィッシング メールを削除するために消去操作を行いました。消去操作は、組織の**管理者ロール**のメンバーのみ行うことができ、コンプライアンス管理者はこれに該当しません。

# ラボ 3 - 演習 5 に進みます。
