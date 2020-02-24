## グローバルスコープ
- そのモデルでの全てのレコード取得に適用される。  
```
static::addGlobalScope(スコープ名 , function (Builder $builder)){  
  ...絞り込み処理...  
}
```

## スコープクラス
- Illuminate\Database\Eloquent名前空間にあるScopeを実装して定義される。  
```
class クラス名 implements Scope{  
  public function apply(Builder $builder, Model $model){  
    ...絞り込み処理...  
  }  
}
```

## Eager Loading
- データベースのアクセス回数を減らすことができる。
  - with()  
  ```
  $posts = Post::with('user')->get();
  ```
  - load()  
  ```
  $posts = Post::all();
  $posts->load('user');
  ```
