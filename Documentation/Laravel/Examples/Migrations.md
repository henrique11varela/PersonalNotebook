# Migrations Example

[Back](../Laravel.md)

```php
//Migration file
public function up()
{
    Schema::create('%table%', function (Blueprint $table) {
        $table->id();
        $table->string('columnName1');
        $table->string('columnName2');
        $table->date('columnName3');
        $table->foreignId('person_id')->constrained();
        $table->foreignId('address_id')->unique()->constrained();
        $table->timestamps();
    });
}
```

> - %table% is the name of the table  
> - `$table->id()` is the primary key auto increment  
> - `$table->foreignId('address_id')->unique()->constrained()` is a foreign key that references the id of the table address and is unique  
> - `$table->timestamps()` defines the timestamps created_at and updated_at  
