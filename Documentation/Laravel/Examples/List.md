# Table.blade.php Example

[Back](../Laravel.md)

```php
{{-- objectList --}}
<table class="table">
    <thead class="thead-dark">
        <tr>
            <th scope="col">#</th>
            <th scope="col">Name</th>
            <th scope="col">Actions</th>
        </tr>
    </thead>
    <tbody>
        @foreach ($objectList as $object)
        <tr>
            <th scope="row">{{ $object->id }}</th>
            <td>{{ $object->name }}</td>
            <td class="d-flex">
                <a class="btn btn-primary mr-2" href="{{ route('project.show', $object->id) }}">Show</a>
                <a class="btn btn-success mr-2" href="{{ route('project.edit', $object->id) }}">Edit</a>
                <form method="post" action="{{route('project.destroy', $object->id)}}">
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

