# 【 CloudWatch：アラーム作成 / 設定 手順】

1. [アラーム作成 ( アラーム状態分 )](#1-アラーム作成--アラーム状態分-)
2. [アラーム作成 ( OKアクション分 )](#2-アラーム作成--okアクション分-)

<br>

( ※今回は、ELB (ALB) の `Unhealthy` を検知してアラーム発報 ( メール通知 ) する設定を2つ作成 ：アラーム状態 / OKアクション )

<br>

---

<br>

## 1. アラーム作成 ( アラーム状態分 )

<br>

《 アラーム名 》 `ALB_UnHealthyHostCount_Alarm`

<br>

- Cloudwatch - [ アラーム ] - [ アラームの作成 ] を押下

- メトリクスの選択<br>
( [ ApplicationELB ] - [ AppELB 別、AZ 別、TG 別メトリクス ] - メトリクス名 [ UnHealthyHostCount ] を選択 )

- メトリクスと条件の指定　( 下図の通りに設定 ) - [ 次へ ]を押下
![alarm_setting01.png](./images/cloudwatch/alarm_setting01.png)
![alarm_setting02.png](./images/cloudwatch/alarm_setting02.png)

- アクションの設定　( 下図の通りに設定 )
![alarm_setting03.png](./images/cloudwatch/alarm_setting03.png)

- [ 新しいトピックの作成 ] 後、 [ SNSコンソールで表示 ] を押下<br>
( ※遷移先画面で [ サブスクリプション ] タブ - [ ステータス ( 保留中の確認 ) ] を確認 )　(下図参照)<br>
![alarm_setting04.png](./images/cloudwatch/alarm_setting04.png)


- 通知先として設定したメールアドレスに同意承認のメールが来るため、承認を実施

- SNSコンソール画面 ( [ サブスクリプション ] タブ - [ ステータス ( 確認済み ) ] を確認)　(下図参照)<br>
![alarm_setting05.png](./images/cloudwatch/alarm_setting05.png)

- アクションの設定 - [ 次へ ] を押下

- 名前と説明を追加　( 任意のアラーム名・アラームの説明を明記 ) - [ 次へ ]を押下
![alarm_setting06.png](./images/cloudwatch/alarm_setting06.png)

- プレビューと作成 - [ アラームの作成 ] を押下

<br>

---

<br>

## 2. アラーム作成 ( OKアクション分 )

<br>

《 アラーム名 》 `ALB_UnHealthyHostCount_Alarm_OK`<br>

<br>

( ※前の手順で作成した上記アラーム  `ALB_UnHealthyHostCount_Alarm` をコピーして作成 )<br>

<br>

- Cloudwatch - [ アラーム ] - [ `ALB_UnHealthyHostCount_Alarm` を押下して詳細画面を表示 ]

- [ アクション ] - [ コピー ]を押下
![alarm_setting07.png](./images/cloudwatch/alarm_setting07.png)

- メトリクスと条件の指定 ( ※上記  `ALB_UnHealthyHostCount_Alarm` と同じ設定条件とする ) - [ 次へ ] を押下

- アクションの設定　( 下図の通りに設定 ) - [ 次へ ] を押下
![alarm_setting08.png](./images/cloudwatch/alarm_setting08.png)

- 名前と説明を追加　( 任意のアラーム名・アラームの説明を明記 ) - [ 次へ ] を押下

- プレビューと作成 - [ アラームの作成 ] を押下
