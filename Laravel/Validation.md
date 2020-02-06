## バリデーション
- フォームに入力された情報が正しい形式かどうかをチェックする機能。
- コントローラのメソッドを使う方法
  - $this->validate($request, [検証設定の配列];  
  - フォームがpost送信された時の処理  

## エラーメッセージの表示の仕組み
- @if(count($errors) > 0)  
    ...メッセージの表示処理...  
  @endif  
    
  @foreach($errors->all() as $error)  
    ...メッセージの表示...  
  @endforeach  
  
## @errorディレクティブ
- @error('項目名')  
  ...{{ $message }}...//メッセージを表示  
  @enderror  
  
## フォームリクエスト
- バリデーション機能をリクエスト内に持たせることができる。  
- php artisan make:request 〇〇Request  
