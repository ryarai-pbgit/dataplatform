# Cortex Analystの検証済クエリ（2025/10/20）

## 1. 検証済みクエリ
過去に何度か触れた状態だと下記のように表示される<br>
１から登録する他に、使用状況に応じて提案されたものをそのまま登録することができます。<br>

![[verified]](images/verified.png)
![[verified_2]](images/verified_2.png)
![[verified_3]](images/verified_3.png)

今回は提案されていた３件をそのまま登録しました。

![[verified_4]](images/verified_4.png)

## 2. アナリストへの問いかけ
いくつかのパターンで問いかけを実施。

### 2.1 検証済みクエリの質問文と全く同一の質問
予想通り、検証済みクエリがヒットして使われる。<br>
一番下に、確認済みクエリに基づいて生成済み、のコメントあり<br>
![[question_1_1]](images/question_1_1.png)
![[question_1_2]](images/question_1_2.png)

### 2.2 検証済みクエリと関係ない質問
この場合は、検証済みクエリにはヒットしないので、下部の表示はない。<br>
また、プロンプトで指定した、だったら回答しないで、というのは無視されました。<br>
![[question_2_1]](images/question_2_1.png)
![[question_2_2]](images/question_2_2.png)

### 2.3 検証済みクエリの質問文に近いけど、ちょっと違う質問
この場合は、ちょっとの違いを吸収して、検証済みクエリをアレンジして、質問に答えてくれるようでした。<br>
検証済みクエリと近いけど、ちょっと違うクエリが生成されて実行されていました。<br>
また、一番下に、確認済みクエリに基づいて生成済み、のコメントあり<br>
![[question_3_1]](images/question_3_1.png)
![[question_3_2]](images/question_3_2.png)

### 2.4 一番下の、確認済みクエリに基づいて生成済み、のコメントはAPIで取得できるのか
https://docs.snowflake.com/ja/user-guide/snowflake-cortex/cortex-analyst/rest-api#label-cortex-analyst-rest-api-response<br>
取得できるようです。<br>
```
message.content[].confidence.verified_query_used.name （string）: 検証済みクエリリポジトリから抽出された、使用した検証済みクエリの名前。
message.content[].confidence.verified_query_used.question （string）: 検証済みクエリリポジトリから抽出された、検証済みクエリが回答する質問。
など
```
