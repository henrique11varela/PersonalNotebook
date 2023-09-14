# Laravel Commands

[Back](../Documentation.md)

## Index

- [Laravel Commands](#laravel-commands)
  - [Index](#index)
  - [Install Laravel](#install-laravel)
    - [Get laravel installer](#get-laravel-installer)
  - [Create Laravel Project](#create-laravel-project)
    - [New Project](#new-project)
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
    - [table example](#table-example)
  - [Controllers](#controllers)
    - [Pass Data to View](#pass-data-to-view)
    - [Model fillable](#model-fillable)
    - [CRUD Controller](#crud-controller)
    - [Form](#form)
    - [select](#select)
  - [Folder Structure](#folder-structure)

## Install Laravel

XAMPP (Version 7.4.33 php)

Composer (Version 2.5.5)

Node (v16.19.1)

### Get laravel installer

```shell
composer global require laravel/installer
```

## Create Laravel Project

### New Project

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

[Example](./Examples/Model.md)

```shell
php artisan make:model %name%
```

> %name% is the name of the model (singular)  

Is made in the model file `app/%model%.php`  
The relations are made here.  

### Migration

[Example](./Examples/Migrations.md)

```shell
php artisan make:migration %creator% --create=%table%
```

> %creator% is the name of the migration (plural) *create_table_plural*  
> %table% is the name of the table (plural)

Is made in the migration file `database/migrations/%date%_%creator%.php`

### Seeder

[Example](./Examples/Seeds.md)

```shell
php artisan make:seeder %name%
```

> %name% is the name of the seeder (singular)  

Is made in the seeder file `database/seeds/Seeder.php`  
Has to be called in the `database/seeds/DatabaseSeeder.php` file  

```php
$this->call(PersonSeeder::class);
```

### Factory

[Example](./Examples/Factory.md)

```shell
php artisan make:factory %name%
```

> %name% is the name of the factory (singular)  

Is made in the factory file `database/factories/Factory.php`

---

## Routes

### Create Route

- On `./routes/web.php`  

```php
Route::prefix('Prefix')->group(function () {
    Route::get('', 'Controller@index')->name('Prefix.index');
    Route::get('create', 'Controller@create')->name('Prefix.create');
    Route::post('', 'Controller@store')->name('Prefix.store');
    Route::get('{id}', 'Controller@show')->name('Prefix.show');
    Route::get('{id}/edit', 'Controller@edit')->name('Prefix.edit');
    Route::put('{id}', 'Controller@update')->name('Prefix.update');
    Route::delete('{id}', 'Controller@destroy')->name('Prefix.destroy');
});
```

> Create a route to call the method in the controller when the url is /subDom

---

## Views

### Create View: [master template](master_template/master_template.md)

- Make a file in the folder `./resources/views` named `%name%.blade.php`
- View example:

  ```php
  @extends('master.main')
  @section('content')
    @component('components.table', [
      'key' => $value,
    ])
    @endcomponent
  @endsection
  ```

### Use Data in View

```php
<!-- Inserts a string in the h1 tag -->
<h1>{{ $variable }}</h1>

<!-- Inserts HTML in the h1 tag -->
<h1>{!! $variable !!}</h1>
```

### table example
[Example](./Examples/List.md)
```php
<table class="table">
  <thead class="thead-dark">
    <tr>
      <th scope="col">#</th>
      <th scope="col">Name</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody>
    @foreach ($projects as $project)
      <tr>
        <th scope="row">{{ $project->id }}</th>
        <td>{{ $project->name }}</td>
        <td class="d-flex">
          <a class="btn btn-primary mr-2" href="{{ route('project.show', $project->id) }}">Show</a>
          <a class="btn btn-success mr-2" href="{{ route('project.edit', $project->id) }}">Edit</a>
          <form method="post" action="{{route('project.destroy', $project->id)}}">
            @csrf
            @method('DELETE')
            <button class="btn btn-danger" type="submit">Delete</button>
          </form>
        </td>
      </tr>
    @endforeach
  </tbody>
</table>
```

---

## Controllers

### Pass Data to View

```php
public function index()
{
  $variable = Model::all();
  return response(view('viewName', [
    'key' => $variable,
  ]));
}
```

> Pass the data `$players` to the view `players`
> $players is an array of players (model)

### Model fillable

```shell
protected $fillable = [
    'name',
];
```

### CRUD Controller

```shell
public function index()
{
  $projects = Model::all();
  return view('pages.Project.index', [
    'projects' => $projects,
  ]);
}

public function create()
{
  return view('PATH_TO_VIEW');
}

public function store(Request $request)
{
  $this->validate($request, [
    'name' => 'required',
  ]);

  $newProject = new Project();
  $newProject->name = $request->name;
  $newProject->save();

  return redirect(route('project.index'));
}

public function show(int $id)
{
  $project = Project::find($id);
    return view('pages.Project.show', [
    'project' => $project,
  ]);
}

public function edit(int $id)
{
  $project = Project::find($id);
  return view('pages.Project.edit', [
    'project' => $project,
  ]);
}

public function update(Request $request, int $id)
{
  $this->validate($request, [
    'name' => 'required',
  ]);

  $project = Project::find($id);

  $project->name = $request->name;
  $project->save();

  return redirect(route('project.index'));
}

public function destroy(int $id)
{
  $project = Project::find($id);
  $project->delete();

  return redirect(route('project.index'));
}
```

### Form

```php
{{-- $project --}}
{{-- $mode s_Show e_Edit c_Create --}}
<form method="post" action="{{ $mode == 'c' ? route('project.store') : ($mode == 'e' ? route('project.update', $project->id) : '') }}">
  @csrf
  @method($mode == 'c' ? 'POST' : 'PUT')

  {{-- Input --}}
  <div class="input-group mb-3">
    <div class="input-group-prepend">
      <span class="input-group-text" id="inputGroup-sizing-default">Name</span>
    </div>
    <input type="text" id="name" name="name" class="form-control @error('name') is-invalid @enderror"
      value="{{ isset($project) ? $project->name : old('name') }}" required aria-label="Sizing example input"
      aria-describedby="inputGroup-sizing-default" @if($mode == 's') disabled @endif>
    @error('name')
      <span class="invalid-feedback" role="alert">
        <strong>{{ $message }}</strong>
      </span>
    @enderror
  </div>

  {{-- Submit --}}
  @if($mode != 's')
    <button type="submit" class="btn btn-primary">Submit</button>
  @endif
</form>

```

### select

```php
<label for="project_id">Project:</label>
<select
  id="project_id"
  name="project_id"
  class="form-control @error('project_id') is-invalid @enderror"
  required>
  <option value="" disabled selected>Select a category</option>

  @foreach($projects as $project)
    <option value="{{ $project->id }}">
      {{ $project->id }} - {{ $project->name }}
    </option>
  @endforeach
</select>

@error('project_id')
  <span class="invalid-feedback" role="alert">
    <strong>{{ $message }}</strong>
  </span>
@enderror
```

---

## Folder Structure

```shell
Project
║ 
╠═ /app
║   ╚═ /Http
║       ╚═ /Controllers
║           ╚═ Controllers.php
║
╠═ /database
║   ╠═ /factories
║   ║   ╚═ Factory.php
║   ╠═ /migrations
║   ║   ╚═ table.php
║   ╚═ /seeds
║       ╠═ DatabaseSeeder.php
║       ╚═ Seeder.php
║
╠═ /resources
║   ╚═ /views
║       ╠═ /components
║       ║  ╚═ component.blade.php
║       ╚═ view.blade.php
║
╠═ /routes
║   ╚═ web.php
║
╚═ .env
```

---
