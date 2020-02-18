## バリデーション
- フォームに入力された情報が正しい形式かどうかをチェックする機能。
- コントローラのメソッドを使う方法
  - $this->validate($request, [検証設定の配列];  
  - フォームがpost送信された時の処理  

## エラーメッセージの表示の仕組み
```
@if(count($errors) > 0)  または  @if($errors->any())  
    
  @foreach($errors->all() as $error)  
    {{ $error }}...メッセージの表示...  
  @endforeach  
  
@endif  
```

- デフォルトではエラーメッセージは英語。
  - 日本語にするには？  
    - `resources/lang`内に、`jp`フォルダを作成。  
    - `resources/lang/en`内の`validation.php`のコピーを、`jp`フォルダ内に作成。　　
    - `validation.php`の必要な部分を日本語に修正する。　←エラーメッセージが日本語に。  
    - `config/app.php`内の、`locale`を`jp`に修正する。  
      - デフォルトの言語設定が日本語になります。これにより、Laravel はメッセージ定義が必要になったときにまず`jp`ディレクトリを探しに行きます。  
        定義ファイルが見つかればそれを使い、見つからなければ`fallback_locale`である`en`のディレクトリにあるファイルを使います。
- 入力欄の名称をカスタマイズするには、`FormRequest`クラスに`attributes`メソッドを追加します。
        
## @errorディレクティブ
```
@error('項目名')  
  ...{{ $message }}...//メッセージを表示  
@enderror  
```
  
## フォームリクエスト
- バリデーション機能をリクエスト内に持たせることができる。  
- php artisan make:request 〇〇Request  
- `messages`メソッドでは個別の FormRequest クラスの内部でのみ有効なメッセージを定義できます。  
-  日付の指定の例...  
```
public function rules()
    {
        return [
            'due_date' => 'required|date|after_or_equal:today',
        ];
    }
```
`after_or_equal`（特定の日付と同じまたはそれ以降の日付であること）。  
引数として`today`を指定することにより、今日を含んだ未来日だけを許容します。  

## Confirmedルール	
- ある項目（仮に abc とする）とその項目名 + _confirmation という名前の項目（abc_confirmation）の入力値が一致することを検証する。
- パスワードの再設定時に使用。

## unique ルール
- 実際にデータベースの内容を参照してすでに使用されている値かどうかを確かめるルール。

## validation.php
- ここに指定された内容はアプリケーション全体で有効になります。

