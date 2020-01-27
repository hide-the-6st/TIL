## マイグレーションファイルの作成ができない  
php artisan make:migration create_people_table  
↓  
Cannot declare class CreateUsersTable, because the name is already in use

- 解決方法  
/database/migrations/内の元々ある3つのファイルを開き、class名を変更する。  
※class名変更後は、ターミナルで要"composer dump-autoload"?
