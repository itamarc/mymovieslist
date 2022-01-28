# External Movies API

To obtain the movies data, the app will access an external API.

The movies only will be saved if a user includes it in a list.

Requires an API_KEY to access the API. Free under registration.

## The API

I'll be using the free movie API from:

https://www.themoviedb.org/

The primary documentation of the API can be found at:

https://developers.themoviedb.org/3

### Base path to poster images:

https://image.tmdb.org/t/p/original

### To search for a movie:

https://api.themoviedb.org/3/search/movie?api_key=[API_KEY]&language=en-US&query=[QUERY]&page=1&include_adult=false

QUERY is the search term.

### Query String Schema:

| Parameter | Type | Description | Required? |
|---|---|---|---|
| api_key | string | default: <<api_key>> | **required** |
| query | string | Pass a text query to search. This value should be URI encoded.<br>minLength: 1 | **required** |
| language | string | Pass a ISO 639-1 value to display translated data for the fields that support it.<br>minLength: 2<br>pattern: ([a-z]{2})-([A-Z]{2})<br>default: en-US | optional |
| page | integer | Specify which page to query.<br>minimum: 1<br>maximum: 1000<br>default: 1 | optional |
| include_adult | boolean | Choose whether to include adult (pornography) content in the results.<br>default: false | optional |
| region | string | Specify a ISO 3166-1 code to filter release dates. Must be uppercase.<br>pattern: ^[A-Z]{2}$ | optional |
| year | integer | year | optional |
| primary_release_year | integer | primary_release_year | optional |

### Result Schema:

| Field | Type | Required? |
|---|:---:|:---:|
| object |||
| page | integer | optional |
| results | array[object] {Movie List Result Object} | optional |
| poster_path | string or null | optional |
| adult | boolean | optional |
| overview | string | optional |
| release_date | string | optional |
| genre_ids | array[integer] | optional |
| id | integer | optional |
| original_title | string | optional |
| original_language | string | optional |
| title | string | optional |
| backdrop_path | string or null | optional |
| popularity | number | optional |
| vote_count | integer | optional |
| video | boolean | optional |
| vote_average | number | optional |
| total_results | integer | optional |
| total_pages | integer | optional |

### Sample result:

Using query 'Avenger'.

The result had a total of 20 entries. It was cut to show only 3 below.

```json
{
    "page": 1,
    "results": [
        {
            "adult": false,
            "backdrop_path": "/aZBZtLCM90QHDCuZFR6oc4NXCWu.jpg",
            "genre_ids": [
                28,
                12,
                878
            ],
            "id": 100402,
            "original_language": "en",
            "original_title": "Captain America: The Winter Soldier",
            "overview": "After the cataclysmic events in New York with The Avengers, Steve Rogers, aka Captain America is living quietly in Washington, D.C. and trying to adjust to the modern world. But when a S.H.I.E.L.D. colleague comes under attack, Steve becomes embroiled in a web of intrigue that threatens to put the world at risk. Joining forces with the Black Widow, Captain America struggles to expose the ever-widening conspiracy while fighting off professional assassins sent to silence him at every turn. When the full scope of the villainous plot is revealed, Captain America and the Black Widow enlist the help of a new ally, the Falcon. However, they soon find themselves up against an unexpected and formidable enemy—the Winter Soldier.",
            "popularity": 88.065,
            "poster_path": "/tVFRpFw3xTedgPGqxW0AOI8Qhh0.jpg",
            "release_date": "2014-03-20",
            "title": "Captain America: The Winter Soldier",
            "video": false,
            "vote_average": 7.7,
            "vote_count": 15635
        },
        {
            "adult": false,
            "backdrop_path": "/lmZFxXgJE3vgrciwuDib0N8CfQo.jpg",
            "genre_ids": [
                12,
                28,
                878
            ],
            "id": 299536,
            "original_language": "en",
            "original_title": "Avengers: Infinity War",
            "overview": "As the Avengers and their allies have continued to protect the world from threats too large for any one hero to handle, a new danger has emerged from the cosmic shadows: Thanos. A despot of intergalactic infamy, his goal is to collect all six Infinity Stones, artifacts of unimaginable power, and use them to inflict his twisted will on all of reality. Everything the Avengers have fought for has led up to this moment - the fate of Earth and existence itself has never been more uncertain.",
            "popularity": 475.593,
            "poster_path": "/7WsyChQLEftFiDOVTGkv3hFpyyt.jpg",
            "release_date": "2018-04-25",
            "title": "Avengers: Infinity War",
            "video": false,
            "vote_average": 8.3,
            "vote_count": 23750
        },
        {
            "adult": false,
            "backdrop_path": "/7RyHsO4yDXtBv1zUU3mTpHeQ0d5.jpg",
            "genre_ids": [
                12,
                878,
                28
            ],
            "id": 299534,
            "original_language": "en",
            "original_title": "Avengers: Endgame",
            "overview": "After the devastating events of Avengers: Infinity War, the universe is in ruins due to the efforts of the Mad Titan, Thanos. With the help of remaining allies, the Avengers must assemble once more in order to undo Thanos' actions and restore order to the universe once and for all, no matter what consequences may be in store.",
            "popularity": 307.291,
            "poster_path": "/or06FN3Dka5tukK1e9sl16pB3iy.jpg",
            "release_date": "2019-04-24",
            "title": "Avengers: Endgame",
            "video": false,
            "vote_average": 8.3,
            "vote_count": 20221
        }
    ],
    "total_pages": 8,
    "total_results": 160
}
```

### To get the genres list:

https://api.themoviedb.org/3/genre/movie/list?api_key=[API_KEY]&language=en-US

#### Genre List Result:

Result obtained at 2020-01-28:

```json
{
    "genres": [
        {
            "id": 28,
            "name": "Action"
        },
        {
            "id": 12,
            "name": "Adventure"
        },
        {
            "id": 16,
            "name": "Animation"
        },
        {
            "id": 35,
            "name": "Comedy"
        },
        {
            "id": 80,
            "name": "Crime"
        },
        {
            "id": 99,
            "name": "Documentary"
        },
        {
            "id": 18,
            "name": "Drama"
        },
        {
            "id": 10751,
            "name": "Family"
        },
        {
            "id": 14,
            "name": "Fantasy"
        },
        {
            "id": 36,
            "name": "History"
        },
        {
            "id": 27,
            "name": "Horror"
        },
        {
            "id": 10402,
            "name": "Music"
        },
        {
            "id": 9648,
            "name": "Mystery"
        },
        {
            "id": 10749,
            "name": "Romance"
        },
        {
            "id": 878,
            "name": "Science Fiction"
        },
        {
            "id": 10770,
            "name": "TV Movie"
        },
        {
            "id": 53,
            "name": "Thriller"
        },
        {
            "id": 10752,
            "name": "War"
        },
        {
            "id": 37,
            "name": "Western"
        }
    ]
}
```
