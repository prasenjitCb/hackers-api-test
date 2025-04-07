# Hackers API

A Go-based REST API that mirrors Hacker News content, providing endpoints for top stories, Show HN, and Ask HN posts. Built with Gin and featuring Swagger documentation.

## Features

- 🚀 Fast and efficient API responses
- 💾 In-memory caching to reduce HN API calls
- 📚 Swagger/OpenAPI documentation
- 🔄 CORS enabled for frontend integration
- 🐳 Docker support
- 📱 Endpoints for different story types (top/show/ask)
- 🧪 Comprehensive test suite

## Prerequisites

- Go 1.23 or higher
- Docker (optional)

## Quick Start

### Running Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/cloudbees-days/hackers-api.git
   cd hackers-api
   ```

2. Install dependencies:
   ```bash
   go mod download
   ```

3. Generate Swagger documentation:
   ```bash
   go install github.com/swaggo/swag/cmd/swag@latest
   swag init
   ```

4. Run the application:
   ```bash
   go run main.go
   ```

The API will be available at `http://localhost:8080`

### Using Docker

1. Build the image:
   ```bash
   docker build -t hackers-api .
   ```

2. Run the container:
   ```bash
   docker run -p 8080:8080 hackers-api
   ```

## API Documentation

Once the application is running, you can access the Swagger documentation at:
```
http://localhost:8080/swagger/index.html
```

### Available Endpoints

- `GET /api/stories` - Get top stories (default)
- `GET /api/stories/top` - Get top stories
- `GET /api/stories/show` - Get Show HN stories
- `GET /api/stories/ask` - Get Ask HN stories

### Response Format

```json
{
  "id": 123456,
  "title": "Show HN: My Cool Project",
  "url": "https://github.com/cool/project",
  "points": 100,
  "submitted_by": "johndoe",
  "created_at": "2024-01-28T12:00:00Z",
  "comments_url": "https://news.ycombinator.com/item?id=123456",
  "comments": 42,
  "type": "show"
}
```

## Caching

The API implements an in-memory cache with the following characteristics:
- Cache duration: 5 minutes
- Maximum stories per type: 30
- Thread-safe implementation

## Development

### Project Structure

```
.
├── main.go           # Main application file
├── main_test.go      # Test file
├── Dockerfile        # Docker configuration
├── go.mod           # Go module file
├── go.sum           # Go module checksum
└── docs/            # Generated Swagger documentation
```

### Testing

The project includes comprehensive tests covering:
- API endpoints functionality
- Caching mechanism
- Error handling
- CORS headers

To run the tests:

```bash
# Run all tests
go test -v ./...

# Run tests with coverage
go test -race -coverprofile=coverage.txt -covermode=atomic ./...

# View coverage in browser
go tool cover -html=coverage.txt
```

### Adding New Features

1. Update the code in `main.go`
2. Regenerate Swagger docs: `swag init`
3. Add tests for new functionality
4. Run tests to ensure everything passes
5. Build and run

## Acknowledgments

- [Hacker News API](https://github.com/HackerNews/API)
- [Gin Web Framework](https://github.com/gin-gonic/gin)
- [Swagger/Swag](https://github.com/swaggo/swag)
