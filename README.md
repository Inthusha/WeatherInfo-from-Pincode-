# WeatherInfo-from-Pincode

# Backend Assignment - Weather Info for Pincode

## Project Overview
This project contains one main REST API module:

1. **Weather Info API**  
   - Provides weather information for a given **Pincode** and **date**.  
   - Optimized to reduce API calls using caching in the database.

## Technology Stack
- Java 21 
- Spring Boot 3.x  
- Spring Data JPA  
- MySQL  
- WebClient for external API calls  
- JUnit 5 & Mockito for testing  
- Maven  

## Running the Application

1. Configure Database
MySQL: update application.properties:

application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/weatherdb?useSSL=false
spring.datasource.username=root
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

2. Add OpenWeather API Key in application.properties
openweather.api.key=YOUR_API_KEY

3. Build & Run
mvn clean install
mvn spring-boot:run

The application will run on http://localhost:8080

Weather Info API
Endpoint
POST  /api/weather

Request Body
json

{
  "pincode": "411014",
  "forDate": "2025-08-28"
}

Response
json

{
  "pincode": "411014",
  "date": "2025-08-28",
  "latitude": 18.53,
  "longitude": 73.85,
  "temperature": 30.5,
  "humidity": 70,
  "description": "clear sky",
  "windSpeed": 5.3
}

Error Responses
Status	     Error                Reason	
400	    Invalid Pincode / Date	 "Pincode must be a 6-digit number"/"Date is required(today only allowed)"
400	    Extra / malformed JSON	 "Malformed JSON request"
503   	API down	               "Weather API is unreachable"


