---
kind: faq
title: JIRA とのインテグレーションを設定しましたが、イベントやチケットはどのように作成されるのですか？
---

## コンフィギュレーション

Datadog と JIRA とのインテグレーションが設定されると、JIRA タイル内で定義された 'チケットタイプ' に基づき、どの問題を JIRA から取得して送信するかを Datadog のインテグレーションが決定します。
{{< img src="integrations/faq/create_ticket.png" alt="create_ticket" >}}

上の画像では、作成されたチケットタイプ 'jira-test2-task' があるのが確認できます。このセクションを展開すると、次の画面が表示されます。
{{< img src="integrations/faq/jira_ticket_type.png" alt="jira_ticket_type" >}}

こちらのフィールドセットでは、Datadog のインテグレーションが JIRA とどのようにやり取りするかを定義します。'Project Key' フィールドは、このタイルがどの JIRA プロジェクトを参照するかを決定する一方、'Issue Type' フィールドは、所定のプロジェクトボードから送信・取得される JIRA の課題タイプを指定します。'Tags' フィールドはオプションですが、JIRA から取得されるイベントにタグをアタッチしたい場合は、ここで Datadog タグを割り当てることができます。

'Required Fields' フィールドは、実は 'Project Key' と 'Issue Type' を入力し、一度チケットを保存した後にのみ表示される点がやや異なります。この 'Required Fields' セクションでは、JIRA タイル上部にリストアップされている値 (ドル記号で始まる値) を追加できます。

より具体的に説明すると、上で定義したチケットタイプは、プロジェクトキーが 'TEST2' の JIRA プロジェクトから、JIRA の課題タイプ 'タスク' に該当するものを送信・取得します。

## Datadog から JIRA へ

DataDog では、@ を使った通知を利用してチケットタイプを参照し、JIRA にプッシュすることができます。つまり、モニターを定義して、モニターのメッセージ内で @jira-test2-task を参照した場合、モニターがアラートを出すたびに、プロジェクトキーが 'TEST2' の JIRA プロジェクト内に 'タスク' タイプの課題を作成します。

## JIRA から Datadog へ

キー 'TEST2' で指定されたプロジェクトに関して JIRA で作成された 'タスク' タイプの課題はすべて、Datadog イベントストリームに取り込まれ、インテグレーションタイルで定義したタグが適用されます。

## 重要

* Datadog のインテグレーションは約 5 分ごとに JIRA をスクレイピングしますが、Datadog 内に表示されるまでの時間は、課題タイプによって変わる可能性があります。一般的には、'ストーリー' などの大きめの課題タイプは、'タスク' などの小さめの課題タイプよりも取得に時間がかかります。
* 1 つのプロジェクトから複数の課題タイプを取得することも、複数のプロジェクトから 1 つの課題タイプを取得することも可能です。
* 利用可能なタグは、インテグレーションタイルで各チケットタイプ用に定義したタグのみとなります。
* インテグレーションの構成に関する操作やエラーは、すべて Datadog イベントストリームに表示されます。