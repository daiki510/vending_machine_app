## 手順
require "/Users/ddgg7755/DIC/workspace/vending-_machine/lib/vm_stock.rb"
vm = VendingMachine.new
vm.insert(500)
vm.judge
vm.available_drinks
vm.select_drink(1)
vm.random
vm.current_total_money
vm.check_sales

### 在庫補充
vm.store_drink(:Coke, 5)
vm.store_drink(:Red_bull, 5)
vm.store_drink(:Water, 5)
vm.stock_info

## 課題
> ステップ０　お金の投入と払い戻し
> 
* 10円玉、50円玉、100円玉、500円玉、1000円札を１つずつ投入できる。
* 投入は複数回できる。
* 投入金額の総計を取得できる。
* 払い戻し操作を行うと、投入金額の総計を釣り銭として出力する。
> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう！）

> ステップ１　扱えないお金
> 
* 想定外のもの（硬貨：１円玉、５円玉。お札：千円札以外のお札）が* 投入された場合は、投入金額に加算せず、それをそのまま釣り銭としてユーザに出力する。
> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう！）

> ステップ２　ジュースの管理
> 
* 値段と名前の属性からなるジュースを１種類格納できる。初期状態で、コーラ（値段:120円、名前”コーラ”）を5本格納している。
* 格納されているジュースの情報（値段と名前と在庫）を取得できる。

> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう！）

> ステップ３　購入
> 
* 投入金額、在庫の点で、コーラが購入できるかどうかを取得できる。
* ジュース値段以上の投入金額が投入されている条件下で購入操作を行うと、ジュースの在庫を減らし、売り上げ金額を増やす。
* 投入金額が足りない場合もしくは在庫がない場合、購入操作を行っても何もしない。
* 現在の売上金額を取得できる。
* 払い戻し操作では現在の投入金額からジュース購入金額を引いた釣り銭を出力する。

> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう* ！）

> ステップ４　機能拡張
> 
* ジュースを3種類管理できるようにする。
* 在庫にレッドブル（値段:200円、名前”レッドブル”）5本を追加する。
* 在庫に水（値段:100円、名前”水”）5本を追加する。
* 投入金額、在庫の点で購入可能なドリンクのリストを取得できる。

> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう！）

> ステップ５　釣り銭と売り上げ管理
> 
* ジュース値段以上の投入金額が投入されている条件下で購入操作を行うと、釣り銭（投入金額とジュース値段の差分）を出力する。
* ジュースと投入金額が同じ場合、つまり、釣り銭0円の場合も、釣り銭0円と出力する。
* 釣り銭の硬貨の種類は考慮しなくてよい。

> リファクタリング
> 
（今後の仕様変更に備えて実装とテストをリファクタリングしましょう！）


## 以下応用課題

> ステップ6　釣り銭ストックの導入
> 
* 自動販売機は釣り銭ストックを持つ事ができる。
* 釣り銭ストックとして、有効な各お札と硬貨10枚ずつ保持する。
* 釣り銭を返す際は、値段の大きな物から硬貨を優先して出力するようにする。ストックからなくなった硬貨は、可能であれば他の硬貨で補う（例えば50円硬貨を10円硬貨で補う）
* 釣り銭には投入金額のお札および硬貨も使える(110円入れて、100円の水を買うといった場合のように余分に入れたお金も戻る)。
* 釣り銭を出力したら、釣り銭用ストックを減らす。
* 購入操作を行った際に、釣り銭用ストックが足りない場合、何もしない。
* 釣り銭用ストックを取得できる。
> ステップ７　ジュースのランダム購入
> 
* 在庫にダイエットコーラ（値段:120円、名前”ダイエットコーラ”）5本を追加する。
* 在庫にお茶（値段:120円、名前”お茶”）5本を追加する。
* 「ランダム」購入ボタンを導入する。
* 「ランダム」購入ボタンを押すと、コーラ、ダイエットコーラ、お茶がランダムに購入できる。
* 「ランダム」候補のドリンクの在庫が全てない時は通常のドリンクがない場合と同じ振る舞いをする。
* 「ランダム」は投入金額、在庫の点で購入可能なドリンクのリストに中に入る(つまり、120円入れて、コーラとお茶の在庫がある場合、* 「コーラ」と「お茶」と「ランダム」が購入可能なドリンクのリストになる)。

> 以下進捗を見て追加するさらなる応用課題
> 
* 釣銭の高機能化
* 売上金額を釣銭に回すことができる
* 賞味期限管理
* ジュースの賞味期限（年月日）を1本単位で登録できる。
* 現在日時が購入対象のジュースの賞味期限を過ぎている場合、ジュースの購入ボタンを押しても何もしない。
* 格納されているジュースの賞味期限情報を取得できる
