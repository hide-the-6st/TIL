# DBクラスとメソッド
$変数 = DB::select(実行するSQL文);　　
  
DB::insert(クエリ文,パラメータ配列);  
- レコードの作成...「フォームの値の取得」 + 「DB::insertの実行」 + 「トップへのリダイレクト」  

DB::update(クエリ文,パラメータ配列);  
  
DB::delete(クエリ文,パラメータ配列);  