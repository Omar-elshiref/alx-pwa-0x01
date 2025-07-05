# Project Description
CineSeek is a modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS. The application allows users to browse movies from the MoviesDatabase API, view movie details, and search for films by year or genre. The project focuses on creating a responsive, well-structured web application with proper API integration and TypeScript typing.

## Learning Objectives

- Understand API documentation and integration.
- Implement TypeScript interfaces for API responses.
- Create reusable React components.
- Build a responsive layout with Tailwind CSS.
- Manage application state for filtering and pagination.
- Implement proper error handling and loading states.
- Set up Next.js API routes for server-side data fetching.
- Manage environment variables for API keys.

## Requirements

### Technical Stack

- Next.js 14 (Pages Router)
- TypeScript
- Tailwind CSS
- Font Awesome icons
- MoviesDatabase API

### Development Requirements

- Node.js (v16 or higher)
- npm or yarn
- Git for version control

File Structure
`alx-movie-app/
├── components/
│   ├── commons/
│   │   ├── Button.tsx
│   │   ├── Loading.tsx
│   │   └── MovieCard.tsx
│   └── layouts/
│       ├── Footer.tsx
│       ├── Header.tsx
│       └── Layout.tsx
├── interfaces/
│   └── index.ts
├── pages/
│   ├── api/
│   │   └── fetch-movies.ts
│   ├── movies/
│   │   └── index.tsx
│   ├── _app.tsx
│   └── index.tsx
├── public/
├── styles/
│   └── globals.css
├── .env.local
├── .eslintrc.json
├── .gitignore
├── next.config.js
├── package.json
└── tsconfig.json`

## Best Practices

### Code Quality
- Use TypeScript interfaces for all component props and API responses.
- Follow a component-based architecture with clear separation of concerns.
- Implement proper error handling in all API requests.
- Display loading states to enhance user experience.
- Store sensitive data, such as API keys, in environment variables.

### Performance
- Utilize client-side navigation with the Next.js router.
- Optimize API calls with efficient pagination.
- Ensure responsive design using Tailwind CSS.
- Optimize images with the Next.js `Image` component.

### Maintainability
- Apply consistent code formatting throughout the project.
- Maintain a clear and organized folder structure.
- Build reusable components with comprehensive prop typing.
- Provide proper documentation in the README.

### API Integration
- Integrate with the MoviesDatabase API using key endpoints:
    - `/titles`: Main endpoint for fetching movie data.
        - Supports filtering by year and genre.
        - Implements pagination for browsing results.

### Authentication
- Use API key authentication via request headers.
- Store API keys in environment variables.
- Route API requests through a server-side API to prevent exposing keys on the client.

### Error Handling
- Show a loading component during pending states.
- Use try/catch blocks in API routes.
- Check status codes in API responses.
- Apply type guards to validate API data.

### Usage Limits
- Consider API rate limiting.
- Use pagination to limit request size.
- Implement client-side caching of responses where appropriate.
- Use error boundaries for graceful error handling.

## API overview
The MoviesDatabase API provides access to a large collection of movie and TV show data. Key features include:

- **Search and Discovery:** Search for movies, TV shows, and people by title, keyword, or ID.
- **Filtering:** Filter results by year, genre, language, and type (movie or series).
- **Detailed Information:** Retrieve comprehensive details for titles, including cast, crew, plot, ratings, images, and trailers.
- **Trending and Popular Lists:** Access trending, popular, and top-rated movies or shows.
- **Pagination:** Supports paginated responses for large result sets.
- **Person Data:** Look up actor and crew profiles, including filmography.
- **API Key Authentication:** Secure access via API key in request headers.

These features enable robust movie discovery, detailed browsing, and integration of rich media content into applications.

## Version

Current API version: v1

## Available Endpoints

- **`/titles`**: Fetches a list of movies or TV shows. Supports filtering by year, genre, and pagination.
- **`/titles/{id}`**: Retrieves detailed information for a specific movie or TV show by its unique ID.
- **`/titles/search/title/{title}`**: Searches for movies or TV shows by title.
- **`/titles/utils/genres`**: Returns a list of available genres for filtering.
- **`/titles/utils/languages`**: Returns a list of supported languages.
- **`/actors/{id}`**: Fetches details about a specific actor or crew member.
- **`/actors/{id}/titles`**: Lists movies or shows associated with a specific actor.

## Request and Response Format

### Example Request

```http
GET https://moviesdatabase.p.rapidapi.com/titles?year=2023&genre=Action&page=1
Headers:
    X-RapidAPI-Key: YOUR_API_KEY
    X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

### Example Response

```json
{
    "results": [
        {
            "id": "tt1234567",
            "titleText": { "text": "Example Movie" },
            "releaseYear": { "year": 2023 },
            "genres": { "genres": [{ "text": "Action" }] },
            "primaryImage": { "url": "https://..." }
        }
    ],
    "page": 1,
    "next": "/titles?year=2023&genre=Action&page=2"
}
```

- **Request**: Use query parameters for filtering (e.g., `year`, `genre`, `page`).
- **Response**: Returns a paginated list of results, each with movie details.

## Authentication

All requests require authentication via an API key:

- Include the `X-RapidAPI-Key` header with your API key.
- Set the `X-RapidAPI-Host` header to `moviesdatabase.p.rapidapi.com`.

**Example:**

```http
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

Store your API key in environment variables and never expose it on the client side.

## Error Handling

- **400 Bad Request**: Invalid parameters or malformed request. Check your query parameters.
- **401 Unauthorized**: Missing or invalid API key. Ensure your key is correct and included in headers.
- **403 Forbidden**: You do not have access to the requested resource.
- **404 Not Found**: The requested resource does not exist.
- **429 Too Many Requests**: Rate limit exceeded. Wait before retrying.
- **500 Internal Server Error**: Server-side issue. Retry later.

**Handling in Code:**

- Use `try/catch` blocks for API calls.
- Check response status codes and display user-friendly error messages.
- Implement loading and error states in your UI.

## Usage Limits and Best Practices

- **Rate Limits**: The API enforces rate limits (see your RapidAPI dashboard for specifics). Exceeding limits returns a 429 error.
- **Pagination**: Use pagination to avoid large requests and stay within usage limits.
- **Caching**: Cache frequent responses client-side to reduce API calls.
- **Environment Variables**: Store API keys securely in environment variables.
- **Error Boundaries**: Use error boundaries in your React app for graceful error handling.
- **Efficient Filtering**: Apply filters (year, genre) to minimize unnecessary data transfer.

Refer to the [MoviesDatabase API documentation](https://rapidapi.com/SAdrian/api/moviesdatabase) for more details.