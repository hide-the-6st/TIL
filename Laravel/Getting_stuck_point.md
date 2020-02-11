## マイグレーションファイルの作成ができない  
php artisan make:migration create_people_table  
↓  
Cannot declare class CreateUsersTable, because the name is already in use

- 解決方法  
/database/migrations/内の元々ある3つのファイルを開き、class名を変更する。  
※class名変更後は、ターミナルで要"composer dump-autoload"?
  
その後、3つのファイルのclass名を元に戻す。

## シーディングの失敗
`php artisan db:seed --class=PeopelTableSeeder`  
↓  
Target class [PeopelTableSeeder] does not exist.  
teratailで質問→スペルミスを指摘される。  
x:Peopel  ○:People

## 「database is locked」

## 「database disk image is malformed」  

## バリデーションのエラー
- エラーメッセージ
  - Failed asserting that an array contains '期限日 には今日以降の日付を入力してください。'.  
  - Illuminate\Contracts\Container\BindingResolutionException: Target class [session.store] does not exist.  
- 解決方法...assertSessionHasErrorsメソッドの引数が間違っていた？
```
$response->assertSessionHasErrors([  
        'due_date' => '期限日 には今日以降の日付を入力してください。',  
      ]);  
↓  
$response->assertSessionHasErrors(  
        'due_date', '期限日 には今日以降の日付を入力してください。',  
      );
 ```
