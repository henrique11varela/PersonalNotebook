# Laravel Commands

## Index
- [Laravel Commands](#laravel-commands)
  - [Index](#index)
  - [Install Laravel](#install-laravel)
  - [Create Laravel Project](#create-laravel-project)
  - [Setup Laravel Project](#setup-laravel-project)
  - [Run Laravel Server](#run-laravel-server)
  - [Database](#database)
  - [Create Model/Controller/Factory/Seeder](#create-modelcontrollerfactoryseeder)
  - [Routes](#routes)
  - [Views](#views)
  - [Controllers](#controllers)
  - [Folder Structure](#folder-structure)
    

## Install Laravel

- Get laravel installer
    ```shell
    composer global require laravel/installer
    ```

## Create Laravel Project

- Criar Projeto limpo
    ```shell
    composer create-project --prefer-dist laravel/laravel:^7.0 %nome_do_projeto%
    ```
    > %nome_do_projeto% é o nome do projeto


## Setup Laravel Project

- Add Frontend Resources: [documentation](https://packagist.org/packages/laravel/ui)
    ```shell
    composer require laravel/ui:^2.4
    php artisan ui vue --auth
    ```

- Install composer/npm dependencies
    ```shell
    composer install
    ```
    ```
    npm install
    ```

- Setup npm packages settings
    ```shell
    npm run dev
    ```

## Run Laravel Server
- Run Laravel Server
    ```shell
    php artisan serve
    ```
    
---

## Database

- Create Database
    > Create a database in phpMyAdmin (XAMPP)

- .env
    > Change DB_DATABASE to the name of the database

- Migrate Database
    ```shell
    php artisan migrate
    ```
    > Create tables using migrations

- Seed Database
    ```shell
    php artisan db:seed
    ```
    > Fill tables with data using seeders

- Migrate and Seed Database
    ```shell
    php artisan migrate:fresh --seed
    ```
    > Create tables using migrations and fill tables with data using seeders fresh from zero

---

## Create Model/Controller/Factory/Seeder
- Model/Controller/Factory/Seeder
    ```shell
    php artisan make:model %name% -a
    ```
    > %name% is the name of the model (singular)  
    > -a is to create all the files (model, controller, factory, seeder)

- Controller
    ```shell
    php artisan make:controller %name%
    ```
    > %name% is the name of the controller (singular)  


- Model
    ```shell
    php artisan make:model %name%
    ```
    > %name% is the name of the model (singular)  
    

- Factory
    ```shell
    php artisan make:factory %name%
    ```
    > %name% is the name of the factory (singular)  


- Seeder
    ```shell
    php artisan make:seeder %name%
    ```
    > %name% is the name of the seeder (singular)  



---

## Routes

- Create Route
    ```php
    Route::get('/subDom', 'controller@method');
    ```
    > Create a route to call the method in the controller when the url is /subDom

---

## Views

- Create View
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

- Use Data in View
    ```php
    <!-- Inserts a string in the h1 tag -->
    <h1>{{ $players }}</h1>

    <!-- Inserts HTML in the h1 tag -->
    <h1>{!! $players !!}</h1>
    ```

---

## Controllers

- Pass Data to View
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

```
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

---
















```shell
php artisan make:migration create_table_posts --create=posts
php artisan make:migration nome_do_criador_de_tabelas --create=nome_tabela
```

função up é *create*  
função down é *drop*

```shell
php artisan migrate
php artisan migrate:fresh --seed
php artisan db:seed 
```


 seeds

DatabaseSeeder.php é o ficheiro responsavel por chamar as restantes seeds

```shell
php artisan make:seeder nomedatabelaTableSeeder
```


```shell
php artisan make:factory nomedatabelaFactory
php artisan make:model Post
```

```shell
php artisan make:model nome -a
```




