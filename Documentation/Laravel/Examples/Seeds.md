# Seeds Example

[Back](../Laravel.md)

```php
//Seeds file
public function run()
{
    //Manual insert
    \DB::table('pets')->insert([
        'columnName1' => 'Pet 1',
        'columnName2' => '2000-1-5',
        'columnName3' => 'brown',
        'person_id' => 1,
    ]);
    //Factory insert
    factory(\App\Pet::class, 400)->create();
}
```

> Example for a Pet table
