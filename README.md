# 🎬 MoviesDatabase API

## API Overview  
The **MoviesDatabase API** provides complete and updated information about movies, TV shows, series, episodes, and actors. With over **9 million titles** and **11 million actors/crew members**, the API is a powerful tool for developers who want to integrate movie data into their applications.  

It includes details such as:  
- Title information (movies, series, episodes)  
- Actor and crew details  
- Ratings, reviews, and box office numbers  
- Awards, trivia, and external links  
- YouTube trailers, images, and videos  
- Upcoming releases and trending lists (e.g., top-rated movies, box office hits)  


## Version  
**Current API Version:** v1  


## Available Endpoints  

### 🎥 Titles  
- **`/titles`** – Returns an array of titles with optional filters (genre, year, type, etc.).  
- **`/titles/{id}`** – Returns details for a single title by IMDb ID.  
- **`/titles/{id}/ratings`** – Returns ratings and number of votes for a title.  
- **`/titles/series/{id}`** – Returns episodes (light info) of a series.  
- **`/titles/seasons/{id}`** – Returns the number of seasons for a series.  
- **`/titles/series/{id}/{season}`** – Returns episodes of a specific season.  
- **`/titles/episode/{id}`** – Returns details about a specific episode.  
- **`/titles/x/upcoming`** – Returns a list of upcoming titles.  

### 🔍 Search  
- **`/titles/search/keyword/{keyword}`** – Search titles by keyword.  
- **`/titles/search/title/{title}`** – Search titles by title (exact or partial).  
- **`/titles/search/akas/{aka}`** – Search titles by alternate titles (exact match).  

### 👤 Actors  
- **`/actors`** – Returns an array of actors (with pagination support).  
- **`/actors/{id}`** – Returns details for a specific actor by IMDb ID.  

### 🛠 Utilities  
- **`/title/utils/titleType`** – Returns available title types.  
- **`/title/utils/genres`** – Returns available genres.  
- **`/title/utils/lists`** – Returns available predefined lists (e.g., top-rated, most popular).  

---

## Request and Response Format  

### Example Request  
http
GET /titles/search/title/Inception?info=base_info&limit=1


### Example Response (Simplified)

```json
{
  "results": [
    {
      "id": "tt1375666",
      "titleText": { "text": "Inception" },
      "primaryImage": { "url": "https://image.url" },
      "titleType": { "id": "movie" },
      "releaseDate": { "year": 2010 },
      "genres": { "genres": [{ "text": "Action" }, { "text": "Sci-Fi" }] },
      "ratingsSummary": { "aggregateRating": 8.8, "voteCount": 2000000 },
      "plot": { "plotText": { "plainText": "A thief who steals corporate secrets..." } }
    }
  ]
}
```


### Notes

All query parameters are optional.
Many responses return a results object.
Paged responses include page, next, and entries.


## Authentication

The API documentation does not specify authentication.

⚠️ If hosted on RapidAPI or another API provider, you will typically need an API key passed in request headers, such as:

X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com


## Error Handling

The API may return standard HTTP error codes:

400 Bad Request – Invalid parameters (e.g., wrong IMDb ID format).

404 Not Found – No data found for the request.

429 Too Many Requests – Rate limit exceeded (if applicable).

500 Internal Server Error – Unexpected issue on the API server.


Best practice: Always check the response for an error message and handle gracefully in your code.


## Usage Limits and Best Practices

Maximum 50 items per request (limit query parameter).

Use pagination (page parameter) to fetch large datasets.

Use info parameter to request only the data you need (mini_info, base_info, image, etc.) for faster and lighter responses.

Prefer predefined lists (most_pop_movies, top_rated_250, etc.) for trending/curated collections instead of querying the full database.

If rate limits exist (e.g., on RapidAPI), implement retry logic and caching to avoid hitting API limits unnecessarily.



