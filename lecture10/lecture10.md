# 【 lecture10：インフラ自動化 / IaC / CloudFormation 】

<br>

---

<br>

## 【 講義・リサーチ (メモ) 】

---

<details><summary>【 インフラ自動化 / IaC 】</summary>

<br>

■ インフラ自動化において考慮・検討・注意すべき事項<br>
- 自動化を構築する人材 / 構築されたものをメンテナンスする人材
- コスト削減のため盲目的に既存環境を自動化することはリスクも伴う
- 全自動・半自動 (=何かしらの工程で人の手が加わる自動化) / ( ※用途別に使い分け )<br>
- 全自動化可能なことを不安のため半自動化にすることはコストにしかならない<br>
- 自動化の考え方<br>
( ①全自動化 → ②必要に応じて一部を手動化 → ③②の一部を自動化 (半自動化) )<br>
( ※必要に応じてそもそも自動化すべき工程自体をなくすことも考慮する )

<br>

---

</details>

<details><summary>【 CloudFormation (各用語・概念等) 】</summary>

<br>

■ テンプレート<br>
- YAML / JSON形式で記述<br>
( ※CloudFormationのYAMLは、通常のYAML文法と異なる点がある )
- 1テンプレートにつき1スタックを作成
- 各リソースに記述する項目・設定方法は公式ドキュメントを参照<br>
( ※必須項目等を都度々々調べて記述 )<br>
《 参考：[AWS CloudFormation のドキュメント](https://docs.aws.amazon.com/ja_jp/cloudformation/index.html) 》<br>

<br>

■ スタック<br>
- テンプレートファイルによって自動構築されたリソース / 環境の1単位 (管理単位)<br>
( ※1テンプレートにつき、1スタックが作成される )
- スタック管理下にあるリソース構築前後の変更差分を検知/検出する<br>
：構築前 ( 変更セット ( Change Set ) ) / 構築後 ( ドリフト )<br>
- 修正したテンプレートを再読み込みすることでスタックの更新が可能<br>
- スタックを削除すると構築された環境が全て削除される<br>
- スタック作成時にエラーが起きるとロールバックが実行される<br>
( ※ただし、スタック自体は残るためエラー原因を確認して不必要になれば削除する )<br>
- スタック名の重複使用は不可

<br>

■ リソースID<br>
- リソース毎に存在する一意のID<br>
：主従 / 親子関係に関連し、これが何と何に紐づいているか把握することでテンプレートの各リソース記述に必要な要素が判別しやすくなる

<br>

■ 論理ID<br>
- リソースIDと区別するためのID<br>
：テンプレート内で使用する変数のようなもの (=テンプレート内で参照したい情報がある場合に指定)

<br>

■ クロススタック参照 (=スタック間の参照設定)<br>
- [ 参照元のテンプレート / スタック ]<br>
：Outputsセクションで他のテンプレートから参照できるように出力させる<br>
　( ※参照元では、出力名に擬似パラメータ参照 `AWS::StackName` を使用 )<br>
　( 記述例 `Name: !Sub ${AWS::StackName}-VPCID` )
- [ 参照先テンプレート / スタック ]<br>
：Parametersセクションに出力名の一部をデフォルト値として キー/値 で設定し、<br>
　importValue関数で上記を読み込ませる<br>
　( 記述例 `Fn::ImportValue: !Sub ${VPCStack}-VPCID` )<br>
　( 補足：importValue関数は、`!Sub(短縮形)` が含まれる場合は `!importValue(短縮形)` が使用できないため `Fn::ImportValue` で記述する )

<br>

■ 組込関数<br>
- 各種関数の内容は公式ドキュメントを参照<br>
( ※上手く活用することで記述するコード数の削減が可能 )<br>
《 参考：[組み込み関数リファレンス](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html) 》<br>
  - !Ref関数 ( 同一テンプレート内での参照に用いる )<br>
  - !GetAtt関数 ( 指定するリソースの所属情報を参照する場合に用いる )<br>
 ( 例. [SGが所属するSGID・VPCID](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-security-group.html#aws-properties-ec2-security-group-return-values) 等 )<br>
  - !Sub関数<br>
( スタックを作成または更新するまで使用できない値を含むコマンドまたは出力を作成 )<br>
( 例. `!Sub ${}` ( =Parametersセクションに記述した キー/値 を ${} に代入 等 ) )

<br>

■ パラメータ設定 ( Parametersセクションで記述 )<br>
- 固定値ではなく、スタック毎に値を変更したい場合などに設定

<br>

■ ユーザデータ ( [AWS::EC2::Instance のプロパティ ](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html#cfn-ec2-instance-userdata))<br>
- インスタンス起動(作成)時、1回だけ記述されたコマンドを実行<br>
( ※データ削除などを引き起こす場合があるため、基本的には使用しない方が無難 )<br>
：代替案① ( 手動でスクリプト実行したのち、そのスクリプトを削除 )<br>
：代替案② ( Ansbleで一度実行したものは二度と実行させないように設定 )

<br>

---

</details>

<details><summary>【 ツール 】</summary>

 <br>

- [CloudFormation デザイナー](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/working-with-templates-cfn-designer.html)<br>
( グラフィックツール (※チェックとして活用等する) )<br>
- [Former2](https://www.former2.com/)<br>
( 既存リソースから Infrastructure as Code 出力を生成できるようにする Webサービス )<br>

<br>

---

</details>

<br>

## 【 スタック (テンプレート) の構成 】

<br>


■スタック(テンプレート)分割(設計観点・考え方)
　：スタック(テンプレート)の運用・管理を考慮したうえで設計(分割/構成)を実施
　　(※具体的には下記の観点設計、スタック間はクロススタック参照にて情報を参照/関連付け)
　◎3層構造(レイヤー毎)に分割/構成
　　(※考え方としては、依存度・ライフサイクル(更新周期)毎にレイヤーを分け、それに合わせてスタック(テンプレート)分割を行う)
　　① Networkレイヤー(VPC/サブネット/ルートテーブル等)
　　② Securityレイヤー(セキュリティグループ/IAM等)
　　③ Applicatonレイヤー(EC2/RDS/ELB等)
　　(※①-③の関係性/属性：①は依存される側/更新頻度(低)、③は依存する側/更新頻度(高))

　◎③Aplicatonレイヤーはさらに下記に細分化して分割/構成
　　③-1 共有サービス(認証･プロキシ･メール等サーバ：Directory Service/Route53等)
　　③-2 Data(データ/状態を保持するリソース(ステートフル)：RDS/S3等)
　　③-3 Applicaton(データ/状態を保持しないリソース(ステートレス)：EC2/ELB/ECS/AutoScalling等)
　　(※①-③の関係性/属性：①は依存される側/更新頻度(低)、③は依存する側/更新頻度(高))

　◎その他(※メンテナンス等実施者/チーム/所有者など、スタック(テンプレート)管理者毎の分割設計も考慮が必要)

■リソース構成図/スタック(テンプレート)構成図

<br><br>

## 【 CloudFormation によるリソース構築 】
■ 構成図<br>
■ リソース構築
- スタック
- VPC - Network Layer
- SecurityGroup - Security Layer
- RDS - Application Layer
- EC2 - Application Layer
- ELB (ALB) - Application Layer
- S3 - Application Layer

<br><br>

##

<br><br>

## 【参考】
- ベストプラクティス
- ブラックベルト
- ハンズオン
- リファレンス
- 組込関数
