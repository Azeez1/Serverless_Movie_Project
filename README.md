Here's the content you can use for your **README.md** file or project summary documentation on GitHub:

---

# **Serverless Movies API**

## **Project Overview**
The **Serverless Movies API** is a fully serverless application built using AWS services. This API provides endpoints for retrieving movie information from a NoSQL database (DynamoDB) and serves movie cover images stored in S3. The application is scalable, cost-efficient, and requires no server management, leveraging AWS Lambda and API Gateway for API functionality.

## **Architecture**
The project follows a serverless architecture using the following AWS services:
- **AWS Lambda**: For executing the backend logic to query the movie database.
- **API Gateway**: For exposing RESTful API endpoints.
- **DynamoDB**: A NoSQL database for storing movie details.
- **S3**: For storing and serving movie cover images.

## **Endpoints**
### 1. **GET /getmovies**
Retrieves all the movies stored in the DynamoDB database.

#### **Sample Request**
```bash
GET https://your-api-id.execute-api.region.amazonaws.com/prod/getmovies
```

#### **Sample Response**
```json
[
    {
        "title": "Inception",
        "releaseYear": 2010,
        "genre": "Science Fiction, Action",
        "coverUrl": "https://movie-cover-images-azeez.s3.us-east-1.amazonaws.com/inception.jpg"
    },
    {
        "title": "American Gangster",
        "releaseYear": 2007,
        "genre": "Crime, Drama",
        "coverUrl": "https://movie-cover-images-azeez.s3.us-east-1.amazonaws.com/american_gangster.jpg"
    }
]
```

### 2. **GET /getmoviesbyyear/{year}**
Retrieves movies released in a specified year.

#### **Sample Request**
```bash
GET https://your-api-id.execute-api.region.amazonaws.com/prod/getmoviesbyyear/2010
```

#### **Sample Response**
```json
[
    {
        "title": "Inception",
        "releaseYear": 2010,
        "genre": "Science Fiction, Action",
        "coverUrl": "https://movie-cover-images-azeez.s3.us-east-1.amazonaws.com/inception.jpg"
    }
]
```

#### **Error Handling**
If an invalid year is provided (e.g., non-numeric input) or no movies are found for the given year, the API returns a relevant error message.

**Sample Error Response for Invalid Input:**
```json
{
    "error": "Invalid year format. Please provide a valid integer year."
}
```

**Sample Error Response for No Movies Found:**
```json
{
    "error": "No movies found for the given year."
}
```

## **Project Features**
1. **Serverless Architecture**: The API uses AWS Lambda and API Gateway, ensuring a scalable and cost-effective solution.
2. **DynamoDB Integration**: A NoSQL database is used to store movie information, making it easy to query and retrieve data.
3. **S3 for Movie Covers**: Movie cover images are stored in AWS S3, with public URLs served in the API responses.
4. **API Endpoints**: Two endpoints provide functionality for retrieving all movies and filtering movies by release year.
5. **Error Handling**: The API provides error responses for invalid input or no data found.

## **Setup Instructions**

### Prerequisites
- An AWS account with access to Lambda, API Gateway, S3, and DynamoDB.
- AWS CLI or SDK for managing your AWS resources.
- Git for version control.

### Steps
1. **Clone the Repository**
   ```bash
   git clone https://github.com/Azeez1/Serverless_Movie_Project.git
   cd Serverless_Movie_Project
   ```

2. **Deploy Lambda Functions**
   - Use the AWS CLI or the AWS Console to deploy the provided Lambda functions (`GetMovies` and `GetMoviesByYear`).
   - Ensure the Lambda functions are connected to your API Gateway and can query your DynamoDB table.

3. **Configure DynamoDB**
   - Set up a DynamoDB table named `Movies` with the following attributes:
     - `title` (String)
     - `releaseYear` (Number)
     - `genre` (String)
     - `coverUrl` (String)

4. **Upload Movie Covers to S3**
   - Create an S3 bucket to store movie cover images.
   - Make sure the images are publicly accessible via URL or generate pre-signed URLs in Lambda.

5. **API Gateway**
   - Set up the API Gateway with two endpoints: `/getmovies` and `/getmoviesbyyear/{year}`.
   - Ensure they are linked to the appropriate Lambda functions.

## **Future Enhancements**
1. **AI-Generated Movie Summaries**: Use AWS services like Comprehend or external APIs (like OpenAI GPT) to generate summaries of movies.
2. **Pagination**: Implement pagination to handle large datasets when retrieving all movies.
3. **Authentication**: Add API key-based or token-based authentication to secure the API.

---

Feel free to modify this content to suit your needs and add any specific details about your project. Let me know if you need any further edits or additions!
