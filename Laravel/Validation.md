## バリデーション
- フォームに入力された情報が正しい形式かどうかをチェックする機能。
- コントローラのメソッドを使う方法
  - $this->validate($request, [検証設定の配列];  
  - フォームがpost送信された時の処理  

## エラーメッセージの表示の仕組み
- @if(count($errors) > 0)  または  @if($errors->any())  
    ...メッセージの表示処理...  
  @endif  
    
  @foreach($errors->all() as $error)  
    ...メッセージの表示...  
  @endforeach  
  
- デフォルトではエラーメッセージは英語。
  - 日本語にするには？  
    - `resources/lang`内に、`jp`フォルダを作成。  
    - `resources/lang/en`内の`validation.php`のコピーを、`jp`フォルダ内に作成。　　
    - `validation.php`の必要な部分を日本語に修正する。　←エラーメッセージが日本語に。  
    - `config/app.php`内の、`locale`を`jp`に修正する。  
      - デフォルトの言語設定が日本語になります。これにより、Laravel はメッセージ定義が必要になったときにまず`jp`ディレクトリを探しに行きます。  
        定義ファイルが見つかればそれを使い、見つからなければ`fallback_locale`である`en`のディレクトリにあるファイルを使います。
        
## @errorディレクティブ
- @error('項目名')  
  ...{{ $message }}...//メッセージを表示  
  @enderror  
  
## フォームリクエスト
- バリデーション機能をリクエスト内に持たせることができる。  
- php artisan make:request 〇〇Request  
