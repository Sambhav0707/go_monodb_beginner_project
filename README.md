# Go MongoDB Beginner Project

A simple REST API built with Go and MongoDB for managing users. This project demonstrates basic CRUD operations using the MongoDB Go driver.

## Features

- ✅ Create users
- ✅ Get user by ID
- ✅ Delete users
- 🔄 Update users (planned)
- 🔄 List all users (planned)

## Tech Stack

- **Backend**: Go (Golang)
- **Database**: MongoDB
- **HTTP Router**: julienschmidt/httprouter
- **Environment Management**: godotenv
- **MongoDB Driver**: go.mongodb.org/mongo-driver

## Prerequisites

Before running this project, make sure you have:

- [Go](https://golang.org/dl/) (version 1.19 or higher)
- [MongoDB](https://www.mongodb.com/try/download/community) (running locally or MongoDB Atlas)

## Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd go_mongoDB_beginner_project
   ```

2. **Install dependencies**
   ```bash
   go mod tidy
   ```

3. **Set up environment variables**
   ```bash
   # Copy the example environment file
   cp .env.example .env
   
   # Edit .env file with your MongoDB connection string
   MONGODB_URI=mongodb://127.0.0.1:27017
   ```

4. **Start MongoDB**
   
   **Option A: Local MongoDB**
   ```bash
   # Windows (if installed as service)
   net start MongoDB
   
   # Linux/Mac
   sudo systemctl start mongod
   ```
   
   **Option B: Docker**
   ```bash
   docker run -d --name mongodb -p 27017:27017 mongo:latest
   ```
   
   **Option C: MongoDB Atlas (Cloud)**
   - Sign up at [MongoDB Atlas](https://www.mongodb.com/atlas)
   - Create a free cluster
   - Get your connection string and update `.env` file

5. **Run the application**
   ```bash
   go run main.go
   ```

The server will start on `http://localhost:3000`

## API Endpoints

### Create User
```http
POST /user
Content-Type: application/json

{
  "name": "John Doe",
  "gender": "male",
  "age": 30
}
```

**Response:**
```json
{
  "id": "507f1f77bcf86cd799439011",
  "name": "John Doe",
  "gender": "male",
  "age": 30
}
```

### Get User
```http
GET /user/{id}
```

**Response:**
```json
{
  "id": "507f1f77bcf86cd799439011",
  "name": "John Doe",
  "gender": "male",
  "age": 30
}
```

### Delete User
```http
DELETE /user/{id}
```

**Response:**
```
Deleted user 507f1f77bcf86cd799439011
```

## Project Structure

```
go_mongoDB_beginner_project/
├── controllers/
│   └── user.go          # HTTP handlers for user operations
├── models/
│   └── user.go          # User data model
├── main.go              # Application entry point
├── go.mod               # Go module file
├── go.sum               # Go module checksums
├── .env                 # Environment variables (not in git)
├── .gitignore           # Git ignore rules
├── README.md            # This file
└── LICENSE              # Project license
```

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb://127.0.0.1:27017` |
| `SERVER_PORT` | Server port | `3000` |
| `SERVER_HOST` | Server host | `localhost` |

## Database Schema

### User Collection
```json
{
  "_id": "ObjectId",
  "name": "string",
  "gender": "string",
  "age": "number"
}
```

## Development

### Running Tests
```bash
go test ./...
```

### Building
```bash
go build -o app main.go
```

### Running with Docker
```bash
# Build the image
docker build -t go-mongodb-app .

# Run the container
docker run -p 3000:3000 go-mongodb-app
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Troubleshooting

### "no reachable servers" Error
This error occurs when MongoDB is not running. Make sure to:
1. Install MongoDB Community Server
2. Start the MongoDB service
3. Check if the connection string in `.env` is correct

### Connection Refused
- Verify MongoDB is running on the correct port (27017)
- Check firewall settings
- Ensure the connection string is correct

### Import Errors
Run `go mod tidy` to download and organize dependencies.

## Support

If you encounter any issues, please:
1. Check the troubleshooting section above
2. Search existing issues
3. Create a new issue with detailed information

---

**Happy Coding! 🚀**
