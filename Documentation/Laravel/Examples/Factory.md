# Factory Example

[Back](../Laravel.md)

```php
$factory->define(Person::class, function (Faker $faker) {
    return [
        'name' => $faker->name(),
        'birthday' => $faker->date(),
        'email' => $faker->email(),
        'address_id' => $faker->unique()->numberBetween(6, 105),
    ];
});
```

> Example for a Person table
