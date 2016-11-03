# CURL & JSON


## json-server

```bash
json-server -w db.json
json-server --watch db.json
``` 

## curl.exe path
```bash
$ curl -X GET http://localhost:3000/movies
# or
$ curl -X GET "http://localhost:3000/movies"
``` 

```json
{
  "movies": [
    {
      "id": 1,
      "name": "The Godfather",
      "director": "Francis Ford Coppola",
      "rating": 9.1
    },
    {
      "id": 2,
      "name": "Casablanca",
      "director": "Michael Curtiz",
      "rating": 8.8
    },
    {
      "id": 3,
      "name": "Inception",
      "director": "Christopher Nolan",
      "rating": 9
    }
  ]
``` 

