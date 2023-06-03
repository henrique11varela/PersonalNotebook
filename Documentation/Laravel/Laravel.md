# Laravel Commands

[Back](../Documentation.md)

## Index

- [Laravel Commands](#laravel-commands)
  - [Index](#index)
  - [Install Laravel](#install-laravel)
    - [Get laravel installer](#get-laravel-installer)
  - [Create Laravel Project](#create-laravel-project)
    - [Criar Projeto limpo](#criar-projeto-limpo)
  - [Setup Laravel Project](#setup-laravel-project)
    - [Add Frontend Resources: documentation](#add-frontend-resources-documentation)
    - [Install composer/npm dependencies](#install-composernpm-dependencies)
    - [Setup npm packages settings](#setup-npm-packages-settings)
  - [Run Laravel Server](#run-laravel-server)
    - [Run](#run)
  - [Database](#database)
    - [Create Database](#create-database)
    - [.env](#env)
    - [Migrate Database](#migrate-database)
    - [Seed Database](#seed-database)
    - [Migrate and Seed Database](#migrate-and-seed-database)
  - [Create Model/Controller/Factory/Seeder](#create-modelcontrollerfactoryseeder)
    - [Model/Controller/Factory/Seeder](#modelcontrollerfactoryseeder)
    - [Controller](#controller)
    - [Model](#model)
    - [Migration](#migration)
    - [Seeder](#seeder)
    - [Factory](#factory)
  - [Routes](#routes)
    - [Create Route](#create-route)
  - [Views](#views)
    - [Create View: master template](#create-view-master-template)
    - [Use Data in View](#use-data-in-view)
  - [Controllers](#controllers)
    - [Pass Data to View](#pass-data-to-view)
  - [Folder Structure](#folder-structure)

## Install Laravel

### Get laravel installer

```shell
composer global require laravel/installer
```

## Create Laravel Project

### Criar Projeto limpo

```shell
composer create-project --prefer-dist laravel/laravel:^7.0 %nome_do_projeto%
```  

> %nome_do_projeto% é o nome do projeto

## Setup Laravel Project

### Add Frontend Resources: [documentation](https://packagist.org/packages/laravel/ui)

```shell
composer require laravel/ui:^2.4
```

```shell
php artisan ui vue --auth
```

### Install composer/npm dependencies

```shell
composer install
```

```shell
npm install
```

### Setup npm packages settings

```shell
npm run dev
```

## Run Laravel Server

### Run

```shell
php artisan serve
```  

---

## Database

### Create Database

> Create a database in phpMyAdmin (XAMPP)

### .env

> Change DB_DATABASE to the name of the database

### Migrate Database

```shell
php artisan migrate
```  

> Create tables using migrations

### Seed Database

```shell
php artisan db:seed
```

> Fill tables with data using seeders

### Migrate and Seed Database

```shell
php artisan migrate:fresh --seed
```

> Create tables using migrations and fill tables with data using seeders fresh from zero

---

## Create Model/Controller/Factory/Seeder

### Model/Controller/Factory/Seeder

```shell
php artisan make:model %name% -a
```

> %name% is the name of the model (singular)  
> -a is to create all the files (model, controller, factory, seeder)

### Controller

```shell
php artisan make:controller %name%
```

> %name% is the name of the controller (singular)  

### Model

```shell
php artisan make:model %name%
```

> %name% is the name of the model (singular)  

### Migration

[Example](./Examples/Migrations.md)

```shell
php artisan make:migration %creator% --create=%table%
```

> %creator% is the name of the migration (plural) *create_table_plural*  
> %table% is the name of the table (plural)

### Seeder

[Example](./Examples/Seeds.md)

```shell
php artisan make:seeder %name%
```

> %name% is the name of the seeder (singular)  

### Factory

[Example](./Examples/Factory.md)

```shell
php artisan make:factory %name%
```

> %name% is the name of the factory (singular)  

---

## Routes

### Create Route

- On `./routes/web.php`  

```php
Route::get('/subDom', 'controller@method');
```

> Create a route to call the method in the controller when the url is /subDom

---

## Views

### Create View: [master template](master_template/master_template.md)

- Make a file in the folder `./resources/views` named `%name%.blade.php`
- View example:

  ```php
  //this view extends `./resources/views/master/main.blade.php`
  @extends('master.main')
  //Fills `@yield('content')` with the content of the section
  @section('content')
    @component('components.table', [
      'players' => $players,
    ])
    @endcomponent
  @endsection
  ```

### Use Data in View

```php
<!-- Inserts a string in the h1 tag -->
<h1>{{ $players }}</h1>

<!-- Inserts HTML in the h1 tag -->
<h1>{!! $players !!}</h1>
```

---

## Controllers

### Pass Data to View

```php
public function index()
{
  $players = player::all();
  return response(view('players', [
    'players' => $players,
  ]));
}
```

> Pass the data `$players` to the view `players`
> $players is an array of players (model)

---

## Folder Structure

```shell
Project
║ 
╠═ /app
║   ╚═ /Http
║       ╚═ /Controllers
║
╠═ /database
║   ╠═ /factories
║   ╠═ /migrations
║   ╚═ /seeds
║
╠═ /resources
║   ╚═ /views
║       ╚═ /components
║
╠═ /routes
║
╚═ .env
```

---
