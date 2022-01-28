# My Movies List REST API

## GET Endpoints

### /user

Return the data of the current logged in user, or nothing (in this case, will be redirected to the login page).

```json
{
    id: 1,
    name: "Itamar",
    email: "itamarc@gmail.com",
    imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
    registered: "2022-01-07T00:00:00.000Z"
}
```

### /user/{id}

Return the data of a user, including his movies lists.

```json
user: {
    id: 1,
    name: "Itamar",
    email: "itamarc@gmail.com",
    imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
    registered: "2022-01-07T00:00:00.000Z"
    movies-lists:
    [
        {
            id: 1,
            name: "My list",
            created: "2022-01-01T00:00:00.000Z",
            updated: "2022-01-02T00:00:00.000Z",
        },
        {
            id: 2,
            name: "Sci-fi Movies",
            created: "2022-01-01T00:00:00.000Z",
            updated: "2022-01-02T00:00:00.000Z",
        },
    ]
}
```

### /movies-lists

Return the movies lists from all users, more recently updated first.

Parameter:

- ```page``` - Show the result for the specified page. Each page have 20 lists. Default to 1 if not set.

```json
[
    {
        id: 1,
        name: "My list",
        created: "2022-01-01T00:00:00.000Z",
        updated: "2022-01-02T00:00:00.000Z",
        user: {
            id: 1,
            name: "Itamar",
            email: "itamarc@gmail.com",
            imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
            registered: "2022-01-07T00:00:00.000Z"
        }
    },
    {
        id: 2,
        name: "Sci-fi Movies",
        created: "2022-01-01T00:00:00.000Z",
        updated: "2022-01-02T00:00:00.000Z",
        user: {
            id: 1,
            name: "Itamar",
            email: "itamarc@gmail.com",
            imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
            registered: "2022-01-06T13:00:00.000Z"
        }
    },
    {
        id: 3,
        name: "Romance Movies",
        created: "2022-01-01T00:00:00.000Z",
        updated: "2022-01-02T00:00:00.000Z",
        user: {
            id: 2,
            name: "John",
            email: "john.constantine@realhell.com",
            imageUrl: "https://www.superherodb.com/pictures2/portraits/10/100/718.jpg",
            registered: "2022-01-07T10:00:00.000Z"
        }
    },
]
```

### /movies-lists/{id}

Return the basic data of a movies list.

```json
{
    id: 1,
    name: "My list",
    created: "2022-01-01T00:00:00.000Z",
    updated: "2022-01-02T00:00:00.000Z",
    user: {
        id: 1,
        name: "Itamar",
        email: "itamarc@gmail.com",
        imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
        registered: "2022-01-07T00:00:00.000Z"
    }
}
```

### /movies-lists/{id}/movies

Return a movies list data, including the movies in the list.

```json
{
    id: 1,
    name: "My list",
    created: "2022-01-01T00:00:00.000Z",
    updated: "2022-01-02T00:00:00.000Z",
    user: {
        id: 1,
        name: "Itamar",
        email: "itamarc@gmail.com",
        imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
        registered: "2022-01-07T00:00:00.000Z"
    },
    movies: [
        {
            id: 1,
            title: "The Polar Express",
            year: 2004,
            categories: ["Animation"]
        },
        {
            id: 2,
            title: "The Dark Knight",
            year: 2008,
            categories: ["Action"]
        },
        {
            id: 3,
            title: "Clash of the Titans",
            year: 2010,
            categories: ["Action", "Fantasy"]
        },
        {
            id: 4,
            title: "Inception",
            year: 2010,
            categories: ["Sci-fi"]
        },
        {
            id: 5,
            title: "Tenet",
            year: 2020,
            categories: ["Sci-fi"]
        },
        {
            id: 6,
            title: "Interstellar",
            year: 2014,
            categories: ["Sci-fi"]
        },
        {
            id: 7,
            title: "American Sniper",
            year: 2014,
            categories: ["Drama", "War"]
        }
    ]
}
```

## POST Endpoints

### /user

New user registration.

#### Data sent

```json
{
    name: "Itamar",
    email: "itamarc@gmail.com",
    imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
}
```

#### Returned data

```json
{
    id: 1,
    name: "Itamar",
    email: "itamarc@gmail.com",
    imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
    registered: "2022-01-07T00:00:00.000Z"
}
```

### /movies-list

Create a new movies list.

#### Data sent

```json
{
    name: "My list",
}
```

#### Returned data

```json
{
    id: 1,
    name: "My list",
    created: "2022-01-01T00:00:00.000Z",
    updated: "2022-01-02T00:00:00.000Z",
    user: {
        id: 1,
        name: "Itamar",
        email: "itamarc@gmail.com",
        imageUrl: "https://avatars.githubusercontent.com/u/19577272?v=4",
        registered: "2022-01-07T00:00:00.000Z"
    }
}
```

### /movie

Include a new movie in a list.

#### Data sent

```json
{
    movies-list-id: 1,
    title: "The Polar Express",
    year: 2004,
    categories: ["Animation"],
    rank: 7,
    watched: true
}
```

### /movie/{id}

Update a movie in a list.

Can only update the categories, rank and watched fields.

#### Data sent

```json
{
    categories: ["Animation"],
    rank: 7,
    watched: true
}
```

## DELETE Endpoints

### /movies-lists/{id}

Remove a movies list. If the list have movies in it, remove them also.

### /movies-lists/{id}/movies/{id}

Remove a movie from a movies list.
