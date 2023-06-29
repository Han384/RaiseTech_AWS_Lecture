# 【 RaiseTech_AWS_lecture 】
## ■ 概要 / 詳細<br>
- RaiseTech AWSフルコース ( 課題提出用リポジトリ )<br>
- 各講義で課題設定があるものについてはマークダウンファイルにまとめて提出を実施<br>
( 例 ) 第10回講義の課題 ⇨ [lecture10.md](./lecture_task/lecture10/lecture10.md)<br>

【 学習/実践 (済) 内容 】

| 講義 / 課題 |                   課題提出ファイル                    |                                          内容                                          |
| :---------: | :---------------------------------------------------: | :------------------------------------------------------------------------------------: |
|    第2回    |      [lecture02.md](./lecture_task/lecture02.md)      |                   Git/GitHubを用いたチーム開発におけるバージョン管理                   |
|    第3回    |      [lecture03.md](./lecture_task/lecture03.md)      |                    Ruby on RailsによるWebアプリケーションのデプロイ                    |
|    第4回    |      [lecture04.md](./lecture_task/lecture04.md)      |                                   VPC･EC2･RDSの構築                                    |
|    第5回    | [lecture05.md](./lecture_task/lecture05/lecture05.md) | Ruby on Rails サンプルアプリケーションのデプロイ<br>・ELB(ALB) / S3 の構築・構成図作成 |
|    第6回    | [lecture06.md](./lecture_task/lecture06/lecture06.md) |                        証跡・ロギング / 監視・通知 / コスト管理                        |
|    第7回    | [lecture07.md](./lecture_task/lecture07/lecture07.md) |                                    セキュリティ対策                                    |
|   第10回    | [lecture10.md](./lecture_task/lecture10/lecture10.md) |                         インフラ自動化 / IaC / CloudFormation                          | <br> |

【 学習/実践 (予定) 内容 】

|                                       講義 / 課題　内容                                       |
| :-------------------------------------------------------------------------------------------: |
| インフラの自動テスト ( ServerSpec ) ・ CI/CDツール ( CircleCI ) ・ 構成管理ツール ( Ansible ) | <br>

<br>

## ■ 実践内容　( 第5回・第10回の内容を抜粋 )<br>
### 【 第5回：AWS上に Ruby on Rails のサンプルアプリケーションをデプロイ 】<br>
- EC2上にサンプルアプリケーションをデプロイ
  - 組み込みサーバー (Puma) でデプロイ
  - WEBサーバー ( Nginx ) / APサーバー ( Unicorn ) に分けてデプロイ
- ELB (ALB) / S3  を追加・動作確認
- Rails の Active Storage を連携、画像の保存先をS3に設定
- AWS構成図作成

<br>

- デプロイ手順 ( [lecture05.md](./lecture_task/lecture05/lecture05.md) )
- Webアプリケーション ( デプロイ・ブラウザ動作確認 )
![Webアプリケーション-ブラウザ動作確認](./lecture_task/lecture05/images/S3_Rails(ActiveStorage)/browser_check1.png)<br>
- AWS構成図
![構成図](./lecture_task/lecture05/images/Diagram/diagram_lecture05.png)
