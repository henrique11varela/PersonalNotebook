# Migrations Example

[Back](../Laravel.md)

```php
//Model file
class %model% extends Model
{
    public function %function_name%()
    {
        return $this->hasMany(\App\%other_model%::class);
    }
}
```

> - %model% and %other_model% are the nams of the models  
> - %function_name% is the name of the function
> - `hasMany` is a one to many relationship
> - `hasOne` is a one to one relationship
> - `belongsToMany` is a many to many relationship
> - `belongsTo` is a many to one relationship

The foreign key side is the one that has the `belongsTo` relationship
